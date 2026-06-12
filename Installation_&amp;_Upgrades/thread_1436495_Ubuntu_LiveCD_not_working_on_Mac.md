---
title: "Ubuntu LiveCD not working on Mac"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by dherts on 2010-03-22
Hey all,

I've been trying to install Ubuntu because I'd really like to double-boot 10.6 with it. I've made several Ubuntu disks, all of which are recognized perfectly for installation in Virtualbox, but none of which are recognized as bootable by my machine. That is, I can use them to install Ubuntu into virtualbox (so I know the disk works) but my Macbook Pro simply won't recognize the disk as bootable.

Suggestions?

---

### Post by zvacet on 2010-03-23
See if  yo can fins something useful [here.]("http://ubuntuforums.org/showthread.php?t=1192296")

---

### Post by Mark Phelps on 2010-03-23
If you're looking at Ubuntu 10.04, I would strongly advise that you do NOT install it -- at least, not at this time.

It only just entered beta testing a few days ago and is still unstable as a result.

You would do better installing either 9.10 or waiting until the end of April and installing 10.04 after it is released.

---

### Post by zvacet on 2010-03-23
> I've been trying to install Ubuntu because I'd really like to double-boot 10.6 with it.

I think OP mean that he use Snow Leopard (OSX 10.6)and want to dual boot.

---

### Post by jaoc223 on 2010-03-23
Have you tried booting the alternate cd? I have an iMac 24" running snow leopard, when i was unable to boot from a live cd the alternate cd's worked for me. Just a suggestion. Hope it might help. Just be careful to install grub on /dev/sda3, sda3 works if you just have the +hfs partition for mac and a fat 32 partition for ubuntu. Also make sure you're using Refit. the lastest version is 0.14, Refit helps you boot into ubuntu, it will sync your partitions. After installing ubuntu restart and boot into mac osx, restart again and in Refit got to the partition tool and hit "y" to sync partitions, then shutdown the mac completely, boot it back up and select the penguin and you'll boot ubuntu.

Edit. Install Refit before you start your installation of ubuntu. I used bootcamp to create my fat32 then installed refit, then installed ubuntu.

---

### Post by jaggomiken on 2010-11-17
Hi everybody,
 I installed Ubuntu 10.04.1 LTS on my iMac 27'' Core i5.

1) I first installed REFIT from pre-installed Mac OS X.
1a) In MacOSX, resize the HFS+ partition with some of apple's disk utilities so that you make space for linux.

2) Then I used ubuntu-10.04.1-alternate-amd64.iso to make a text-only installation into an ext4 partition.
2a) I used "gnu parted" to delete the partitions created in 1a) for hosting linux and I re-created them with "gnu parted" to avoid messing up GPT with sfdisk or fdisk/cfdisk, that don't handle GPT tables.
2b) I told installer to install Ubuntu into the partition created with gparted (so I didn't use the partition editor builtin into the ubuntu installer). Wait some minutes for the installer to copy files and install packages.
3) Then I booted in and got the well known "blank screen" issue of Xorg after the "ubuntu" logo;
4) So a rebooted the system and selected the "failsafe/rescue" grub entry to boot ubuntu in rescue mode (text only);
5) I selected the failsafe X11 session and told the system to use "low graphic mode" only for this session;
6) The network was working, so I installed the fglrx driver for "proprietary hardware drivers"
7) I configured the /etc/default/grub file to append "readon.modeset=0  nomodeset" after each boot entry (but I'm not sure this setting is  really mandatory for Xorg to work correctly)
8) Then I rebooted and everything works good.

I'm sticking on make the keyboard and mouse work as expected (as in Mac OS X).
Hope this helps.

---

### Post by dislocated on 2012-01-06
> **jaoc223 said:**
> Have you tried booting the alternate cd? I have an iMac 24" running snow leopard, when i was unable to boot from a live cd the alternate cd's worked for me. Just a suggestion. Hope it might help. Just be careful to install grub on /dev/sda3, sda3 works if you just have the +hfs partition for mac and a fat 32 partition for ubuntu. Also make sure you're using Refit. the lastest version is 0.14, Refit helps you boot into ubuntu, it will sync your partitions. After installing ubuntu restart and boot into mac osx, restart again and in Refit got to the partition tool and hit "y" to sync partitions, then shutdown the mac completely, boot it back up and select the penguin and you'll boot ubuntu.

Edit. Install Refit before you start your installation of ubuntu. I used bootcamp to create my fat32 then installed refit, then installed ubuntu.

I am trying to install 11.10 along side snow leopard. Partitions are ready and I have refit installed and working. I have the alternate install cd but during the installation, I don't see an option to select the device for the boot loader (like in the graphic installation). Can someone tell me how to specify this with the alternate (text) installation?

---

