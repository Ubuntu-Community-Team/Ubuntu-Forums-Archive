---
title: "Edubuntu 10.10 LiveCD &quot;Checking Battery State"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by JackAndBlues on 2011-04-14
Hey guys,

I am having a hard time installing Edubuntu 10.10 on a Toshiba L30 and I am asking for help. First things first: 

System specifications: 
Toshiba L30-140
Intel Celeron M CPU 410 1,46 GHz
ATI Radeon XPress 200M Series
MATSHITA DVD-RAM UJ-841S
Bootable with CD/DVD only 


While installing Edubuntu, I encounter two problems:

**Can not mount...**

I will reach to the screen to select to install Edubuntu and it will even show the green leds. I push F1 to get more detailed messages. After 2 minutes or so I will have this error message: 

```

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initframfs) stdin: I/O error
mount: mounting /dev/loopa/0 on //filesystemsquashfs failed: No such device
Can not mount /dev/loop0 (/cdrom/casper/filesystemsquashfs) on //filesystem.squashfs

```I have already searched on Google and in this and a German Ubuntu-Forum, there seemed to be no real solution for it. (Or did I miss anything?) 

What's weird is, and it is also giving me some hope; this error appears randomly. Out of ten attempts to boot, 6 times I will get this error message. 4 times I will get to...

**Checking battery state ... [OK]**

This will advance up to "Checking battery state... [OK]" which will freeze there with no DVD or HDD-Activity visible. 

I encountered very many threads on the "checking battery state" issue, but they seemed obsolete to me, since most of them referred to Ibex. Also this is the Edubuntu LiveCD, it has not yet been installed on the HDD. 

Nonetheless, for the Checking Battery State problem I have tried solutions for Ibex such as "acpi=force pci=noacpi" and "acpi=off". But it wouldn't work. Some people also suggested changing the graphic configurations, this is ATI however, not Nvidia and the BIOS does not offer the option to change it. 

Strangely, the installation has worked brilliantly (with the same dvd) on another  computer (some Laptop Toshiba L30), so I don't believe it might be a  damaged disk. 

Would be glad if I could have help.

JackandBlues

---

### Post by JackAndBlues on 2011-04-25
This is due to a broken DVD-Drive. The topic has changed, so I created a new Thread for this.

---

