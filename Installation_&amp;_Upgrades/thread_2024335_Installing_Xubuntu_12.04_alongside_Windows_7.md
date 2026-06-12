---
title: "Installing Xubuntu 12.04 alongside Windows 7"
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by CrazyGuy158 on 2012-07-13
Hello. I currently run Windows 7 on my laptop with a 640gb harddrive and it currently got two partitions. A C:\ one 150GB for the W7 OS, games and programs and D:\ which is ~449GB for personal files.

I have run Ubuntu in the past and also other distros but I've kind of always reverted to Ubuntu as it always seems to work when other distros doesn't and it's got excellent support for my laptop. 

Why Xfce, you ask? Well, I don't really like Gnome 3 just yet and I don't like KDE. I also do not like LXDE that much. It looks okay and so but I like Xfce better. I also like openbox without any DE to it, so I might install that on Xubuntu later on.

What has kept me from running Ubuntu lately, though, is Unity. I hate it. I hate it so much I stopped using Ubuntu. I tried installing the Xfce desktop but there still were too much of Unity left. I then recently looked into installing Xubuntu, and that's what I'll do.

My partitioning scheme from previous experiences has always been like this:

/boot
/
/home
swap

Now, I'd probably be using Xubuntu a lot, but also Windows 7. What space for each Linux partition could you recommend? Oh, I read somewhere that having Grub installed in the Master Boot Record only allows 3 primary partitions and 1 extended, where you can have as many logicals as you please. If I install Grub in say /boot, will it allow more primaries or does it still only allow 3 plus 1 extended?

I don't want to drop Windows 7 nor do I want to reformat or shrink C:\ or install through Wubi. I'm planning on doing a LiveCD install.

----------

Laptop and specs:

Acer Aspire 5552G (one of the models)

2.3 GHz AMD Athlon II P360 CPU
4 GB DDR3 RAM
1 GB AMD Radeon HD 6650M GPU
640 GB toshiba sata HDD

---

### Post by CrazyGuy158 on 2012-07-13
I wouldn't exactly call myself "noob" with Linux, but maybe not Intermediate. I know my way around the console for basic stuff.

---

### Post by zwygart on 2012-07-13
The partitionning limit is not from Grub, it is from the partition table wich is a msdos table on nearly any computer except Apple, and may be some others. 

So installing boot in one or another place will not change anything. First Check if your D drive is on a primary partition or already on extended. 

Your partitioning scheme is good. So just go ahead. It should be possible to do it that way. 

Pay attention to where you put /boot. It should be as near of the beginning of the drive as possible since some BIOS can't read until the end. The boot partition must be in a reacheable zone of the drive. After the kernel loading and initramfs process the BIOS is no longer used and Linux and home folders may be anywhere.

---

