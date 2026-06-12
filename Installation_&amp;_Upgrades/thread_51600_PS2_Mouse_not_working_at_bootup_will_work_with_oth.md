---
title: "PS/2 Mouse not working at bootup will work with other"
date: 2005-07-24
forum: Installation &amp; Upgrades
---

### Post by daxumaming on 2005-07-24
Hi guys. I'm having a problem here. I'm not sure if it's X, ps/2 mouse, or even grub.

After 3 hours of installing Ubuntu, I found out that the mouse doesn't work from the login to the desktop. I tried googling about this problem and found some solutions, tried all of them but didn't work. 

From the desktop, which seems frozen, I did "Ctrl+Alt+F1" went to the command line, edited /etc/modules but I cant startx. So I reboot, logged in, mouse still not working, then "Ctrl+Alt+Backspace" from desktop, configured some files again and again until all the solutions I found has been exhausted. Anyway, here's what I did.

1. made sure "mousedev" & "psmouse" properly listed in "etc/modules"

2. "/var/log/Xorg.0.log" indicates no errors or failures

3. changed "psmouse" to "psmouse proto=exps" & "psmouse.proto=imps" in "/etc/modules"

4. for "/etc/X11/xorg.conf":

  a. changed "Protocol" from "ImPS/2" to "PS/2" & "Auto"

  b. changed "Device" from "/dev/input/mice" to "/dev/psaux" & "/dev/input/mouse0"

Unfortunately, none worked. Frustrated, I boot up the Vector Linux 4.3 CD and saw that I could boot up a linux partition from there. So at the prompt I typed in "linux root=/dev/hda3 ro" got into the Ubuntu login screen and to my surprise, my mouse started to work. I logged in just to check that my eyes aren't deceiving me. Lo & behold, everything is working like it should be. For the first time, I got to enjoy Ubuntu. My logic told me that the 2.6.10 kernel of Ubuntu isn't working properly with my machine. Vector has 2.4 kernel. 

More determined than ever to find out the real cause of this problem, I booted up in recovery mode and tried scanning for any errors & failures, especially those referring to my mouse. The only error I got is when the machine is trying to sync the system clock. Then I found something. After 3 reboots, I got to list down this:

mice: PS/2 Mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on ISA0060/seria01

Is it possible that Ubuntu has setup my mouse on the ISA bus instead of the PS/2. How do I fix this? Do I need to edit some file? I tried locating the grub.conf, maybe I could start from there but I just can't locate it. Can anyone help me out here? I've been working on this computer for 16hours now and I'm a bit depressed, frustrated, & tired especially since I wanted to work with Ubuntu. Any help is deeply appreciated.


Hardware: P3 733Mhz, 384MB SDRAM, 64MB for onboard Video. Asus Motherboard, Sis630. 20GB Seagate HDD. hda3=/ (2GB)ReiserFS, hda5=/home (2GB)ReiserFS, hda6=swap (1GB).Lite-On CD-RW.

***Updates: 26July2005 0305H***

Errata: Vector 4.3 uses the 2.6.7 kernel. Either way, would this help me with my problem?

I finally got to edit Grub, it's not /etc/grub.conf but /boot/grub/menu.lst, but one thing I really need to know, does the "initrd /boot/initrd.img-2.6.10-5-386" contain a line or something that points to my mouse, if so, is it safe to edit? If not, are there any other files that loads at boot up that I might need to take a look at?

I tried copying the vmlinuz-2.6.7-ide4 of Vector to Ubuntu and changed the line in Grub to 'kernel /boot/vmlinuz-2.6.7-ide4 ro' and as expected, it didn't work. Well at least I'm not giving up on fixing this problem.

When I tried booting up Ubuntu using the Vector CD, I noticed that some lines had "fail" in them. I really can't see it well and can't pause it. But from what I know, it failed to load something in '/lib/...' 

