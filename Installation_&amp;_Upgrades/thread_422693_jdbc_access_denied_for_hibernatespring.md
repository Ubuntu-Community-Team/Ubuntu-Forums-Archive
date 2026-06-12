---
title: "jdbc access denied for hibernate/spring"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by obamasi on 2007-04-25
Hello,

I am receiving the "jdbc access denied" error for a hibernate/spring application I ported from XP to Ubuntu. 
 Here is my configuration:
  Ubuntu 7.0.4 desktop
 MySQL 5 (came with OS install)
 MySQL Java connector
 Java 5
 Spring 1.2
 Hibernate 3.1
 JSF 1.1

I read all of the threads posted on this issue and made the appropriate changes to: /etc/hosts, MySQL user (saruser), and I even created a simple JUnit testcase that connects to the database. The JUint class connects fine with no problem(it is straigth JDBC connection class found all over the internet) but when I deploy my app or even run it within Eclipse (3.2) I get the access denied. Since I can access via plain jdbc I think that the problem lies in spring/ubuntu compatibility???

 Below is a snippet of the Spring config file stanza used to access MySQL (again, this works in Windows), I have tried with and without a password:

<bean id="dataSource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">	
		<property name="driverClassName"><value>com.mysql.jdbc.Driver</value></property>
		<property name="url"><value>jdbc:mysql://localhost:3306/sugarandrice</value></property>
		<property name="username"><value>saruser</value></property>
		<property name="password"><value></value></property>
	</bean>

Any help is appreciated.

Thanks!

---

