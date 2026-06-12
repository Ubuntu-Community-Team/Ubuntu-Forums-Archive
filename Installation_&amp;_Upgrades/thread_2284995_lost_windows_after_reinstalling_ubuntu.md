---
title: "lost windows after reinstalling ubuntu"
date: 2015-07-02
forum: Installation &amp; Upgrades
---

### Post by BENHIBA_AYOUB on 2015-07-02
Hey , i've a problem i had a dual-boot windows 8.1 and ubuntu 16 . and lately i had a problem with ubuntu because after i installed my second graphic card nvidia , it tell ubuntu is running in low graphic mode i tried all kind of solutions on net but no result so i decided to reinstall ubuntu again , after i did i believe that i done it on UEFI mode and without specifying a swap partition . now ubuntu works fine and the problem now that it boot to ubuntu like if windows isn't installed ( i've many partition and the windows partition isn't touched i can access my files via ubuntu ) . i tried boot-repair on live-usb but it didn't solve the problem i also tried to repair windows using the windows CD but in vain it tells that the windows partition is locked .

---

### Post by grahammechanical on 2015-07-02
A few points.

You have Ubuntu 16? The last Ubuntu version was Ubuntu 15.04. The next Ubuntu version will be Ubuntu 15.10.

When we install Ubuntu and tick the box Install Third Party Software we get proprietary video and audio codecs and also a proprietary video driver. If we then change video adapters it is possible that Ubuntu will be using the wrong video driver for the new adapter and low graphic mode is what happens. It is best to use the Additional Drivers tab to switch to the open source video driver before changing video adapters.

If we already have a swap partition and we reinstall or install another version of Ubuntu to a different partition the installer program will use the existing swap partition.

If the machine comes with Windows 8.1 pre-installed then Windows will be installed in EFI mode and that means Ubuntu must be installed in EFI mode otherwise we will be able to load Ubuntu but not Windows or Windows but not Ubuntu. Are you sure that Ubuntu was installed in EFI mode?

When we run Boot Repair it will produce a boot report and store it online and give a URL to link to the location of the boot repair report. If we post that URL on this forum the members here can see for themselves the situation and try to figure out what is wrong. If you made a note of that URL post it here. If not, run Boot Repair again and get that URL for us.

Boot Repair will offer a recommended repair but it will not do any repairs unless we agree to the repairs. One reason that Boot Repair fails to solve the problem is because we have not accepted the recommended repair option.

Regards.

---

### Post by oldfred on 2015-07-02
How did you reinstall?
If you used an auto install option?

 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by BENHIBA_AYOUB on 2015-07-02
well , all i did is that i formated the old ubuntu partition and i installed the new ubuntu on it (UEFI mode ) , the windows partition is still existing . and my computer had windows 8 pre-installed on it .

---

### Post by BENHIBA_AYOUB on 2015-07-02
Problem solved thx guys for trying to help , all i did to solve it is to reinstall again ubuntu but this time i changed the sata settings from bios from IDE to AHCI and after installing ubuntu i choosed IDE again now ubuntu and windows works fine and i didn't need to run boot-repair

---

