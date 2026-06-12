---
title: "Confused,dual booting &amp; Boot Loader?"
date: 2015-04-14
forum: Installation &amp; Upgrades
---

### Post by steve36plenty on 2015-04-14
Hi Everyone,

I hope someone can get me some help with this: I have installed Ubuntu-Mate on a

 500GB Hard Drive, /dev/sda
Partition /dev/sda1
file System ext4 + Mount Point /

I also have a 149GB Unallocated Hard Drive:
/dev/sdb

I would like to install Kubuntu on this Hard Drive, But I am very confused about where to mount this, & where to install the boot loader?? 
Please can I have some help with this.

Thank you Steve Plenty.

---

### Post by dino99 on 2015-04-14
when a user install a new distro, the system is clever enough to do the necessary stuff for you; so nothing to mount yourself (cool :p )
the boot loader has to be set where it have already been done: /dev/sda

you can use the existing swap partition and /home for the new installation. Simply choose 'something else' installer choice when you see it. You also can create the new partition with gparted before starting the installation, for easier propose

---

### Post by steve36plenty on 2015-04-14
Great thank you for your help with this one.! Your the best!

---

### Post by grahammechanical on 2015-04-14
There is something to keep in mind.

The Grub boot loader on sdb will know about Ubuntu Mate on sda because during the process of installing the boot loader Ubuntu Mate will be detected. Also the Installer will default to installing Grub on to sda. So, if sda has the boot priority you will be able to load either Ubuntu Mate (on sda) or Kubuntu (on sdb).

But if you change boot priority to sdb then you will not necessarily get a boot menu.

If you change the Grub location of Kubuntu to sdb then if sda has the boot priority you will not be able to load Kubuntu because the Grub on sda does not know about Kubuntu on sdb. So, you can use the BIOS to switch boot priority to sdb and load into Ubuntu Mate and run this command

[sudo]update-grub[/code]

Some of us prefer when using more than one hard disk and having a different version of Linux on each disk to give each disk its own boot loader. This is my preference.

Regards.

---

### Post by oldfred on 2015-04-14
I also like to take advantage of each drive's MBR and have each installs boot loader on the same drive as the install. Also a bit more reliable as each drive can boot without the other drive.
The older install can find newer on with:
sudo update-grub

I also prefer smaller / (root) partitions of 25GB and either separate /home (newer users) or if multi-booting separate data partition(s). Then you can mount & link your same data into all installs. Then you can also move Firefox & Thunderbird profiles to shared data partition and have same bookmarks & email in all systems.

---

