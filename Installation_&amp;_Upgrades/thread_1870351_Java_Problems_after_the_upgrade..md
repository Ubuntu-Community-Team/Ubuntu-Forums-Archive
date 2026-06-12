---
title: "Java Problems after the upgrade."
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by dnyansagar on 2011-10-27
Hi everyone.
I have been using ubuntu for a while now.
But this recent upgrade of ubuntu from 11.04 to 11.10 has caused me some problems.
Mainly that some java applications are not running properly.
I was using Figtree(phylogenetic tree app.) which was working fine until this upgrade.
Now everytime I try to export from the application I get following error.
My java is not very good so I have hard time understanding the error.
I have reinstalled java JDK6 and also tried JDK7 but same error occurs.
Please help....
./dnyansagar

[INDENT]Exception in thread "AWT-EventQueue-0" java.lang.ExceptionInInitializerError
    at org.freehep.graphicsio.gif.GIFImageWriteParam.<init>(GIFImageWriteParam.java:28)
    at org.freehep.graphicsio.gif.GIFImageWriter.getDefaultWriteParam(GIFImageWriter.java:73)
    at org.freehep.graphicsio.exportchooser.ImageExportFileType.<init>(ImageExportFileType.java:71)
    at org.freehep.graphicsio.gif.GIFExportFileType.<init>(GIFExportFileType.java:42)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
    at java.lang.Class.newInstance0(Class.java:372)
    at java.lang.Class.newInstance(Class.java:325)
    at org.freehep.util.Service.providers(Service.java:71)
    at org.freehep.util.export.ExportFileTypeRegistry.addApplicationClasspathExportFileTypes(ExportFileTypeRegistry.java:118)
    at org.freehep.util.export.ExportFileTypeRegistry.getDefaultInstance(ExportFileTypeRegistry.java:50)
    at org.freehep.util.export.ExportFileType.getExportFileTypes(ExportFileType.java:181)
    at org.freehep.util.export.ExportFileType.getExportFileTypes(ExportFileType.java:173)
    at org.freehep.util.export.ExportDialog.addAllExportFileTypes(ExportDialog.java:64)
    at org.freehep.util.export.ExportDialog.<init>(ExportDialog.java:130)
    at org.freehep.util.export.ExportDialog.<init>(ExportDialog.java:90)
    at org.freehep.util.export.ExportDialog.<init>(ExportDialog.java:82)
    at figtree.application.FigTreeFrame.doExportGraphic(Unknown Source)
    at figtree.application.FigTreeFrame$22.actionPerformed(Unknown Source)
    at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:2012)
    at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2335)
    at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:404)
    at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:259)
    at javax.swing.AbstractButton.doClick(AbstractButton.java:374)
    at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:829)
    at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:873)
    at java.awt.Component.processMouseEvent(Component.java:6268)
    at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
    at java.awt.Component.processEvent(Component.java:6033)
    at java.awt.Container.processEvent(Container.java:2045)
    at java.awt.Component.dispatchEventImpl(Component.java:4629)
    at java.awt.Container.dispatchEventImpl(Container.java:2103)
    at java.awt.Component.dispatchEvent(Component.java:4455)
    at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4633)
    at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4297)
    at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4227)
    at java.awt.Container.dispatchEventImpl(Container.java:2089)
    at java.awt.Window.dispatchEventImpl(Window.java:2517)
    at java.awt.Component.dispatchEvent(Component.java:4455)
    at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:649)
    at java.awt.EventQueue.access$000(EventQueue.java:96)
    at java.awt.EventQueue$1.run(EventQueue.java:608)
    at java.awt.EventQueue$1.run(EventQueue.java:606)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:116)
    at java.awt.EventQueue$2.run(EventQueue.java:622)
    at java.awt.EventQueue$2.run(EventQueue.java:620)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:619)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)
Caused by: java.lang.NullPointerException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.freehep.graphics2d.PixelGraphics2D.<clinit>(PixelGraphics2D.java:101)
    ... 59 more

[/INDENT]

---

### Post by iggi916 on 2012-03-06
I am having the same problem with exporting graphics from NMRViewJ, a java-based software for visualizing NMR data.

---

