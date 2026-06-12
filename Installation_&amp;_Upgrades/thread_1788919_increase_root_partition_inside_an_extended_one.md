---
title: "increase root partition inside an extended one"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by mangoes on 2011-06-23
Hello,
I don't have enough space in the root partition to upgrade. I have the home,root and swap partition (in that order) inside an extended partition. 
Here is fdisk -l:
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3891    31254426    7  HPFS/NTFS
/dev/sda2            3892        4864     7815622+  83  Linux
/dev/sda3            4865       38913   273498592+   5  Extended
/dev/sda5            4865       36960   257811088+  83  Linux
/dev/sda6           36961       38662    13671283+  83  Linux
/dev/sda7           38663       38913     2016126   82  Linux swap / Solaris

Don't worry about sda1 (windows) and sda2 .
The home, root and swap partition are the sda5,6,7 respectively.
Is it possible to annex some space from the home partition without destroying the data there?

Thanks a lot

---

### Post by dino99 on 2011-06-23
you can resize partition if they are not mounted ( boot on a livecd); root need at least 10 Gb

but you can make room using bleachbit or simply: clean/autoclean/autoremove

---

### Post by mangoes on 2011-06-26
> **dino99 said:**
> you can resize partition if they are not mounted ( boot on a livecd); root need at least 10 Gb

but you can make room using bleachbit or simply: clean/autoclean/autoremove

Thanks Dino.  I have 12 gb in root but it does not seem to be enough for latest releases these days.

---

### Post by Quackers on 2011-06-26
12GB is more than enough on my installations. Do you have a lot of things installed? I can't get any of my root partitions past 6GB :-)

---

### Post by varunendra on 2011-06-26
> **Quackers said:**
> 12GB is more than enough on my installations. Do you have a lot of things installed? I can't get any of my root partitions past 6GB :-)
Same with me.
And that when I've installed tons of 'heavy' applications (multiple audio/video/graphics/animation tools, crossover, visual effects - almost everything compiz related, all essential apps, multiple emulators/virtualization tools like VBox, VMware, antivirus (for win of course), ..... too many to mention - multiple ones for the same job - just for testing) along with all default apps. In fact, a remastersys backup ended up only being 2.93 GB in size when I was expecting it to exceed 4.5GB!

You should use Disk Usage Analyzer to determine whether there are unnecessary files in your root drive (run it as super-user).

---

