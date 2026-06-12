---
title: "JSP to Oracle with type 4 driver... problem."
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by obedraju on 2011-10-16
Hello...

Am using 'eclipse indigo' for web applications on ubuntu. 
In jsp page I've written the following code.
-----------------------------------------------------------------
<%@page import="java.sql.*;"%>
<%
try
{
Class.forName("oracle.jdbc.driver.OracleDriver");
Connection con=DriverManager.getConnection("jdbc:oracle:thin: @localhost:1521:xe","system","obedraju");
PreparedStatement ps = con.prepareStatement("create table emp(Id varchar2(29)");

System.out.println("Loading driver");
}
catch(Exception s)
{}

%>
hello
-----------------------------------------------------------------

I'm getting output on page as 'hello' but table is not created on database.

I've added ojdbc14.jar on eclipse.

folder>build path>configure build path>libraries>add external jar>ojdbc14.jar 'ok'.

Restarted.

Can some one help me plz..!!!

---

