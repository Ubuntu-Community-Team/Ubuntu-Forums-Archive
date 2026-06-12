---
title: "Eclipse Problems...and I can't find it's log file!"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by japtar10101 on 2007-12-09
After being so frustrated at attempting to download many plugins to Eclipse, I finally decided to trash it and re-install the program again.  And the newly re-installed Eclipse doesn't open, instead giving me this error:
```
An error has occurred. See the log file
/home/omiyat/.eclipse/org.eclipse.platform_3.2.0/configuration/1197225721754.log.
```
I wish I could be more informative than this, but I can't.  The .eclipse directory contained nothing, nor could it find org.eclipse.platform_3.2.0 directory anywhere.  The log file, even under my terminal, is non-existent.

Is there anything I can do to fix this?  I really want to point a finger at Aptana's plugin for causing all this trouble, but I really don't know where the problem originated.  If Eclipse posts any other log files that could pinpoint my errors, please tell me!

Rather desperate, but thanks for the help!

---

### Post by japtar10101 on 2007-12-09
Hmm...Well, I managed to download Aptana singly instead, and THAT doesn't open either.  Here's the error log I get from that:
```
!SESSION 2007-12-09 14:24:59.015 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.7.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  Studio
Command-line arguments:  -os linux -ws gtk -arch x86 Studio

!ENTRY org.eclipse.equinox.common 4 0 2007-12-09 14:24:59.400
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: The bundle could not be resolved. Reason: Missing Constraint: Bundle-RequiredExecutionEnvironment: CDC-1.0/Foundation-1.0,J2SE-1.3
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:294)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1046)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:573)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:495)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:275)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:455)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
	at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)

!ENTRY org.eclipse.update.configurator 4 0 2007-12-09 14:24:59.401
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: The bundle could not be resolved. Reason: Missing Constraint: Bundle-RequiredExecutionEnvironment: J2SE-1.4,CDC-1.0/Foundation-1.0,J2SE-1.3
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:294)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1046)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:573)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:495)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:275)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:455)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
	at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)

!ENTRY org.eclipse.core.runtime 4 0 2007-12-09 14:24:59.402
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: The bundle could not be resolved. Reason: Missing Constraint: Bundle-RequiredExecutionEnvironment: CDC-1.0/Foundation-1.0,J2SE-1.3
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:294)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1046)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:573)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:495)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:275)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:455)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
	at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)

!ENTRY org.eclipse.osgi 4 0 2007-12-09 14:24:59.407
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.equinox.common_3.2.0.v20060603.jar/ was not resolved.

!ENTRY org.eclipse.osgi 4 0 2007-12-09 14:24:59.407
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.update.configurator_3.2.2.R32x_v20070111.jar/ was not resolved.

!ENTRY org.eclipse.osgi 4 0 2007-12-09 14:24:59.407
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.core.runtime_3.2.0.v20060603.jar/ was not resolved.

!ENTRY org.eclipse.osgi 4 0 2007-12-09 14:24:59.418
!MESSAGE Application error
!STACK 1
java.lang.IllegalStateException: Unable to acquire application service. Ensure that the org.eclipse.core.runtime bundle is resolved and started (see config.ini).
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:65)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:623)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2007-12-09 14:24:59.425
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-12-09 14:24:59.425
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.update.configurator_3.2.2.R32x_v20070111.jar/ was not resolved.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2007-12-09 14:24:59.425
!MESSAGE Missing imported package javax.xml.parsers_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2007-12-09 14:24:59.425
!MESSAGE Missing imported package org.xml.sax_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2007-12-09 14:24:59.425
!MESSAGE Missing imported package org.xml.sax.helpers_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2007-12-09 14:24:59.426
!MESSAGE Missing imported package org.w3c.dom_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-12-09 14:24:59.427
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.core.runtime_3.2.0.v20060603.jar/ was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2007-12-09 14:24:59.427
!MESSAGE Missing required bundle org.eclipse.equinox.preferences_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2007-12-09 14:24:59.427
!MESSAGE Missing required bundle org.eclipse.equinox.registry_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2007-12-09 14:24:59.427
!MESSAGE Missing required bundle org.eclipse.core.contenttype_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2007-12-09 14:24:59.427
!MESSAGE Missing required bundle org.eclipse.core.jobs_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 2 0 2007-12-09 14:24:59.440
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-12-09 14:24:59.444
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.equinox.common_3.2.0.v20060603.jar/ [1] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.common 2 0 2007-12-09 14:24:59.444
!MESSAGE Missing Constraint: Bundle-RequiredExecutionEnvironment: CDC-1.0/Foundation-1.0,J2SE-1.3
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-12-09 14:24:59.444
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.update.configurator_3.2.2.R32x_v20070111.jar/ [2] was not resolved.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2007-12-09 14:24:59.444
!MESSAGE Missing required bundle org.eclipse.equinox.common_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2007-12-09 14:24:59.444
!MESSAGE Missing imported package javax.xml.parsers_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2007-12-09 14:24:59.444
!MESSAGE Missing imported package org.w3c.dom_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2007-12-09 14:24:59.444
!MESSAGE Missing imported package org.xml.sax_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2007-12-09 14:24:59.444
!MESSAGE Missing imported package org.xml.sax.helpers_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-12-09 14:24:59.444
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.core.runtime_3.2.0.v20060603.jar/ [3] was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2007-12-09 14:24:59.444
!MESSAGE Missing required bundle org.eclipse.equinox.common_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2007-12-09 14:24:59.444
!MESSAGE Missing required bundle org.eclipse.core.jobs_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2007-12-09 14:24:59.445
!MESSAGE Missing required bundle org.eclipse.equinox.registry_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2007-12-09 14:24:59.445
!MESSAGE Missing required bundle org.eclipse.equinox.preferences_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2007-12-09 14:24:59.445
!MESSAGE Missing required bundle org.eclipse.core.contenttype_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2007-12-09 14:24:59.445
!MESSAGE Missing optionally required bundle org.eclipse.core.runtime.compatibility.auth_[3.2.0,4.0.0).
```

