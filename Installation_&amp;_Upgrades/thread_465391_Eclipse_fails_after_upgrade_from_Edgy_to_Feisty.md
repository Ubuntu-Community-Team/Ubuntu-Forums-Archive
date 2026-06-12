---
title: "Eclipse fails after upgrade from Edgy to Feisty"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by RobertLos on 2007-06-05
Hello dears,

Please advice on the following puzzle:

I recently upgrade my ubuntu-box from edgy eft to Feisty. I do a lot of web development and my favorite IDE is eclipse. With eclipse I use phpeclipse for PHP-development.

Since upgrading to feisty eclipse 3.2.2. crashes on startup with a dialog box like

-----------------------------------
An error has occurred. See the log file
/home/robert/.eclipse/org.eclipse.platform_3.2.0/configuration/1181078175933.log.
-------------------------------------

(I got the same type of error when starting as root).

I tried removing eclipse and reinstall it again using apt. Didn't help. 

Any ideas?

additional information:

Java was upgraded to java6 during the upgrade. The content of /usr/lib/eclipse/eclipse.ini was changed to
---------------------------
-vmargs
-Xms40m
-Xmx256m
-Djava.library.path=/usr/lib/jni
-----------------------------------------------

The content of /etc/eclipse/java_home is
--------------------------------
# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun
---------------------------------------

> java -version produces: 
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)

-------------------------------
can it be that the wrong java version is used? And how to correct this?


for information I print the log-file.

