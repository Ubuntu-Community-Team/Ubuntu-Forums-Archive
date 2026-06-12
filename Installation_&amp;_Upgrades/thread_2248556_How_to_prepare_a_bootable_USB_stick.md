---
title: "How to prepare a bootable USB stick?"
date: 2014-10-15
forum: Installation &amp; Upgrades
---

### Post by drechsel on 2014-10-15
Hi, 

I tried an awful lot to boot from USB sticks. I used tuxboot, ubuntu startup creator, unetbootin, multibootusb and some other beasts. Initially, that works, machine boots from the stick.

At some time, when had to switch to another iso , I formatted the stick with gparted before - and after installing the new one I could no longer boot. At booting, I can select the stick in my BIOS'es boot menu and are left alone with just a blinking prompt.

The machine boots from a USB HDD - and before it used to boot from two different USB sticks, but now that no longer works.

I used the msdos partition table and fat16, set the boot flag in gparted.

So here comes the question:
How do I properly prepare a USB stick to make it bootable before installing the *.iso onto it?

Or can it be true that a stick can be ruined with formatting or so?

Cheers,
Wolf

---

### Post by yancek on 2014-10-15
The flash drive could be bad, everything fails at some point.  With some of these installers, it is recommended that you use FAT32.  I've never used Fat16 so I'm not sure if that matters.  Do you have another machine on which you can try to boot it to eliminate that as a problem?

---

### Post by Vladlenin5000 on 2014-10-15
Yes, FAT16 matters. You need FAT32.
Besides, each and every tool you already used can format the stick using the proper file system for the job. You don't need GParted for that.

---

### Post by drechsel on 2014-10-16
Hm.
I found some hits which say that dealing with a error message I had

```
Error: No configuration fie found - No Default or UI configuration directive found
```

could be resolved by using vat16 instead of vat32. Indeed, that worked at another machine - but not on the machine in question.

Nevertheless - the tools I mentioned should do all the preparation work properly?
What about things like superfloppy, mbr etc ?

Wolf

---

### Post by sudodus on 2014-10-16
Try a method that is independent of the previous content of the pendrive, including the partition table and file system - ***mkusb*** uses ***dd*** and copies/flashes/clones the content of the iso file to the pendrive (seen as a device). It is very reliable but does not offer persistence. And of course it needs a healthy pendrive. If the hardware is damaged, I think no tool can be expected to work. Pendrives have a limited lifetime (number of write operations to each flash cell), more so than other mass storage devices.

See this link [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by frank75 on 2014-10-16
I use gparted and delete all partitions on the USB stick. Then I create a msdos partition table and after that I format fat32. I use UNetbootin to put the .iso onto the USB stick and since I have my laptops set to boot to the hard drive I have to hit f12 at the splash screen to get a boot menu. I pick USB and boot to it and Bob's your mom's brother.

---

### Post by Vladlenin5000 on 2014-10-16
I never heard of a problem that required special formating. Missing files errors often have to do with a corrupt ISO and/or damaged or failing pendrives.
Have you check the integrity of the ISO you're using? A corrupt ISO will give errors no matter what tool or file system you use...

---

### Post by drechsel on 2014-10-17
Hi everybody,
thanks a lot for your thoughts.

To be honest: I gave in, burned a CD and was happy within minutes.
I guess, the damm bios of my Fujitsu-Siemens is so buggy, that you can do whatever you want - and will be ever frustrated.

Nevertheless, I'll give a try to mkusb occasionally.

Live is too short to waste it on buggy beasts... (-;

Cheers,
Wolf

---

