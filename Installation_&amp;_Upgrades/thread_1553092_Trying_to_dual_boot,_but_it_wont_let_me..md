---
title: "Trying to dual boot, but it wont let me."
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by cloudpersona on 2010-08-14
When I went to install ubuntu 10.04 I resized my main windows 7 partition, giving me free space, but now it says that space is unusable. How am I supposed to install ubuntu without wiping the entire drive?

---

### Post by wilee-nilee on 2010-08-14
> **cloudpersona said:**
> When I went to install ubuntu 10.04 I resized my main windows 7 partition, giving me free space, but now it says that space is unusable. How am I supposed to install ubuntu without wiping the entire drive?

Take a screen shot of gparted from the Live Ubuntu cd and post it.

---

### Post by cloudpersona on 2010-08-14
here it is

---

### Post by oldfred on 2010-08-14
You have used all 4 primary partitions. You can only have 4 primary or convert one primary to an extended that can hold many logical partitions. Ubuntu will work fine in logical but you will have to delete one of your existing partitions. It looks like your sda1 is windows boot, sda2 is windows. Do you then have a recovery and a vendor system partition and what do they do? If not important backup and delete one or the other. If you have not made recovery CD/DVDs from your system you must do that before removing any partitions.

---

### Post by cloudpersona on 2010-08-14
> **oldfred said:**
> You have used all 4 primary partitions. You can only have 4 primary or convert one primary to an extended that can hold many logical partitions. Ubuntu will work fine in logical but you will have to delete one of your existing partitions. It looks like your sda1 is windows boot, sda2 is windows. Do you then have a recovery and a vendor system partition and what do they do? If not important backup and delete one or the other. If you have not made recovery CD/DVDs from your system you must do that before removing any partitions.

There is a recovery partition, on my hdd. So if I delete the recovery partition I'll be able to install ubuntu?

---

### Post by Cavsfan on 2010-08-14
**oldfred** will get you fixed up and then after you are able to dual boot, you might want to take a look at the tutorial
in my signature. I dual boot Windows 7 and Ubuntu 10.04 and have a nice custom GRUB2 background and a 
maintenance free boot menu. You will never have to modify GRUB2 when a new kernel is installed.

---

### Post by oldfred on 2010-08-14
If you delete one primary then you can recreate that partition as the entire free space and add logical partitions for Ubuntu, swap, /home & shared depending on space you have and sizes you want to use.

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

---

