---
title: "Tomcat9 shipped with 22.04 LTS distro malfunction with java 8"
date: 2022-05-24
forum: Installation &amp; Upgrades
---

### Post by loyep on 2022-05-24
Hi everybody,

on a fresh Virtulbox install of 22.04 LTS server version I installed through apt:


[LIST=1]
[*]java 8 jdk/jre
[*]tomcat 9
[/LIST]


After that I copied in the tomcat9 webapps folder one of the webapps working under Java 8 in my 20.04 Virtualbox install.

Problem is that the distro Tomcat9 gives me :

*******************

**HTTP Status 500 – Internal Server Error**

[HR][/HR][COLOR=#E8E6E3][FONT=Tahoma]**Type** Exception Report[/FONT][/COLOR][COLOR=#E8E6E3][FONT=Tahoma]**Message** java.lang.UnsupportedClassVersionError: org/eclipse/jdt/internal/compiler/env/INameEnvironment has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0

[/FONT][/COLOR][COLOR=#E8E6E3][FONT=Tahoma]**Description** The server encountered an unexpected condition that prevented it from fulfilling the request.[/FONT][/COLOR][COLOR=#E8E6E3][FONT=Tahoma]**Exception**[/FONT][/COLOR]javax.servlet.ServletException: java.lang.UnsupportedClassVersionError: org/eclipse/jdt/internal/compiler/env/INameEnvironment has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0
    org.apache.jasper.servlet.JspServlet.service(JspSe  rvlet.java:332)
    javax.servlet.http.HttpServlet.service(HttpServlet  .java:764)
    org.apache.tomcat.websocket.server.WsFilter.doFilt  er(WsFilter.java:53)
[COLOR=#E8E6E3][FONT=Tahoma][B]

Root Cause[/B][/FONT][/COLOR]java.lang.UnsupportedClassVersionError: org/eclipse/jdt/internal/compiler/env/INameEnvironment has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0
    java.lang.ClassLoader.defineClass1(Native Method)
    java.lang.ClassLoader.defineClass(ClassLoader.java  :756)
    java.security.SecureClassLoader.defineClass(Secure  ClassLoader.java:142)
    java.net.URLClassLoader.defineClass(URLClassLoader  .java:473)
    java.net.URLClassLoader.access$100(URLClassLoader.  java:74)
    java.net.URLClassLoader$1.run(URLClassLoader.java:  369)
    java.net.URLClassLoader$1.run(URLClassLoader.java:  363)
    java.security.AccessController.doPrivileged(Native Method)
    java.net.URLClassLoader.findClass(URLClassLoader.j  ava:362)
    java.lang.ClassLoader.loadClass(ClassLoader.java:4  18)
    java.lang.ClassLoader.loadClass(ClassLoader.java:3  51)
    java.lang.Class.forName0(Native Method)
    java.lang.Class.forName(Class.java:264)
    org.apache.jasper.JspCompilationContext.createComp  iler(JspCompilationContext.java:247)
    org.apache.jasper.JspCompilationContext.createComp  iler(JspCompilationContext.java:225)
    org.apache.jasper.JspCompilationContext.compile(Js  pCompilationContext.java:597)
    org.apache.jasper.servlet.JspServletWrapper.servic  e(JspServletWrapper.java:399)
    org.apache.jasper.servlet.JspServlet.serviceJspFil  e(JspServlet.java:379)
    org.apache.jasper.servlet.JspServlet.service(JspSe  rvlet.java:327)
    javax.servlet.http.HttpServlet.service(HttpServlet  .java:764)
    org.apache.tomcat.websocket.server.WsFilter.doFilt  er(WsFilter.java:53)
[COLOR=#E8E6E3][FONT=Tahoma]**Note** The full stack trace of the root cause is available in the server logs.
[/FONT][/COLOR]

*******************

like the app was compiled with Java 11 (which isn't).

[U][B]The important thing is that if I manually install Tomcat on the 22.04 VM the app works flawlessly.

[/B][/U]Has somebody else incurred in this strange behaviour?

Is there a bug in the Apt Tomcat9 install, since the manual install from the .tar.gz file works well?

If more data is required please simply ask.

Thanks in advance

---

### Post by bigstallionweb on 2022-11-01
After a 2 hours battle, I resolved the issue by:
[LIST]
[*]Downloading "org.eclipse.jdt.core-3.18.0.jar" file from [https://repo1.maven.org/maven2/org/eclipse/jdt/org.eclipse.jdt.core/3.18.0/](https://repo1.maven.org/maven2/org/eclipse/jdt/org.eclipse.jdt.core/3.18.0/) (picked this file because it was compiled using JAVA 8) 
[*]Copying the downloaded file to the "/usr/share/java" folder 
[*]Removing the "/usr/share/java/eclipse-jdt-core.jar" symlink 
[*]Creating a new symlink -> ln -s /usr/share/java/org.eclipse.jdt.core-3.18.0.jar /usr/share/java/eclipse-jdt-core.jar 
[/LIST]

---

