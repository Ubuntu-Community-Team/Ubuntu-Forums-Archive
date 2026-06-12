---
title: "Upgraded to Hardy, everything went well but..."
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by stchman on 2008-05-06
Hello all, I just reformatted and installed Hardy.  I must say I am fairly impressed.  Compiz works OOB and the restricted driver manager installed the 169.12 for my 8800GT.

I have a few issues.

1.  I have an Audigy 2 and the rear speakers will not work.  They worked in Feisty.

2.  How do you get VLC to start playing DVDs when inserted into the drive.  I see that you can select something in Nautilus, but I cannot enter the vlc %m like I could in Feisty.

3.  The foo2zjs driver does not work with my Laserjet 1000 printer.  I went to [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) and no dice still.  Anyone have any luck?

4.  I installed the Java 1.6 JRE via Synaptic and Openoffice 2.4 cannot find it.

Everything else runs just fine.  I did notice that when I installed a different GDM login theme the login window took forever to appear.

---

### Post by stchman on 2008-05-07
I figured most of them out.

1.  System--->Preferences--->Sound, select Devices tab and select ALSA for all options.

2.  I edited the VLC menu to have vlc %m

3.  Laserjet 1000 still not working.

4.  I installed the openoffice.org-java-common package and now OO can use the 1.6 JRE.

I would still like some input on the Laserjet 1000 foo2zjs stuff.  Does anyone else have any idea on how to get VLC to use the 4 speaker stuff?

Thanks.

---

### Post by stchman on 2008-05-07
I figured out the Laserjet 1000 stuff.

If you install the HPLIP GUI and then have it install the Laserjet 1000 it downloads the firmware and installs the driver.

---

