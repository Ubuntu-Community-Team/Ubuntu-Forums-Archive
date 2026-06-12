---
title: "When is the next LTS release due"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by kline on 2010-07-26
Anybody know when the next LTS of unbuntu is coming out?  I'm currently running 8.04 and cannot get it upgraded to 10.04.  Maybe 2011 will be a better year... .

---

### Post by JDorfler on 2010-07-26
April 2012.  There is a pattern.

---

### Post by wojox on 2010-07-26
> **kline said:**
> Anybody know when the next LTS of unbuntu is coming out?  I'm currently running 8.04 and cannot get it upgraded to 10.04.  Maybe 2011 will be a better year... .

Why can't you upgrade?

---

### Post by JDorfler on 2010-07-27
Turn off all your visual effects in 8.04 LTS, create a 10.04 LTS install disk.  Do a manual install when it comes to pick how and which disk you want to install your new install.  Do not pick to format your drive.  This way you will not lose anything.  Make sure you use the exact same Login and password.  Then reinstall through Synaptic your usual programs.  More than likely all your settings will remain.

---

### Post by kansasnoob on 2010-07-27
> **wojox said:**
> Why can't you upgrade?

Exactly what I wondered.

---

### Post by Mr_Speedy on 2010-07-27
August 12th 2010 [IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/star_on.png[/IMG] **Ubuntu 10.04.1 LTS** 

Ubuntu 10.04.1 LTS is basically 10.04 LTS with all the current updates. You might have more luck upgrading when the new install .iso comes out.

Personally I have never liked upgrading anything, and have always formated my HDD for a fresh install when a new OS comes out.

However, don't give up. I'm sure there is some sort of workaround that will allow you to upgrade... the right person just needs to see this and give some advice :)

---

### Post by dino99 on 2010-07-27
yes its better to start from scratch as lot of changes have been made since 8.04 (ext4, udev, grub2, ...)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by kline on 2010-07-27
Every time I try to move to 10.04, the laptop hangs upon reboot.  Yes, I have edited /boot/grub/menu.lst to change the 8.04 to 10.04 ...  But my laptop isn't a server.  I have a separate server. 

And I have also d/loaded the alternate CD;  nothing worked.  So I started again from scratch and installed 8.04 from my DVD.  Hm.  The =only= thing I did not do was upgrade the files before I hit the Upgrade button.  I'm pulling over 250+ binary files now.  Once more.

---

### Post by snowpine on 2010-07-27
Hi Kline, here is the prudent course of action, in my opinion: Burn a Live CD of the new 10.04 release. Try it in "with no change to your computer" mode for a while, until you are satisfied it is 100% compatible with your hardware and needs. 

Unfortunately, Ubuntu is not 100% bug free. Sometimes the upgrade process goes wrong and a fresh install of the new release is preferable. 

The good news is that 8.04 still has some support time left (April 2011) so you can be patient and thoroughly test the 10.04 Live CD (or wait for 10.04.1) until you are satisfied it'll work.

---

### Post by kline on 2010-07-27
> **snowpine said:**
> Hi Kline, here is the prudent course of action, in my opinion: Burn a Live CD of the new 10.04 release. Try it in "with no change to your computer" mode for a while, until you are satisfied it is 100% compatible with your hardware and needs. 

Unfortunately, Ubuntu is not 100% bug free. Sometimes the upgrade process goes wrong and a fresh install of the new release is preferable. 

The good news is that 8.04 still has some support time left (April 2011) so you can be patient and thoroughly test the 10.04 Live CD (or wait for 10.04.1) until you are satisfied it'll work.

Having tried 7 or 8 times and not succeded with 10.04, I'll wait for the 11.04 release.  There was a brief error dialog to the effect that X11 had failed.  I have tried the kubuntu DVD and the alternate and the desktop CD versions.  No screen.

---

### Post by Mr_Speedy on 2010-07-28
"So I started again from scratch and installed 8.04 from my DVD." (kline)

Since you are already starting from scratch, why not try installing 10.04 to a freshly formated partition?

Another thing... you mention your laptop hangs after installation (you see the grub, then all goes black.)

When you see the grub, try pressing "e"... then delete the words "quiet" and "splash", then add "nomodeset" in their place. (The press Ctrl and X to boot) This should allow you to boot into Ubuntu. One you're up and running, install your graphics card drivers.

If you're getting a black screen immediately after booting from the CD, then try pressing F6 when you see the purple screen for a few seconds (and again select "nomodeset" from the menu to the right).

I had a similar problem (black screen during installation / after reboot) I hope this helps... but the problem might be different from mine.

---

### Post by kline on 2010-07-29
After trying several times, nope, nothing.  I do see the grub screen [i think] for a few seconds.  Typing 'e' does nothing.   And hitting F6 after a reboot brings up the standard F6 screen.

Time for a bug report!

---

