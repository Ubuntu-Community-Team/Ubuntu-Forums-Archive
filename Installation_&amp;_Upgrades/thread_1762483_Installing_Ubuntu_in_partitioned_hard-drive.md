---
title: "Installing Ubuntu in partitioned hard-drive?"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by Mccfuzz on 2011-05-19
Hi there

At present I have a hard drive with three primary partitions and one extended (logically split).
I'm runnining win 2k pro in each primary partition.
I'm about to reformat the middle primary partition and would like to take this opportunity of trying Ubuntu using the middle primary partition.
I'm using GAG to switch from one partition to another.

Is there any reason why trying Ubuntu in the middle partition would cause problems.
I think I read that Ubuntu can mess up the MBR.
Thaks in advance for your advice!!

McFuzz

---

### Post by coffeecat on 2011-05-19
Hi, and welcome to the forum.

First question: do you have any Linux experience? The reason I ask is that it is usual to have a dedicated swap partition for Linux and I wondered if you had considered this in your partition layout.

There's no reason why installing Ubuntu to your "middle" partition would cause any problems because Linux doesn't care whether it's on a primary or logical partition - it can boot from either. Unlike a certain other proprietary operating system we won't mention. :)

Ubuntu doesn't mess up the mbr - it installs grub to the mbr which is the boot-loader which comes with most Linux distros and which can boot Windows as well. But if you have your own bootloader on the mbr and wish to keep it, I suppose it would look as though grub has messed it up!

A quick explanation of where grub goes. Some code is installed to the mbr (the first 440 bytes or so) and also some code in the embedding area. This is the part of the hard drive between the partition table and the first sector of the first partition. The remaining grub code responsible for booting, together with the main configuration file, is to be found in the /boot/grub folder of the Ubuntu root partition. I have no experience of GAG but, reading their webpage, it looks as though it uses the embedding area as well. Both grub and GAG are far too complex to fit into the mbr - the Windows mbr code is relatively simple.

If you don't want to use grub and want to keep GAG, when you get to the partitioning stage of the Ubuntu installer, you need to choose the "Manual/Advanced" option in version 10.10 and before. You get a chance to stipulate where grub is installed. I can't remember whether or not you can opt out of installing it at all. In the latest 11.04 release of Ubuntu, the manual option has been renamed to something else. Iirc, it is literally "Something Else".

I have a suggestion. Do you have a live CD? Boot up with the live CD and choose "try Ubuntu" which will take you to the live desktop. Open a terminal and post the output of:

```
sudo fdisk -lu
```This will give us details of your partition layout and we will be able to advise better. In particular it will be easier to see what your middle partition is, how big it is and whether there are likely to be any problems. You can find the terminal under Applications > Accessories in the classic gnome desktop (panels top and bottom) or in the Unity desktop, press the Windows/Super key and start typing "terminal" in the search bar - you'll soon see an icon to click.

---

