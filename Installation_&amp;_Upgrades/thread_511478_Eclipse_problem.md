---
title: "Eclipse problem"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by djzwalex on 2007-07-27
Hi.
I installed Eclipse but I can't start it up :-(
I have read related topics and tried them out but it doesn't help me.
I already installer different java-programs:
Sun java runtime  5.0
Sun Java 6 Web Start
java web start 1.4
Sun java 5.0 console 
Sun Java 6 Console
 Java 1.4 plugin for mozilla/firefox




The log file say's

!ENTRY org.eclipse.osgi 4 0 2007-07-28 02:53:09.462
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (211).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid

Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.WorkbenchPlugin


!ENTRY org.eclipse.ui.navigator 4 0 2007-07-28 02:53:09.475
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.navigator.NavigatorPlugin for bundle org.eclipse.ui.navigator is invalid

the attachment is the complete log file.
thanks a lot.


greets me

---

### Post by jctweb on 2007-09-22
Eclipse - it's a nightmare lately.  It worked fine until I tried upgrading to 3.3 - now I can't even get 3.2.2 from the repo working :(

---

### Post by myxsys on 2008-01-12
Download eclipse tarball from the eclipse site. Works fine

---