If only someone with a kind heart tell me what file I need to edit that loads this thing, then maybe, just maybe, I'll be very happy with Ubuntu. It doesn't matter if it crashes the whole system and need to reinstall Ubuntu, I am after all, still learning Linux, and one great way of learning real quick is if you do a lot reinstalling, trial & error, and even configuring & rebooting. And everytime I mess something up, I learn something new.

I will still try configuring Ubuntu, but it willsave me a lot of time if someone with expertise in Ubuntu & Linux in general would give me a few pointers. 

I also tried googling regarding this issue, none seems to work. I must say, I have a very unique issue. Imagine, a ps/2 mouse not working in Linux... Ha!

I also like to thank you for spending some time reading this.

---

### Post by morbidi on 2005-08-08
well, I just realized that I have the same stress has you, and no manner to solve it, does any guru of ubuntu knows of this problem ? btw, I booted up with ubuntu livecd  hoary 5.04, and the mouse work perfectly, but in the install ubuntu it has the same message has yours does. :|

mice: PS/2 Mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on ISA0060/seria01

looking for an answer

---

### Post by pauleblum on 2005-10-19
Me too!!!  Please Help

---

### Post by blushores on 2006-08-05
I am having the same problem as well. If I connect my Microsoft USB optical mouse it works fine, but not the PS/2 mouse for some reason. If anyone has found a solution, please let us know.

Thanks,

---

### Post by Bart Schaefer on 2006-09-17
I may have a clue here.

I have an optical PS/2 mouse.  It doesn't work at all with Breezy or Dapper (I just upgraded).  Suspiciously, the tracking LED is lit when the BIOS is booting the system, but goes dark during ubuntu boot and never comes back on.

If I look at the device manager in Dapper, the i8042 aux port shows an unknown device.

However, if I unplug the optical mouse and plug in an old mechanical ball mouse, suddenly the device is fully detected and the mouse works just fine.

I think the aux port driver is failing to make hot a pin that the optical mouse is using for power, thereby disabling the mouse.  Is there anyone on this forum with enough hardware/driver know-how to suggest a fix?

---

### Post by Bart Schaefer on 2006-09-17
Aha:

[http://bugzilla.kernel.org/show_bug.cgi?id=5703](http://bugzilla.kernel.org/show_bug.cgi?id=5703)

There's already been a bug for this filed against Dapper through the Launchpad bug tracker.

---

### Post by Bart Schaefer on 2006-09-17
Oh, one last detail ... the optical mouse IS working in Dapper.

I had merely failed to unplug the mouse and plug it back in between booting Breezy and rebooting Dapper.

---

### Post by clsgis on 2008-03-05
This bug persists in 7.10.  Here's my version of it.

I installed a normal Ubuntu 7.10 on a PATA drive, works fine.  I can use PS/2 or USB mouse and keyboard.  I can even hotswap them.  I can use both keyboards at once!

Then I did the same exact installation on the same computer, except to an external USB drive.  Both keyboards works in console.  In X (both gdm and GNOME desktop) the PS/2 mouse and keyboard are ignored.

First I thought I screwed up the install to USB drive.  So I made a new ext3 FS there, and **copied** the PATA installation to it.  This is now **exactly** the same install, except for the UUIDs in [FONT="Courier New"]/etc/fstab[/FONT] and [FONT="Courier New"]/boot/grub/menu.lst[/FONT].  The only difference is the USB storage driver loads before the psmouse driver.

The kernel log shows an error predicting the failure:
```
Can't read CTR while initializing i8042
probe of i8042 failed with error -5
```
That doesn't happen in the success (PATA) case.

I tried adding [FONT="Courier New"]psmouse[/FONT] to [FONT="Courier New"]/etc/modules[/FONT], with no effect.  I finally *masked* the problem by **disabling** USB legacy device support in BIOS.  Others have reported they masked it by **enabling** legacy.  I believe this is a kernel USB support bug.  The location of the file system (on PATA or USB) should not affect whether USB mouse works.

---