---------------------------
!SESSION 2007-06-05 23:16:15.367 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2007-06-05 23:16:17.996
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-06-05 23:16:18.108
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-06-05 23:16:18.108
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-06-05 23:16:18.109
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-06-05 23:16:18.139
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (8).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:2389)
	at java.lang.Class.getConstructor0(Class.java:2699)
	at java.lang.Class.newInstance0(Class.java:326)
	at java.lang.Class.newInstance(Class.java:308)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
	... 62 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:2389)
	at java.lang.Class.getConstructor0(Class.java:2699)
	at java.lang.Class.newInstance0(Class.java:326)
	at java.lang.Class.newInstance(Class.java:308)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-06-05 23:16:18.143
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (67).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	... 32 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-06-05 23:16:18.345
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException: Plug-in org.eclipse.ui.ide was unable to load class org.eclipse.ui.internal.ide.IDEApplication.
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.throwException(RegistryStrategyOSGI.java:165)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:149)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2007-06-05 23:16:18.455
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.455
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.nl2 2 0 2007-06-05 23:16:18.455
!MESSAGE Missing host org.eclipse.platform_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.455
!MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nlBi[/email]di_4.1.30.1/ was not resolved.
!SUBENTRY 2 org.eclipse.tomcat.nlBidi 2 0 2007-06-05 23:16:18.456
!MESSAGE Missing host org.eclipse.tomcat_[4.1.30.1,4.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.456
!MESSAGE Bundle [email]update@plugins/org.eclipse.text.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.text.nl1 2 0 2007-06-05 23:16:18.456
!MESSAGE Missing host org.eclipse.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.456
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.ui.nl2 2 0 2007-06-05 23:16:18.456
!MESSAGE Missing host org.eclipse.jdt.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.456
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.core.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.core.nlBidi 2 0 2007-06-05 23:16:18.456
!MESSAGE Missing host org.eclipse.team.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.456
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.nlBidi 2 0 2007-06-05 23:16:18.456
!MESSAGE Missing host org.eclipse.jdt.junit_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.456
!MESSAGE Bundle [email]update@plugins/org.eclipse.sdk.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.sdk.nlBidi 2 0 2007-06-05 23:16:18.456
!MESSAGE Missing host org.eclipse.sdk_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.456
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.editors.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.editors.nl1 2 0 2007-06-05 23:16:18.456
!MESSAGE Missing host org.eclipse.ui.editors_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.456
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh.nl1 2 0 2007-06-05 23:16:18.457
!MESSAGE Missing host org.eclipse.team.cvs.ssh_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.457
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.rcp.nl1 2 0 2007-06-05 23:16:18.457
!MESSAGE Missing host org.eclipse.rcp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.457
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.isv.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.isv.nlBidi 2 0 2007-06-05 23:16:18.457
!MESSAGE Missing host org.eclipse.platform.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.457
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.nlBidi 2 0 2007-06-05 23:16:18.457
!MESSAGE Missing host org.eclipse.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.462
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.ui.refactoring.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring.nl2 2 0 2007-06-05 23:16:18.462
!MESSAGE Missing host org.eclipse.ltk.ui.refactoring_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.462
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.ui.nl2 2 0 2007-06-05 23:16:18.462
!MESSAGE Missing host org.eclipse.jdt.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.462
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.user.nlBi[/email]di/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.user.nlBidi 2 0 2007-06-05 23:16:18.462
!MESSAGE Missing host org.eclipse.platform.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.462
!MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nl[/email]2_4.1.30.1/ was not resolved.
!SUBENTRY 2 org.eclipse.tomcat.nl2 2 0 2007-06-05 23:16:18.462
!MESSAGE Missing host org.eclipse.tomcat_[4.1.30.1,4.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.462
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.ui.nlBidi 2 0 2007-06-05 23:16:18.463
!MESSAGE Missing host org.eclipse.team.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.463
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.ui.nl1 2 0 2007-06-05 23:16:18.464
!MESSAGE Missing host org.eclipse.pde.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.464
!
...
... a lot of similar lines removed for message size here
...
!MESSAGE Missing host org.eclipse.pde.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.525
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.junit.runtime.nlBi[/email]di_3.1.0/ [361] was not resolved.
!SUBENTRY 2 org.eclipse.pde.junit.runtime.nlBidi 2 0 2007-06-05 23:16:18.525
!MESSAGE Missing host org.eclipse.pde.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.525
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.nl1_3.1.0.jar[/email] [362] was not resolved.
!SUBENTRY 2 org.eclipse.pde.nl1 2 0 2007-06-05 23:16:18.525
!MESSAGE Missing host org.eclipse.pde_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.525
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.nl2_3.1.0.jar[/email] [363] was not resolved.
!SUBENTRY 2 org.eclipse.pde.nl2 2 0 2007-06-05 23:16:18.525
!MESSAGE Missing host org.eclipse.pde_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.525
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.nlBidi_3.1.0.jar[/email] [364] was not resolved.
!SUBENTRY 2 org.eclipse.pde.nlBidi 2 0 2007-06-05 23:16:18.525
!MESSAGE Missing host org.eclipse.pde_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.525
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.runtime.nl1_3.1.1.jar[/email] [365] was not resolved.
!SUBENTRY 2 org.eclipse.pde.runtime.nl1 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.pde.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.runtime.nl2_3.1.1.jar[/email] [366] was not resolved.
!SUBENTRY 2 org.eclipse.pde.runtime.nl2 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.pde.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.runtime.nlBidi_3.1.1.jar[/email] [367] was not resolved.
!SUBENTRY 2 org.eclipse.pde.runtime.nlBidi 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.pde.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.source.nl[/email]1_3.1.1/ [368] was not resolved.
!SUBENTRY 2 org.eclipse.pde.source.nl1 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.pde.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.source.nl[/email]2_3.1.1/ [369] was not resolved.
!SUBENTRY 2 org.eclipse.pde.source.nl2 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.pde.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.source.nlBi[/email]di_3.1.1/ [370] was not resolved.
!SUBENTRY 2 org.eclipse.pde.source.nlBidi 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.pde.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.ui.nl1_3.1.1.jar[/email] [371] was not resolved.
!SUBENTRY 2 org.eclipse.pde.ui.nl1 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.pde.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.ui.nl2_3.1.1.jar[/email] [372] was not resolved.
!SUBENTRY 2 org.eclipse.pde.ui.nl2 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.pde.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.ui.nlBidi_3.1.1.jar[/email] [373] was not resolved.
!SUBENTRY 2 org.eclipse.pde.ui.nlBidi 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.pde.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp.nl1_3.1.0.jar[/email] [374] was not resolved.
!SUBENTRY 2 org.eclipse.rcp.nl1 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.rcp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp.nl2_3.1.0.jar[/email] [375] was not resolved.
!SUBENTRY 2 org.eclipse.rcp.nl2 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.rcp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp.nlBidi_3.1.0.jar[/email] [376] was not resolved.
!SUBENTRY 2 org.eclipse.rcp.nlBidi 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.rcp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.sdk.nl[/email]1_3.1.1/ [377] was not resolved.
!SUBENTRY 2 org.eclipse.sdk.nl1 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.sdk_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.sdk.nl[/email]2_3.1.1/ [378] was not resolved.
!SUBENTRY 2 org.eclipse.sdk.nl2 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.sdk_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-05 23:16:18.526
!MESSAGE Bundle [email]update@plugins/org.eclipse.sdk.nlBi[/email]di_3.1.1/ [379] was not resolved.
!SUBENTRY 2 org.eclipse.sdk.nlBidi 2 0 2007-06-05 23:16:18.526
!MESSAGE Missing host org.eclipse.sdk_[3.1.1,3.2.0).

---

