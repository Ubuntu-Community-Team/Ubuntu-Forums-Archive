---
title: "Resin JAVA"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Peque on 2007-02-05
HEy Forum.

I want to use the Resin 3.0.21 webserver in our enviorment for testing., 
I have an Installation of Dapper server with the different packages sun-java5-jre & sun-java5-jdk and had the different packages and needs: 

But each time I want to start the server it comes with this error: 
# /etc/resin-3.0.21/bin/httpd.sh 
WARNING: System property "java.util.logging.manager" should be the name of a subclass of java.util.logging.LogManager
Resin-3.0.21 (built Thu, 10 Aug 2006 12:03:19 PDT)
Copyright(c) 1998-2006 Caucho Technology.  All rights reserved.

  Using Resin(R) Open Source under the GNU Public License (GPL).

  See [http://www.caucho.com](http://www.caucho.com) for information on Resin Professional,
  including caching, clustering, JNI acceleration, and OpenSSL integration.

Starting Resin on Mon, 05 Feb 2007 19:50:46 +0100 (GMT+01:00)

java.lang.NoClassDefFoundError: com.caucho.jmx.IntrospectionMBean
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.caucho.jmx.EnvironmentMBeanServer.<init>(EnvironmentMBeanServer.java)
   at com.caucho.jmx.EnvironmentMBeanServerBuilder.getGlobal(EnvironmentMBeanServerBuilder.java:112)
   at com.caucho.jmx.MBeanServerBuilderImpl.newMBeanServer(MBeanServerBuilderImpl.java:70)
   at javax.management.MBeanServerFactory.newMBeanServer(MBeanServerFactory.java:134)
   at javax.management.MBeanServerFactory.createMBeanServer(MBeanServerFactory.java:75)
   at com.caucho.loader.EnvironmentClassLoader.initializeEnvironment(EnvironmentClassLoader.java:567)
   at com.caucho.server.resin.Resin.init(Resin.java)
   at com.caucho.server.resin.Resin.main(Resin.java:627)
Caused by: java.lang.ClassNotFoundException: java.lang.annotation.Annotation not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:/etc/resin-3.0.21/lib/resin.jar,file:/etc/resin-3.0.21/lib/activation.jar,file:/etc/resin-3.0.21/lib/aopalliance.jar,file:/etc/resin-3.0.21/lib/ejb-20.jar,file:/etc/resin-3.0.21/lib/ejb-30.jar,file:/etc/resin-3.0.21/lib/j2ee-deploy-10.jar,file:/etc/resin-3.0.21/lib/j2ee-management-10.jar,file:/etc/resin-3.0.21/lib/javamail-14.jar,file:/etc/resin-3.0.21/lib/jca-15.jar,file:/etc/resin-3.0.21/lib/jms-11.jar,file:/etc/resin-3.0.21/lib/jmx-12.jar,file:/etc/resin-3.0.21/lib/jsdk-24.jar,file:/etc/resin-3.0.21/lib/jstl-11.jar,file:/etc/resin-3.0.21/lib/jta-101.jar,file:/etc/resin-3.0.21/lib/portlet-10.jar,file:/etc/resin-3.0.21/lib/quercus.jar,file:/etc/resin-3.0.21/lib/resin-jdk15.jar,file:/etc/resin-3.0.21/lib/resin.jar,file:/etc/resin-3.0.21/lib/resinboot.jar,file:/etc/resin-3.0.21/lib/script-10.jar,file:/etc/resin-3.0.21/lib/webutil.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...8 more
java.lang.NoClassDefFoundError: com.caucho.jmx.IntrospectionMBean
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.caucho.jmx.Jmx.createMBean(Jmx.java:269)
   at com.caucho.jmx.Jmx.register(Jmx.java:252)
   at com.caucho.management.server.AbstractManagedObject.registerSelf(AbstractManagedObject.java:125)
   at com.caucho.server.resin.ResinAdmin.<init>(ResinAdmin.java:57)
   at com.caucho.server.resin.ResinServer.<init>(ResinServer.java:156)
   at com.caucho.server.resin.Resin.init(Resin.java)
   at com.caucho.server.resin.Resin.main(Resin.java:627)


Does anybody have an idea of what i going wrong 

THanks :

---

