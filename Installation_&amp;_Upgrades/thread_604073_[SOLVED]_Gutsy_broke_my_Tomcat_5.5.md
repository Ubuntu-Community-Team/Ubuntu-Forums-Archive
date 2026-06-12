---
title: "[SOLVED] Gutsy broke my Tomcat 5.5"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by Josh_P on 2007-11-05
So after my upgrade to Gutsy my Tomcat 5.5 stopped working.
Main problem I'm getting is 

java.lang.IllegalStateException: No Java compiler available
	org.apache.jasper.JspCompilationContext.createCompiler(JspCompilationContext.java:225)
	org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:560)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:302)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:329)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:265)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)

After looking at my $TOMCAT_HOME/common/lib/ , I noticed that a bunch of my lib jar files were updated to links after upgrading to Gutsy.

jasper-compiler-jdt.jar -> ../../../java/ecj.jar

Problem is, that ecj.jar file doesn't exist. Any suggestions?

---

### Post by Josh_P on 2007-11-05
well solution for me was to overwrite the lib directory from my downloaded tomcat. lesson learned, backup all web server stuff before an upgrade

---

