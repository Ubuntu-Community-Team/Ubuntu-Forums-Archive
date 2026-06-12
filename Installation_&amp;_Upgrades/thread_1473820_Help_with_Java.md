---
title: "Help with Java"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by erikja on 2010-05-05
Hi.

I run an antenna measuring instrument on my Ubuntu 10.04.
It has just been set up, but I have issues, that I cannot
handle myself.

```
java -jar vnaJ.2.5.2.jar 
INFO::Application version....2.5.2 2010-05-04
INFO::Java version...........1.5.0
INFO::Java runtime.version...1.5.0
INFO::Java vm.version........4.4.3
INFO::Java vm.vendor.........Free Software Foundation, Inc.
INFO::OS.....................i386 Linux 2.6.32-22-generic
INFO::Country/Language.......DK / en
INFO::Createing Config-Directory: /home/erik/vnaJ/config
INFO::Createing Calibration-Directory: /home/erik/vnaJ/calibration
WARNING:  RXTX Version mismatch
	Jar version = RXTX-2.2pre1
	native lib Version = RXTX-2.2pre2
Exception during event dispatch:
java.lang.NoClassDefFoundError: krause.vna.background.VnaBackgroundTask
   at krause.vna.gui.calibrate.VNACalibrationDialog.doMeasure(VNACalibrationDialog.java:447)
   at krause.vna.gui.calibrate.VNACalibrationDialog.doMeasureOpen(VNACalibrationDialog.java:461)
   at krause.vna.gui.calibrate.VNACalibrationDialog.access$3(VNACalibrationDialog.java:458)
   at krause.vna.gui.calibrate.VNACalibrationDialog$10.actionPerformed(VNACalibrationDialog.java:276)
   at javax.swing.AbstractButton.fireActionPerformed(libgcj.so.10)
   at javax.swing.AbstractButton$EventHandler.actionPerformed(libgcj.so.10)
   at javax.swing.DefaultButtonModel.fireActionPerformed(libgcj.so.10)
   at javax.swing.DefaultButtonModel.setPressed(libgcj.so.10)
   at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(libgcj.so.10)
   at java.awt.Component.processMouseEvent(libgcj.so.10)
   at java.awt.Component.processEvent(libgcj.so.10)
   at java.awt.Container.processEvent(libgcj.so.10)
   at java.awt.Component.dispatchEventImpl(libgcj.so.10)
   at java.awt.Container.dispatchEventImpl(libgcj.so.10)
   at java.awt.Component.dispatchEvent(libgcj.so.10)
   at java.awt.LightweightDispatcher.redispatch(libgcj.so.10)
   at java.awt.LightweightDispatcher.handleMouseEvent(libgcj.so.10)
   at java.awt.LightweightDispatcher.dispatchEvent(libgcj.so.10)
   at java.awt.Container.dispatchEventImpl(libgcj.so.10)
   at java.awt.Window.dispatchEventImpl(libgcj.so.10)
   at java.awt.Component.dispatchEvent(libgcj.so.10)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.10)
   at java.awt.EventDispatchThread.run(libgcj.so.10)


```

What can I do to get it to run ok ?

---

### Post by VeeDubb on 2010-05-05
What I would do, which I always do after a new install, is get rid of the semi-useless open-java garbage, and install proper java.

If you have all the extra repos available, Sun Java is available in the repos.

---

### Post by erikja on 2010-05-06
> **VeeDubb said:**
> What I would do, which I always do after a new install, is get rid of the semi-useless open-java garbage, and install proper java.

If you have all the extra repos available, Sun Java is available in the repos.

Thank you for your reply and suggestion.
Could you please give me a link to where I can download proper java, and also where I can see how to edit/add repos.

Thanks i advance

---

### Post by VeeDubb on 2010-05-06
There's no need to download it manually.

Click the system menu, Administration, Software sources.

Check all of the check boxes on the first two tabs, then close the program.  

When prompted, let it reload all the sources.


Click the system menu, Administration, Synaptic Package Manager

In the search box at the top of the window, type sun-java and you'll see the real sun java appear in the list.  Install everyhting having to do with sun Java.

Everything is already there waiting for you.

---

### Post by erikja on 2010-05-06
> **VeeDubb said:**
> There's no need to download it manually.

Click the system menu, Administration, Software sources.

Check all of the check boxes on the first two tabs, then close the program.  

When prompted, let it reload all the sources.


Click the system menu, Administration, Synaptic Package Manager

In the search box at the top of the window, type sun-java and you'll see the real sun java appear in the list.  Install everyhting having to do with sun Java.

Everything is already there waiting for you.

Hi VeeDubb.

Thanks for your kind reply to me. I did what you suggested, and it all worked flawlessly :D

Now the set up for the measuring tool is working too, and happy I am.

):P

---

