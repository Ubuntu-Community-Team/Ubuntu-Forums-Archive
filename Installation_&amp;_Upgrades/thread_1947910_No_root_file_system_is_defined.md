---
title: "No root file system is defined"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by ctlayon on 2012-03-27
So I'm trying to install a fresh copy of Ubuntu 11.10 on my computer after open Indiana. I've created a live usb that loads the installer for Ubuntu. I select my language, click next until it brings me to the partition window in which it shows /dev/sda in the bottom left corner of the screen but the whole screen is disabled except the bottom row of buttons (aka install). So I click install now and it says 
"No root file system is defined. Please correct this from the partitioning menu."
I can't use the installers partitioning menu as it is currently disabled so I quit the installer and load the live CD. Once inside the live CD I open a terminal window and type fdisk -l which shows /dev/sda (main sata hard drive) and /dev/sdb (live usb). I then ran sudo gparted and created the following (see attachment).

I'm confused as to what the issue is and I'm beginning to think my hard drive is for some reason not compatible with Ubuntu or maybe their is some really weird bios setting preventing it from working properly?

---

### Post by QIII on 2012-03-27
Unlike some direct Unix descendents like openIndiana (open source grand child of Solaris), /boot is rarely needed in Linux.

I would clear the entire table (if you are planning to wipe everything anyway) and create / as a boot point, /home and a swap partition.  Keep it simple unless you have some specialized needs.

---

### Post by ctlayon on 2012-03-27
Thanks I've tried just doing a / and a swap but I still run into the same problems it doesn't seem to see the partitions on the drive via the installer yet it somehow sees it in both fdisk and gparted

[EDIT]
I've tried "create / as a boot point, /home and a swap partition"

---

### Post by ctlayon on 2012-03-27
I ran the following command: ```
sudo mkfs.ext2 /dev/sda
``` notice that its the whole drive not /dev/sda1. Then I ran the installer and it worked. I'm guessing there was some sort of weird non overwrite thing on the hard drive that gparted couldn't get around. I noticed this while it was writing the changes it went through the formatting really quickly and thought oh maybe this. Thanks for the help.

---

### Post by darkod on 2012-03-27
This problem is usually when you have used the disk in raid before. That leaves raid meta data remains which windows ignores but ubuntu doesn't. In this case it doesn't display the partitions preventing you possibly to install over a raid array.

If you ARE NOT running raid, boot into live mode, open terminal and try:
sudo dmraid -E -r /dev/sda

If that asks you to remove meta data, confirm and start the install again. It should work fine.

---

### Post by darkod on 2012-03-27
> **ctlayon said:**
> I ran the following command: ```
sudo mkfs.ext2 /dev/sda
``` notice that its the whole drive not /dev/sda1. Then I ran the installer and it worked. I'm guessing there was some sort of weird non overwrite thing on the hard drive that gparted couldn't get around. I noticed this while it was writing the changes it went through the formatting really quickly and thought oh maybe this. Thanks for the help.

Are you sure it works? I have never seen formatting with a filesystem on the whole device, not only on a partition.

See how it goes and let us know because this should definitely not work.

---

### Post by ctlayon on 2012-03-27
> **darkod said:**
> Are you sure it works? I have never seen formatting with a filesystem on the whole device, not only on a partition.

See how it goes and let us know because this should definitely not work.

Yeah that's what fixed it, I didn't get to try the way you suggested all though I'm sure it would have worked too. Just to be clear after the installer recognized /dev/sda as a valid device I let it automaically erase the whole thing and partition it.

---

### Post by darkod on 2012-03-27
> **ctlayon said:**
>  Just to be clear after the installer recognized /dev/sda as a valid device I let it automaically erase the whole thing and partition it.

OK, that can work. :)

---

### Post by saidii89 on 2012-05-15
all users around the world are facing such problem and the solution to it is pretty simple
 
make sure that the partition file system [you wish to install linux, ubunto or backrack on it] is ext4, ext3 or ext2 [not fat32 or ntfs]
 
then mount "/" on it, how? easy: 
1- on the installation process press [change] on the partition you wish to use
 
2- make sure [do not use this partition] scroll is not chosen, scroll to ext4, ext3 or ext2
 
3- and on "mount" field write "/"
 
4- when clicking ok then next a message will appear saying something like [swap area was not defined, do you wish to continue or choose a swap area? because bla bla bla..], click "ok" and continue or click "go back" and choose another partition and click change, on the file system scroll choose [swap] and click ok and next
 
this will solve both "no root file system is defined" and the "swap area" message, if you still get the swap area message then on step 4 mount "/swap" to the partition
 
**AND THIS SOLVES IT!**
every time anyone need solutions to silly problems like this then you know who to ask!
 
ask me anything [and I really mean it] by accessing any of my profiles or my blog, and if I can help I will do it :) ->
 [http://www.twitter.com/saidii89](http://www.twitter.com/saidii89)
 [http://www.facebook.com/saidii89](http://www.facebook.com/saidii89)
 [http://www.formsrping.me/saidii89](http://www.formsrping.me/saidii89)
 [http://www.saidi-theory.blogspot.com]("http://www.saidi-theory.blogspot.com/")
 
brought to you by Sa'eed Awad
[Saidi Theory Solutions] by Sa'eed Awad

---

