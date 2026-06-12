---
title: "Installation Questions"
date: 2012-12-16
forum: Installation &amp; Upgrades
---

### Post by Mike Green9 on 2012-12-16
Windows 7 with 1gb RAM

Hi.

I am installing Ubuntu 12 onto a 20gb ext3 partition. I have 100gb free disk space.

The install asked me to choose a swap space. Do I have to allocate another partition for the swap space, and if so, what size should it be?

I installed without allocating a swap space. Can I allocate a swap space after the install?

The install asked me for a mount point. I chose /. Is this okay?

I also want to ensure that GRUB2 will be installed within the UBUNTU partition. Is there an option for this on the install? (I will use EasyBCD to select Windows7 or UBUNTU.)

Thanks for your help,

M...

---

### Post by Ghiro82 on 2012-12-16
Hi!
I don't understand your problems. How have you formatted the partition? 
It must be in FAT or FAT32. I installed ubuntu a lot of time and I don't remember that the install asked a mount point. 
If you install Ubuntu and Windows in one hard disk,the dual boot should be automatic.

---

### Post by Pjotr123 on 2012-12-16
No need at all for FAT or FAT32. Do it like this:
[https://sites.google.com/site/easylinuxtipsproject/installation](https://sites.google.com/site/easylinuxtipsproject/installation)
Easy as can be. :)

If you prefer manual installation (but why?): the Ubuntu partition needs the mount point / . Formatted in EXT4, not in EXT3. And a separate swap partition, which should be a at least a little larger than the size of your RAM.

I advise to let the installer simply put Grub into the MBR. Grub is a very cool and versatile tool, ideal to boot every operating system in existence. :)

---

### Post by Bucky Ball on 2012-12-16
*Thread moved to **Installation & Upgrades***

---

### Post by ajgreeny on 2012-12-16
> **Ghiro82 said:**
> Hi!
I don't understand your problems. How have you formatted the partition? 
It must be in FAT or FAT32. I installed ubuntu a lot of time and I don't remember that the install asked a mount point. 
If you install Ubuntu and Windows in one hard disk,the dual boot should be automatic.
Sorry, but you have this completely wrong.

The linux partition must be formatted to a linux filesystem such as ext4, the default for Ubuntu.  You can not install Linux on a fat32 partition; if you try you will either be unsuccessful, or if you use the default settings, the installer will simply format the partition to ext4 automatically.

If you choose to manually set partitions for the installation by choosing "Something Else" at disk preparation stage you will have to choose / as the mountpoint for the root partition.  If you don't the installtion will not proceed further, or you will get errors when you try to boot Ubuntu saying no root partition could be found.

@OP
You will find a lot of useful information in many community help pages of the ubuntu wiki [https://help.ubuntu.com/community](https://help.ubuntu.com/community) and also at [Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php"), the latter of which I find very useful.

---

### Post by Ghiro82 on 2012-12-16
I'm really sorry for my mistakes. Thank you for the info. I'll give a look :)

---

### Post by Mike Green9 on 2012-12-19
Thanks for your help. I reran the install and carefully read each screen. I found out where to specify the swap partition.

Ubuntu 12.1 is up and running. It's much better than my previous attempt of Ubuntu 9.


M...

---

### Post by Bucky Ball on 2012-12-20
> **Mike Green9 said:**
> Thanks for your help. I reran the install and carefully read each screen. I found out where to specify the swap partition.

Ubuntu 12.1 is up and running. It's much better than my previous attempt of Ubuntu 9.


M...

If you consider this solved, please mark it so to help others from 'Thread Tools' at top right of this page. ;)

Other issues? Post a new thread with descriptive thread title ...

---

