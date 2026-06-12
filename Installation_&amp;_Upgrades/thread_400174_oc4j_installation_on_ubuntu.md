---
title: "oc4j installation on ubuntu"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by rhd_rahar on 2007-04-03
Hello all,

I have problem installing oc4j standalone server on ubuntu 6.10.
I am using java 1.4.2 and oc4j 101320. Can you help me how to install oc4j.

fyi

# java -jar oc4j.jar -install
WARNING: Cannot cleanup application URLStreamHandlers.
OC4J startup failed
oracle.classloader.util.AnnotatedClassFormatError: oracle.j2ee.ws.client.BasicService (erroneous identifier)

          Invalid class: oracle.j2ee.ws.client.BasicService
                 Loader: oracle.ws.client:10.1.3
            Code-Source: /JAVA/webservices/lib/wsclient.jar
          Configuration: <code-source> (ignore manifest Class-Path) in META-INF/boot.xml in /JAVA/j2ee/home/oc4j.jar

        Dependent class: oracle.classloader.util.XMLConfiguration
                 Loader: gnu.gcj.runtime.SystemClassLoader@372616
            Code-Source: /JAVA/j2ee/home/lib/pcl.jar
          Configuration: /JAVA/j2ee/home/lib/pcl.jar

        at oracle.classloader.PolicyClassLoader.bulkLoadClasses (PolicyClassLoader.java:1538) [/JAVA/j2ee/home/lib/pcl.jar, by gnu.gcj.runtime.SystemClassLoader@372616]
        at oracle.classloader.util.XMLConfiguration.bulkLoadClasses (XMLConfiguration.java:885) [/JAVA/j2ee/home/lib/pcl.jar, by gnu.gcj.runtime.SystemClassLoader@372616]
        at oracle.classloader.util.XMLConfiguration.access$100 (XMLConfiguration.java:41) [/JAVA/j2ee/home/lib/pcl.jar, by gnu.gcj.runtime.SystemClassLoader@372616]
        at oracle.classloader.util.XMLConfiguration$Externals.load (XMLConfiguration.java:871) [/JAVA/j2ee/home/lib/pcl.jar, by gnu.gcj.runtime.SystemClassLoader@372616]
        at oracle.classloader.util.XMLConfiguration.endElement (XMLConfiguration.java:685) [/JAVA/j2ee/home/lib/pcl.jar, by gnu.gcj.runtime.SystemClassLoader@372616]
        at gnu.xml.stream.SAXParser.parse (libgcj.so.70) [jre bootstrap, by jre.bootstrap:1.4.2]
        at oracle.classloader.util.XMLConfiguration.configureLoaders (XMLConfiguration.java:277) [/JAVA/j2ee/home/lib/pcl.jar, by gnu.gcj.runtime.SystemClassLoader@372616]
        at oracle.classloader.util.InitialLoadersFactory.populateLoaders (InitialLoadersFactory.java:389) [/JAVA/j2ee/home/lib/pcl.jar, by gnu.gcj.runtime.SystemClassLoader@372616]
        at oracle.classloader.util.InitialLoadersFactory.initLoaders (InitialLoadersFactory.java:230) [/JAVA/j2ee/home/lib/pcl.jar, by gnu.gcj.runtime.SystemClassLoader@372616]
        at oracle.classloader.util.InitialLoadersFactory.create (InitialLoadersFactory.java:167) [/JAVA/j2ee/home/lib/pcl.jar, by gnu.gcj.runtime.SystemClassLoader@372616]
        at oracle.oc4j.loader.boot.BootStrap.main (BootStrap.java:26) [/JAVA/j2ee/home/oc4j.jar, by gnu.gcj.runtime.SystemClassLoader@372616]
        at oracle.oc4j.loader.boot.BootStrap (method and line unknown).
        at gnu.java.lang.MainThread (method and line unknown).
        at gnu.java.lang.MainThread (method and line unknown).

thanks.

---

### Post by jjjjjj on 2008-06-03
First of (not surprised) OC4J is not certified like many other applications on ubuntu; see [http://www.oracle.com/technology/software/products/ias/files/oracle_soa_certification_101310.html](http://www.oracle.com/technology/software/products/ias/files/oracle_soa_certification_101310.html)

---

