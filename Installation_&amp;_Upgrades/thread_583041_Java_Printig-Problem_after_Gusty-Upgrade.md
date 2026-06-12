---
title: "Java Printig-Problem after Gusty-Upgrade"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by sleopold on 2007-10-20
Hallo,

if i want to print from an Java-Appklcation if got this error: 

 Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException: null attribute
        at sun.print.IPPPrintService.isAttributeValueSupported(IPPPrintService.java:1147)
        at sun.print.ServiceDialog$OrientationPanel.updateInfo(ServiceDialog.java:2121)
        at sun.print.ServiceDialog$PageSetupPanel.updateInfo(ServiceDialog.java:1263)
        at sun.print.ServiceDialog.updatePanels(ServiceDialog.java:437)
        at sun.print.ServiceDialog.initPrintDialog(ServiceDialog.java:195)
        at sun.print.ServiceDialog.<init>(ServiceDialog.java:124)
        at javax.print.ServiceUI.printDialog(ServiceUI.java:188)
        at sun.print.RasterPrinterJob.printDialog(RasterPrinterJob.java:855)
        at javax.swing.JTable.print(JTable.java:6195)
        at javax.swing.JTable.print(JTable.java:6046)
        at javax.swing.JTable.print(JTable.java:6001)
        at javax.swing.JTable.print(JTable.java:5966)
        at javax.swing.JTable.print(JTable.java:5940)
        at jfakt.einnahmen_drucken(jfakt.java:728)
        at jfakt.actionPerformed(jfakt.java:623)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
        at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
        at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1216)
        at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1257)
        at java.awt.Component.processMouseEvent(Component.java:6038)
        at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
        at java.awt.Component.processEvent(Component.java:5803)
        at java.awt.Container.processEvent(Container.java:2058)
        at java.awt.Component.dispatchEventImpl(Component.java:4410)
        at java.awt.Container.dispatchEventImpl(Container.java:2116)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
        at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
        at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
        at java.awt.Container.dispatchEventImpl(Container.java:2102)
        at java.awt.Window.dispatchEventImpl(Window.java:2429)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)

I got this problem after doing the Gusty-Upgrade (amd64) wiht Feisty tehe is no printing-problem.

---

### Post by zoranc on 2007-10-26
I had the same problem after upgrading to Gutsy and problem is with cupsys 1.3.2. At this moment only way to get print out of Java application is to downgrade cupsys to 1.2.8 version. After I did it printing from Java applications works again. Here is a shell for downgrading to cupsys 1.2.8:

---

### Post by sleopold on 2007-10-28
OK thats it! Everything work fine.

Thank you!

---

### Post by nysanu on 2008-04-29
I also had this problem after installing Ubuntu 8.04.
When attempting to downgrade cupsys, this failed due to dependencies to libldap2, that was not installable.

But, the problem lies within the JVM, so the problem was fixed when I installed a pre-release of it, 6u10 build b20, that can be found at [http://download.java.net/jdk6/6u10/promoted/b20/](http://download.java.net/jdk6/6u10/promoted/b20/).

I assume you already have java-6-sun-1.6.0.06 installed.

The steps (a bit ugly, but works):
1) Download the appropriate build (pick the .bin)
2) Do a chmod 755 on the downloaded build
3) Change directory to /usr/lib/jvm
4) Execute the downloaded build; /<location>/<build>.bin
   This will unpack the JVM into jdk1.6.0_10
5) Make a symbolic link to point to the JVM
   sudo ln -s jdk1.6.0_10 java-6-sun

That's it. Now printing from java applications work, even when using the latest cupsys.

Good luck!

---

