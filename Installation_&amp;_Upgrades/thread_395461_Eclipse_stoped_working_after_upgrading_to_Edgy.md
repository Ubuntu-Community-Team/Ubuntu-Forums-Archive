---
title: "Eclipse stoped working after upgrading to Edgy"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by hfilter on 2007-03-28
Hi 
After upgrading to Edgy (32-bit) using the official method my Eclipse IDE stopped working.

If I try to start eclipse it gives a message: "An error has occurred. See the log file /home/heinrichf/workspace/.metadata/.log"

And the log contains the following:
```

!SESSION 2007-03-28 13:54:07.347 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_ZA
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2007-03-28 13:54:12.541
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-03-28 13:54:12.542
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-03-28 13:54:12.542
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-03-28 13:54:12.543
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2007-03-28 13:54:17.050
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2007-03-28 13:54:17.289
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (7).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:86)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:409)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /ncbmis/include/workflow/requestService/srAddActivity.php not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 27 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /ncbmis/include/workflow/requestService/srAddActivity.php not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:86)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:409)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-03-28 13:54:17.372
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)


```

If I run eclipse as a super user there are no problems.

I suspect it has something to do with the eclipse plugins that were installed on the previous version of eclipse (and these plugins were not installed for root).

Any help would be greatly appreciated.

Thank you
Heinrich

---

### Post by Xanadu on 2007-03-30
I had a similar issue after a system crash and the following worked for me:
1. Rename workspace (mv workspace workspace.bak)
2. Start Eclipse
3. Import the projects from workspace.bak (with the "copy files" box checked)

---

### Post by hfilter on 2007-03-30
Thank you Xanadu. That worked for me as well!:) 

Your help is much appreciated.

Heinrich

---

### Post by hfilter on 2007-03-30
At least Eclipse is starting up now, but does anyone know how to move the plug-ins that were installed on eclipse 3.1.

Thanks
Heinrich.

---

