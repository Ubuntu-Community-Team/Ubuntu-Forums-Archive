---
title: "Need driver for graphics card, will not install without driver"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by yonni on 2008-02-15
Right, I have a samsung R20 laptop and I want to install linux on one of the partitions. I am completely new to linux, but an experienced computer user.

Looking it up on google found [this page]("http://www.linlap.com/wiki/Samsung+R20") which indicates that it should be an easy ride installing linux. However, when I insert my live CD, it brings up all kinds of error messages that seem to relate to the display, searches on the subject confirm this. And the end result is a command line mess where you can't even shut it down properly.

The page linked above also says that I need the radeonHD driver (for my ATI Radeon 1250m) included in most distributions, and points me to where I can obtain this. Well, what I ask is: 1) Is the radeonHD driver included with ubuntu (or more specifically, the Kubuntu live CD, Gutsy Gibbon)
2) If so, why will it not let me run off the live CD?
3) If not, how am I supposed to install a driver when I can't even install the OS?

Your help is much appreciated. I must warn you I'm going to bed now (I'm in the GMT time zone), and therefore wont reply till morning (my time).

---

### Post by stevejesus on 2008-02-15
You should try installing from the Ubuntu alternate CD first.
This will let you install without having to use your graphics card.  Then, once you have that installed, you should worry about installing the driver.  It is not on the CD.

---

### Post by mrsteveman1 on 2008-02-15
I'm curious what the errors say, is it dropping you into single user mode? IE just a command prompt? It should boot into a semi-usable state even with a graphics card that you don't have a driver for, because it should be using VESA modes which every card supports.

Like someone else mentioned, you should probably grab the alternate CD and install it that way for now if nothing else works.

As an aside, the ubuntu cds have all had an option to load 3rd party drivers at boot time, so I'm kinda curious why it never gets used, this seems like a perfect situation for it. Perhaps if this turns out to be a real issue that would be a temporary solution. I'm gonna see what is required to use that feature.

In the meantime post the errors you are seeing if you can.

---

### Post by yonni on 2008-02-16
When trying to boot from the live CD, I hit "Start or Install Kubuntu", and then after a while, I get left with this on the screen:

```
[   364.773920] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   365.278413] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   365.278460] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
Loading, please wait...
Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the 
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ <flashing cursor>
```

When I type "sudo shutdown now", it attempts to shut down, gives me more errors that are more cryptic and then sticks me at another command prompt where the keys are assigned wrongly (including backspace, delete and arrowkeys just typing various characters). At this point I give up and hold the power button until it turns off.

---

### Post by mrsteveman1 on 2008-02-16
When the CD boots, press F6 to edit the boot line and add one of these to the end:

```

NOIOAPIC
NOLAPIC
NOAPIC

```

Try them one at a time and see if anything changes.

---

