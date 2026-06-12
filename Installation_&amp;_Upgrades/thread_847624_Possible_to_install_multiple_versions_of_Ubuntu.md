---
title: "Possible to install multiple versions of Ubuntu?"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by brianafischer on 2008-07-02
I would like to beta test Ubuntu 8.10 Ibex on my laptop.  I am currently dual booting Ubuntu Hardy 8.04 and Windows Vista.  I would like to triple boot with the option to select Hardy/Ibex/Vista.  Is this possible?

---

### Post by scragar on 2008-07-02
yes, I was tripple booting hardy(pre release), gutsy(which was stable at the time) and windows XP(which hasn't been used in almost 4 months, not even for gaming actualy, gotta love wine) without any problems, grub will add your current ubuntu partition as an alternate OS.


I am unsure how things will turn out with a kernel update though, since the update will proberly edit grub and switch grub back to the current usage(instead of the new one), so that might cause you to lose Ibex till you add it back to the grub listings. Kernel updates are normaly pretty rare as far as updates go though, so I don't think that's even much of a concern.

---

### Post by Pumalite on 2008-07-02
It is possible. You need space. If you have Ubuntu inside an extended partitions; you would have to shrink one of those partitions to allocate space for Intrepid Ivex. You can do this with Gparted Live CD. You have to backup everything before you start.

---

### Post by brianafischer on 2008-07-02
I have a spare 35GB on my NTFS partition that I can shrink.  I would like to minimize the disk space usage by the alpha release, so I will create a dedicated 10GB ext3 root partition for Ibex.

A few more things:
I would like to share the linux-swap partition.
I would like to share the /home/ folders.  However, I am thinking that this may cause some compatability issues with newer Ibex software overwriting preferences for Hardy.

Any comments?

---

### Post by Pumalite on 2008-07-02
The /swap partition is fine. Better have separate /home. Make sure you respect the rule of 4 primaries per drive. Inside of an extended partition, you can have as many logicals as you want.

---

### Post by louieb on 2008-07-02
Things to think about. 

Creating a new partition can be hard or easy depending on the current partition layout.
 As Pumalite points out partition layout and type has rules. Post your partition table and I can tell if its going to be easy, hard or somewhere inbetween. 
```
 sudo fdisk -l
```Kernel updates and GRUB.
After you have set up the partition and are installing the 2nd Linux in it,  It may ask you where to install GRUB or you may have to hunt for how to change the install location. Instead of installing to the MBR,  i**nstall GRUB to the boot sector of the 2nd Linux partition**. 

Then it just a matter of adding a **chainloader or configfile **entry in the Ubuntu GRUB menu. Doing it this way keeps kernel updates for each distro separate. Works well.

---

