---
title: "Dual Boot @ Linux"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by rogeliodelarosa97 on 2010-07-05
Hello i have 1 quick question am i able to triple boot opensuse, mandriva, and ubuntu i already got ubuntu and wanted to know how to triple boot them please be as specific and descriptive as possible since i am a newbie

---

### Post by cj.surrusco on 2010-07-05
Check out this thread if you want a detailed explanation. 

[http://ubuntuforums.org/showthread.php?t=254400](http://ubuntuforums.org/showthread.php?t=254400)

---

### Post by wilee-nilee on 2010-07-05
> **cj.surrusco said:**
> Check out this thread if you want a detailed explanation. 

[http://ubuntuforums.org/showthread.php?t=254400](http://ubuntuforums.org/showthread.php?t=254400)

That is a link from 2006 and has no reference to grub2, it is a moot thread.

Thread starter you claim to have all 3 booting your description is confusing what is it that you have working? and what do you want?

---

### Post by rogeliodelarosa97 on 2010-07-05
I have Ubutnu desktop 10.4 and want mandriva 2010 one and openSUSE 11.2

---

### Post by cj.surrusco on 2010-07-05
> **rogeliodelarosa97 said:**
> I have Ubutnu desktop 10.4 and want mandriva 2010 one and openSUSE 11.2

First you need to partition the hard drive for the new distros. That would mean possibly shrinking Ubuntu's partition and creating two new ext4 partitions for the second and third distros.

Install both of the new OS's on the new partitions and choose not to install the bootloader during install. Then you can boot back into Ubuntu and update grub using:
```
sudo update-grub
```
That will add the new OS's to Grub and allow you to boot all of them.

Let me know if you need further detail.

---

### Post by rogeliodelarosa97 on 2010-07-06
Hello may you explain how to partition step by step using ubuntu live cd it would really help please be specific

---

### Post by confused57 on 2010-07-06
Herman's instructions here should help you:
[http://ubuntuforums.org/showthread.php?t=1462617](http://ubuntuforums.org/showthread.php?t=1462617)

---

### Post by rogeliodelarosa97 on 2010-07-06
hello i have finally partitioned using a gparted live cd and now once i boot up i get a message saying 

mount: mounting /dev/disk/by-uuid/2c2e7ba2-5c4448fa-b1a3-77a0f576907 on root
failed: invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /crop on /root/crop failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init=botarg

please help!!!!!!!!!!!!!!!!!!! me i am a newbie so be descriptive

---

