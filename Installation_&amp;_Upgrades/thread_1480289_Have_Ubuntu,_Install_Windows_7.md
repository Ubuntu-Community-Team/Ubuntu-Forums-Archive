---
title: "Have Ubuntu, Install Windows 7"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by jdmBlue on 2010-05-11
I would like to dual boot Ubuntu and Windows 7.

I have Ubuntu 9.10 Live CD and Windows 7 Pro Live CD. Ubuntu is installed but Windows 7 isn`t. I have gparted installed.

I found the following directions within Ubuntu documentation.

**Master Boot Record backup and re-replacement**

 Back-up the existing MBR, install Windows, replace your backup overwriting the Windows boot code: 

[LIST=1]
[*]Create an NTFS partition for windows (using fdisk, GPartEd or whatever tool you are familiar with)
[*]Backup the MBR e.g. dd if=/dev/sda of=/mbr.bin bs=446 count=1
[*]Install windows
[*]Boot into a [LiveCD]("https://help.ubuntu.com/community/LiveCD")
[*]Mount your root partition in the LiveCD
[*]Restore the MBR e.g. dd if=/media/sda/mbr.bin of=/dev/sda bs=446 count=1
[*]Restart and Ubuntu will boot
[*]Setup grub to boot windows
[/LIST]
I don`t want to backup the MBR and restore as listed. I would rather use the Ubuntu Live CD to reinstall the GRUB.

My question is how do I overwrite the MBR? 

Do I use gparted and change the partition?
Do I create an NTFS partition as listed above? 
Or what do I need to otherwise do to boot the Windows 7 Live CD so that it will install?

I don`t have much experience with Ubuntu.

---

### Post by Arla on 2010-05-11
My advice, by careful!

I installed windows, and it wiped out my ubuntu data drive while it installed (thanks M$). Fortunately I had just copied my data off, so could just replace it.

Personally, if I was in your situation, I'd probably backup my data, install Windows (manually partitioning whatever space I wanted to use for windows) then install Ubuntu again and partition where I wanted it. Then restore all my data to wherever it was going to go.

---

### Post by jdmBlue on 2010-05-11
> **Arla said:**
> My advice, by careful!

I installed windows, and it wiped out my ubuntu data drive while it installed (thanks M$). Fortunately I had just copied my data off, so could just replace it.

Personally, if I was in your situation, I'd probably backup my data, install Windows (manually partitioning whatever space I wanted to use for windows) then install Ubuntu again and partition where I wanted it. Then restore all my data to wherever it was going to go.


How do I manually partion the space ? With GParted do I create a NTFS partition that Windows will know to write when the LiveCD is booted in the harddrive? What size should the partition be?

What do I do with the partition that has Ubuntu?

---

### Post by Arla on 2010-05-11
IF (and it's a big if) you are happy to reinstall everything.

The answers kind of depend on your needs, personally I've got a 320GB drive, have it split into 40GB for Windows (if I recall you can tell windows how much space to use when you install it) 20GB for each Ubuntu install (I have two, you probably only need one) 15GB for video capture (I need a partition specifically for that, but I do video stuff) 2GB for Swap space, and then the rest is my /home folder (for my main Ubuntu install, for my test Ubuntu install I have home in the same partition as the root).

However, that said, I use Ubuntu for 90% of what I do, and use windows to play a few games, and for video editing, your needs may differ depending on what you use each OS for.

---

### Post by darkod on 2010-05-11
> **jdmBlue said:**
> How do I manually partion the space ? With GParted do I create a NTFS partition that Windows will know to write when the LiveCD is booted in the harddrive? What size should the partition be?

What do I do with the partition that has Ubuntu?

You are right, just reinstalling grub2 from the 9.10 cd it much better.

Creating ntfs partition with Gparted is also good idea, I have done that even on a new PC with no OS. Then you boot with the win7 dvd and the installer will ask where to install and list the partitions. Just select the one you prepared. One note, I don't think windows can be on logical partition, it has to be a primary.

The size of the win7 partition depends what you plan installing. For win7 only, dedicate at least 25GB, if you plan to use any large sized software, take that into account.

When the installation finishes the computer will boot straight into win7. Look around if it's working fine, then boot with the 9.10 and restore grub2. If you need help with that just ask.

Once in ubuntu you will have to run

sudo update-grub

so it can locate win7 and add it to the menu (at first ubuntu boot you will not see option for win7, it's perfectly normal because it was installed after ubuntu).

---

### Post by Arla on 2010-05-11
> **darkod said:**
> You are right, just reinstalling grub2 from the 9.10 cd it much better.

If windows doesn't screw with your partitions, sure..

As I said, I recently did this, planning to do just that, and windows 7 removed my ext4 partition that had my /home on it!

So be warned...

---

### Post by darkod on 2010-05-11
> **Arla said:**
> If windows doesn't screw with your partitions, sure..

As I said, I recently did this, planning to do just that, and windows 7 removed my ext4 partition that had my /home on it!

So be warned...

If you have a prepared partition you only have to point it to it. No need even to start the partition manager, or handle partitions with the win7 installer in any way. I don't know what you did, but it sounds like you pointed it to the wrong partition.

Anyway, we are discussing grub2 reinstallation here. If the root partition gets messed up, having a MBR backup won't help much anyway, right?

Mistakes happen but if you paint a too dark picture you can sometimes make someone with less experience and already nervous enough even more panicked.

Of course handling partitions should be done with care, nevermind which tool you use. And installing a new OS is not always for everyone too (I don't mean you of course). :) If someone starts with that, I consider them warned from the start. :)

---

