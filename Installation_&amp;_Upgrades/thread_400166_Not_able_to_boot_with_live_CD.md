---
title: "Not able to boot with live CD"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by Jou Moer on 2007-04-03
I have a wee bit of a problem.  I have a Dell Latitude D620 with Windows XP.  I want to make it dual boot with Kubuntu 6.10.  However, when I boot up with the CD, I get the splash with the options for language keyboard, VGA etc.  I then select the required options and the select the top option to proceed.  Up to this stage all goes well, everything is as expected.

Then, when the live cd is supposed to do it's magic and I have the KDE Desktop with the install icon, it does not happen.

Instead I only get a black screen with the following:

> Last Login: Tue Apr 3 13:18:39 2007 on tty5
Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UCT 2006 i686

The programs included with the Ubuntu system are free software:
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$

The live cd is a working one and I had this laptop as a working dual boot machine with Ubuntu.

Why it went wrong; I had some problems with XP and seeing as it is a work laptop, I restored the image using Ghost, thus I'm back to a "vanilla" XP machine with only the one partition.

---

### Post by taurus on 2007-04-03
What happens if you run this command from that prompt?

```
startx
```

---

### Post by Jou Moer on 2007-04-03
Hi Taurus,  I have just tried "startx" and it is quite interesting to see the error message.  The last few entries reads as:
> (WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE)I810(0): No Video BIOS modes for chosedn depth.
(EE) Screen(s) found, but none have a usuable configuration.

Fatal Server error:
no screens found
X10: fatal IO error 104 (connection reset by peer) on X server "0.0"
       after 0 requests (0 known processed) with 0 events remaining.
ubuntu@ubuntu:~$

In a way it makes sense, as when I selected the vga options for the screen, I selected the largest as 1024x768 and this is not correct as this laptop is one of those widescreen machines so the options should be something like 1280x800 or 1024x640 or something like that, but it does not list any wide screen type of display resolutions.

The graphics used by this machine is the Intel chipset.

This machine has the latest BIOS version and I think I'll reset the BIOS to default settings, but change the boot order to boot from CD first.

This is bizarre as the first time I made this machine dualboot with Ubuntu I did not have this issues.  The only difference is that I want to move from Gnome to KDE and the fact that I wiped the whole HDD via a restore using Ghost.

Any further advice greatly appreciated as I don't know what to do next.

---

### Post by taurus on 2007-04-03
Try to reconfigure your resolution again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, try starting X again with

```
start
```

---

### Post by Jou Moer on 2007-04-03
Unfortunately nothing happens.  I reset the machine's BIOS to the default, then tried again, but still get to my original problem screen as listed in the first post.  On the display option it still showed normal resolutions instead if widescreen resolutions but this time I selected the VGA option.

When Entering "sudo dpkg-reconfigure -phigh xserver-xorg" the following appears: 
> xserver-xorg postinst warning: not updating /etc/X11/X; file has been customised
xserver-xorgposting warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20070403162447

I then entered "sudo start" but then I only get the "ububntu@ubuntu:~$" prompt and nothing happens.

Could it be that Kubuntu does not support widescreen displays?

Any more advice appreciated.

PS.  Dunno if it will work but I'll try to connect a normal flat screen monitor later to see if it will work.

---

