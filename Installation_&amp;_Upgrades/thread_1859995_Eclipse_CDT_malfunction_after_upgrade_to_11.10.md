---
title: "Eclipse CDT malfunction after upgrade to 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by s-valley on 2011-10-14
I just upgraded my system 11.04 to 11.10.   It upgraded my eclipse from Galileo to Indigo.  Now my CDT seems to be not working.

the error message as follows:

**Message**
Unable to create editor ID org.eclipse.cdt.ui.editor.CEditor: No editor descriptor for id org.eclipse.cdt.ui.editor.CEditor

**Exception stack trace**
org.eclipse.ui.PartInitException: No editor descriptor for id org.eclipse.cdt.ui.editor.CEditor
	at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:601)
	at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:465)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
	at org.eclipse.ui.internal.EditorAreaHelper.setVisibleEditor(EditorAreaHelper.java:271)
	at org.eclipse.ui.internal.EditorManager.setVisibleEditor(EditorManager.java:1459)
	at org.eclipse.ui.internal.EditorManager$5.runWithException(EditorManager.java:972)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3563)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3212)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
	at org.eclipse.ui.internal.Workbench$33.runWithException(Workbench.java:1595)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3563)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3212)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2604)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2494)
	at org.eclipse.ui.internal.Workbench$7.run(Workbench.java:674)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:667)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:123)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:622)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:577)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1410)


**Session Data**

eclipse.buildId=I20110613-1736
java.version=1.6.0_23
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86


Please help me.

---

### Post by shumifan50 on 2011-12-13
I suffer the same problem. Did anybody find a solution to this. Looking at the error log displayed, it looks like it also broke Qt integration.

Any help appreciated.

I would also like to integrate subversion, bt that has a problem in Eclipse Indigo/ubuntu as the libsvn-java required by Indigo is not available on ubuntu.

---

### Post by shumifan50 on 2011-12-13
I fixed the CDT problem by setting up the eclipse URL for the 8.1 CDT in eclipse to fetch the new version. I then installed the 8.1 CDT from eclipse and it all started working again.

---

### Post by romulusnr on 2012-01-31
I don't understand why there are so many issues like this in 11.10. 

Even Win 98 or Vista wasn't this bad.

Everything is broken, choice taken away, replaced with apps with less flexibility, broken upgrade paths for mission-critical software (what, no one uses Eclipse? are you kidding?) 

Canonical is determined to convert Linux from a powerful OS to a cute OS. Blech.

inb4 ala "you're wrong about flexibility, just install ccsm and you can change the icon size, see?"

Ranting, because after fighting with Gnome 3's INcompatible, fake "Gnome 2 look" for a day, and fighting with Unity for another day, I'm now fighting with Eclipse for a day. Not something my company probably considers very productive, and not a good sell for workplace Linux.

Oneiric = Form over function? You betcha!

---

### Post by SteMMo on 2012-02-02
I have the same problem(s) but for Java development.
I configured Eclipse 3.7.1 for Android development but now it is all break.
The upgrade silently substituted OOO and Eclipse and now i'm stucked !!!
In this way Ubuntu will never enter in a office or any other serious use!!! :confused:


File Java:
Could not open the editor: No editor descriptor for id org.eclipse.jdt.ui.CompilationUnitEditor

File xml:
Could not open the editor: No editor descriptor for id org.eclipse.wst.xml.ui.internal.tabletree.XMLMultiPageEditorPart

Version: 3.7.0
Build id: I20110613-1736

No New file or new project for Java, only CVS.

Help > Install new software: no packages in the list.

---

### Post by zob on 2012-04-24
I have the same problem as SteMMo. My eclipse was setup for android development. But under an upgrade of the ADT this happened. Now it seems half of the functionality of eclipse has dissapeared. No more syntax highlighting. It doesn't seem to recognize different filetypes (all the small icons in navigator or project explorer, be it for .java or .xml or whatever, now just look the icons for .txt-files).I don't know, maybe it's some setting, but I really don't have a clue.

I also get the same error messages as SteMMo mentioned.

I'm on ubuntu 12.04 (I don't think that is the problem though).
Eclipse version: 3.7.2-1
Build id: I20110613-1736

Just want to follow the thread...


I just tried to revert the updates. Got this error messages: [http://paste.ubuntu.com/944625/](http://paste.ubuntu.com/944625/)

I'll have to make sure it's not just server that's down or something. But now you know (if you want to).

---

### Post by zob on 2012-04-24
Just tried to reinstall everything. Java, eclipse and stuff. I'm still having the same problem. This is actually crazy. Even the option to create a new java project has disappeared from eclipse...

---

### Post by Bonta on 2012-06-18
I have had this problem when running downloaded Eclipse as well as repository installed Eclipse.

---

### Post by zob on 2012-06-19
I should maybe add that it worked very well for me when I finally deleted the repos installation an got eclipse from here: [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

---

