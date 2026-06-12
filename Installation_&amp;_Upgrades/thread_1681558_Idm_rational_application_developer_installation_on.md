---
title: "Idm rational application developer installation on ubuntu"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by yozden on 2011-02-04
```
!SESSION 2011-02-04 18:44:13.052 -----------------------------------------------
eclipse.buildId=unknown
java.fullversion=J2RE 1.6.0 IBM J9 2.4 Linux x86-32 jvmxi3260sr5ifx-20090821_41076 (JIT enabled, AOT enabled)
J9VM - 20090821_041076_lHdSMr
JIT  - r9_20090518_2017
GC   - 20090417_AA
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=tr_TR
Framework arguments:  -product com.ibm.rational.rad.product.v75.ide
Command-line arguments:  -os linux -ws gtk -arch x86 -product com.ibm.rational.rad.product.v75.ide

!ENTRY org.eclipse.ui 2 0 2011-02-04 18:44:16.246
!MESSAGE Warnings while parsing the key bindings from the 'org.eclipse.ui.commands' extension point
!SUBENTRY 1 org.eclipse.ui 2 0 2011-02-04 18:44:16.246
!MESSAGE Could not parse key sequence: plug-in='com.ibm.etools.siteedit.editor', id='com.ibm.etools.siteedit.edit.navigation.label', keySequence='Shift+F3'

!ENTRY org.eclipse.osgi 4 0 2011-02-04 18:44:19.768
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: XPCOM error -2147467262
    at org.eclipse.swt.browser.Mozilla.error(Unknown Source)
    at org.eclipse.swt.browser.Mozilla.setText(Unknown Source)
    at org.eclipse.swt.browser.Browser.setText(Unknown Source)
    at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.generateContentForPage(Unknown Source)
    at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.dynamicStandbyStateChanged(Unknown Source)
    at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.doStandbyStateChanged(Unknown Source)
    at org.eclipse.ui.internal.intro.impl.model.AbstractIntroPartImplementation.standbyStateChanged(Unknown Source)
    at org.eclipse.ui.internal.intro.impl.model.IntroPartPresentation.standbyStateChanged(Unknown Source)
    at org.eclipse.ui.intro.config.CustomizableIntroPart.standbyStateChanged(Unknown Source)
    at org.eclipse.ui.internal.ViewIntroAdapterPart$2.run(Unknown Source)
    at org.eclipse.swt.custom.BusyIndicator.showWhile(Unknown Source)
    at org.eclipse.ui.internal.ViewIntroAdapterPart.setStandby(Unknown Source)
    at org.eclipse.ui.internal.WorkbenchIntroManager.setIntroStandby(Unknown Source)
    at org.eclipse.ui.internal.WorkbenchIntroManager.showIntro(Unknown Source)
    at org.eclipse.ui.internal.WorkbenchWindow$20.runWithException(Unknown Source)
    at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(Unknown Source)
    at org.eclipse.swt.widgets.RunnableLock.run(Unknown Source)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
    at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(Unknown Source)
    at org.eclipse.ui.internal.Workbench$27.runWithException(Unknown Source)
    at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(Unknown Source)
    at org.eclipse.swt.widgets.RunnableLock.run(Unknown Source)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
    at org.eclipse.ui.internal.Workbench.runUI(Unknown Source)
    at org.eclipse.ui.internal.Workbench.access$4(Unknown Source)
    at org.eclipse.ui.internal.Workbench$5.run(Unknown Source)
    at org.eclipse.core.databinding.observable.Realm.runWithDefault(Unknown Source)
    at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Unknown Source)
    at org.eclipse.ui.PlatformUI.createAndRunWorkbench(Unknown Source)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(Unknown Source)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(Unknown Source)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(Unknown Source)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(Unknown Source)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(Unknown Source)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
    at java.lang.reflect.Method.invoke(Unknown Source)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Unknown Source)
    at org.eclipse.equinox.launcher.Main.basicRun(Unknown Source)
    at org.eclipse.equinox.launcher.Main.run(Unknown Source)
    at org.eclipse.equinox.launcher.Main.main(Unknown Source)
```
This is the log file .

I installed RAD on ubuntu 10.10 .

when its starts up it says An eror occured see the /home/user/workspace/.metadata/.log 

How can i fix this?

---