---

### Post by paranoid_humanoid on 2008-04-09
i get the error with the standalone aptana community version too..
why hasn't somebody figured this out yet!! i really need it :confused:. i hate booting into windows to use dreamweaver :mad:

---

### Post by daxumaming on 2008-04-10
I just installed it, you may have a different error than mine, but here's what I did to get Aptana running:
1) install sun-java6-jdk
2) run: sudo update-java-alternatives --set java-6-sun

Oh, btw, I'm using the version from [http://www.aptana.com/studio/download](http://www.aptana.com/studio/download)

---

### Post by davham on 2008-05-16
worked like a charm 
Thank You
David

ps
You should post it to the Aptana site

---

### Post by japtar10101 on 2008-05-17
> **daxumaming said:**
> I just installed it, you may have a different error than mine, but here's what I did to get Aptana running:
1) install sun-java6-jdk
2) run: sudo update-java-alternatives --set java-6-sun

Oh, btw, I'm using the version from [http://www.aptana.com/studio/download](http://www.aptana.com/studio/download)

Well, now Eclipse open up, which is great!

But now I get this error: "you're using outdated java library!  upgrade up to JRE 1.5!" error.

---

### Post by willworkforart on 2008-05-27
I'm been trying to set up aptana for a couple days now - thought I finally stumbled on the solution here, but still get an error when I go to launch it. Any help would be greatly appreciated. This is what the log file says:

```
!SESSION 2008-05-27 22:24:21.931 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  Studio
Command-line arguments:  -os linux -ws gtk -arch x86 Studio

!ENTRY org.eclipse.osgi 4 0 2008-05-27 22:24:25.134
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/wwfa/aptana/configuration/org.eclipse.osgi/bundles/109/1/.cp/libswt-pi-gtk-3236.so: /home/wwfa/aptana/configuration/org.eclipse.osgi/bundles/109/1/.cp/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:436)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at com.aptana.ide.rcp.AbstractIDEApplication.createDisplay(AbstractIDEApplication.java:152)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:89)
	at com.aptana.ide.rcp.Application.run(Application.java:43)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
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

!ENTRY org.eclipse.osgi 2 0 2008-05-27 22:24:25.145
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-05-27 22:24:25.145
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.0.0.009905.jar was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-05-27 22:24:25.145
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.

!ENTRY org.eclipse.osgi 2 0 2008-05-27 22:24:25.145
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-05-27 22:24:25.145
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.0.0.009905.jar [19] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-05-27 22:24:25.145
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.
!SESSION 2008-05-27 22:27:38.658 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  Studio
Command-line arguments:  -os linux -ws gtk -arch x86 Studio

!ENTRY org.eclipse.osgi 4 0 2008-05-27 22:27:39.747
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/wwfa/aptana/configuration/org.eclipse.osgi/bundles/109/1/.cp/libswt-pi-gtk-3236.so: /home/wwfa/aptana/configuration/org.eclipse.osgi/bundles/109/1/.cp/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:436)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at com.aptana.ide.rcp.AbstractIDEApplication.createDisplay(AbstractIDEApplication.java:152)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:89)
	at com.aptana.ide.rcp.Application.run(Application.java:43)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
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

!ENTRY org.eclipse.osgi 2 0 2008-05-27 22:27:39.792
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-05-27 22:27:39.792
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.0.0.009905.jar was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-05-27 22:27:39.792
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.

!ENTRY org.eclipse.osgi 2 0 2008-05-27 22:27:39.792
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-05-27 22:27:39.792
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.0.0.009905.jar [19] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-05-27 22:27:39.793
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.
!SESSION 2008-05-27 22:31:47.019 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  Studio
Command-line arguments:  -os linux -ws gtk -arch x86 Studio

!ENTRY org.eclipse.osgi 4 0 2008-05-27 22:31:50.232
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/wwfa/aptana/configuration/org.eclipse.osgi/bundles/109/1/.cp/libswt-pi-gtk-3236.so: /home/wwfa/aptana/configuration/org.eclipse.osgi/bundles/109/1/.cp/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:436)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at com.aptana.ide.rcp.AbstractIDEApplication.createDisplay(AbstractIDEApplication.java:152)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:89)
	at com.aptana.ide.rcp.Application.run(Application.java:43)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
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

!ENTRY org.eclipse.osgi 2 0 2008-05-27 22:31:50.267
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-05-27 22:31:50.267
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.0.0.009905.jar was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-05-27 22:31:50.267
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.

!ENTRY org.eclipse.osgi 2 0 2008-05-27 22:31:50.268
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-05-27 22:31:50.268
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.0.0.009905.jar [19] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-05-27 22:31:50.268
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.
```

---

