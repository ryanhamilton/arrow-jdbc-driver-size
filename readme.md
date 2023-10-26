# Arrow SQL driver bloatware

Sample app that shows size of resulting "hello world" jar when using org.apache.arrow:flight-sql-jdbc-driver.

Output seems to be 69MB jar file.


My comment from linkedin:
"I'm a massive fan of arrow and of the influxdb rewrite but I would like to push back on your JDBC comments.

"if you don’t understand why implementing a JDBC or ODBC driver is so complex and nuanced it often takes a whole team of developers, consider yourself lucky" 
I personally have implemented 2 JDBC drivers and it's not that hard. 

The default recommended arrow JDBC driver implementation is terrible and I can see how implementing that would make someone say that it's hard. No attempt has been made at crafting something beautiful. If you add flight-sql-jdbc-driver as a dependency to a java appllication it pulls in 70MB of dependencies including 8 platform specific versions of netty and 1000s of files. H2 database which includes a JDBC driver and a database engine is 2.5MB. If you want smaller, here is JDBC implemented as a single file (https://github.com/KxSystems/kdb/blob/master/c/jdbc.java), this is used by 100s of users globally. 

I admire the idea of a common data format but tying it to a 70MB verbose implementation when someone just wants a java driver isn't convincing me."