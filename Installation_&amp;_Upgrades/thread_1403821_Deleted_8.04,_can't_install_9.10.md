---
title: "Deleted 8.04, can't install 9.10"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by Nicholas482109 on 2010-02-10
I wanted to upgrade my 8.04 install on my 500gb external to 9.10. I was having issues with it after I tried booting up the system on a different computer than I usually do so I decide to just format it and install 9.10. I put it on a 12gb partition but I get Error 15 when I try to boot. What am I doing different from when I installed 8.04 and how do I partition swap space on the drive?

---

### Post by johnson.d on 2010-02-12
The issue seems to be at the grub level

The following link may help you regarding grub in Ubuntu 9.10

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

For adding a swap partition you will need to boot into the system.
After booting you can install gparted utility by using the following command:

> $ sudo apt-get install gparted

Then you can run this utilty from Gnome menu -> Administration -> Gparted

Now you can create a swap partition by using the folowing procedure

1) Right click on the unallocated space and click new

2) Enter the details in the window according to your requirement and click add (Drop down and select file system to swap)

3) Goto Edit -> Apply Changes

Now the new swap partition will be created

Now it can be enabled by using the following command:

> $ swapon /dev/sdax

Where x is the partition number according to Ubuntu

---

### Post by mikewhatever on 2010-02-12
What do you mean by 'I put it on a 12gb partition'? Did you manage to install 9.10 or not?

---

### Post by recluce on 2010-02-12
You don't give us enough information to work with. GRUB error 15 "File not found" usually means that GRUB is looking for the linux kernel in the wrong place.

---

