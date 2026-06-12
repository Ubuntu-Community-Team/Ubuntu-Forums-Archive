---
title: "Fresh install over unbootable install"
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by cartesian on 2011-09-20
I successfully got my laptop dual booting windows vista and ubuntu.  After 'tinkering' things I now can't boot into the ubuntu partition.  I've tried to fix it but to no avail.

There is nothing that needs saving on the linux part so I thought I would do a fresh install.

I need to know will the installer let me choose the partition to install on?  Presumably it can see the correctly formatted partition.  Will it see the grub menu I have now or will it overwrite it?  Should I let it write a new one anyway?

Basic questions I know, but I don't want to trash the windows partition!

Thanks.

---

### Post by drs305 on 2011-09-20
You will be asked how you want to install Ubuntu. At that point, select 'Do something else' or manual partititoning (the bottom option). You will be able to review the current partitions and should:

Select current Ubuntu partition. 
Next choose the mountpoint (/) and 
Tick to enable formatting of that partition.

Grub will overwrite what is on the drive's MBR (the default, do not install to a partition but let it install to the drive). 

When the installation if finished, Grub should have found Windows and included it in the menu. If not, run "sudo update-grub".

As you are installing, if you have questions and can get online, please ask for help here rather than guess.  ;-)

---

### Post by Quackers on 2011-09-20
Yes, but it depends on which Ubuntu you are installing as to the method.
If you are using Ubuntu 10.04 or 10.10 you should select the manual partitioning option in the installer.
If you are installing 11.04 you need to choose "something else".
You can then choose which partition to use. Be sure you are using the correct one, as everything will be over-written.

---

### Post by An Sanct on 2011-09-20
> **cartesian said:**
> I need to know will the installer let me choose the partition to install on?  Presumably it can see the correctly formatted partition.

The installer lets you choose via 'wizard' mode, to install "next to" another OS (windows) or in 'expert' mode, to choose the exact partition. Both with the possibility to format the selected partiotion clean again. If swap exists, it will not re-create ie. do another one.

> **cartesian said:**
> Will it see the grub menu I have now or will it overwrite it?  Should I let it write a new one anyway?
It will overwrite the old grub and replace it with a new one, according to the version you want to install. This procedure will recreate all the "new" boot options - including the present Windows.

> **cartesian said:**
>  Basic questions I know, but I don't want to trash the windows partition!

There should be no problems if you use an official release. Do not use an alpha/beta version! If you want to get Oneiric to your machine, install Natty and dist-upgrade it to Oneiric, this is currently much safer - noone will guarantee for a beta.

PS. its always good to hear multiple answers, before proceeding ;)

---

### Post by cartesian on 2011-09-22
Thanks for the posts guys.

Please keep an eye on this thread if you don't mind.  I'm not sure when I'll get to the install but it will be soon.

Thanks again.

---

### Post by cartesian on 2011-09-22
OK

I've run through the installer and selected manual to choose the partition where to install. it lists the following:

dev/sda
/dev/sda1   fat3   /media/sda1
/dev/sda2   ntfs   /media/sda2
/dev/sda3   ext3   /media/sda3
free space
/dev/sda5   ntfs   /media/sda5

I presume that the 2 ntfs partitions are my Windows ones, the C drive and the separate D Data drive; they are roughly the same size as the windows partitions, so I should choose the ext3 one?

When I choose the ext3 partition it asks me to specify a mount point. Is /media/sda3 not the mount point?

Also it asks me to specify a swap partition, how do I do that?

Thanks for your help.

---

### Post by drs305 on 2011-09-22
> **cartesian said:**
> 

When I choose the ext3 partition it asks me to specify a mount point. Is /media/sda3 not the mount point?

Also it asks me to specify a swap partition, how do I do that?

Thanks for your help.

The mountpoint is /  It should be one of the options in the dropdown box.

Swap is going to have to be an extended partition, but it's going to have to be in the extended partition. If the installer lets you, you can just click on the unallocated space and try to make that swap, and then resize it correctly after the installation. Eventually you will probably only want it to be 1-2GB.

---

### Post by cartesian on 2011-09-23
drs305,
great, i've got a nice clean install and a swap partition in the free space.  I've booted into both linux and windows successfully.

I've realised it is quite an old version of ubuntu, 7.x.x, can i upgrade to a newer version within the ubuntu version I have or do I have to get a new iso image and install/upgrade that way?

Thanks.

---

### Post by drs305 on 2011-09-23
That is too old a version to upgrade. Your best options are probably to install 10.04 Lucid, which is the long term version, or 11.04 Natty, which is the current version. The advantage to these is the ability to update to do an online upgrade to the next version: Lucid to the next LTS version next year, or from 11.04 to 11.10 Oneiric later this year.

There is a big change between the way Lucid does things and the way Natty and future versions look. Lucid would be good if you want stability, Natty if you don't want to learn two 'new' ways of doing things. Just my opinion.
 The one issue we didn't deal with was how large your swap partition ended up being. Now that you have Ubuntu running, you can shrink it with an app called gparted if necessary. Depending on how much RAM you have, 1-2GB is usually fine. Assuming it's in the extended partition, if you end up with additional space you can create another partition for data, storage, etc.

---

### Post by cartesian on 2011-09-24
The swap partition is 1GB and I have GB RAM installed.

Just installed 10.04 and everything seems OK.  I've booted into both partitions, Windows and Ubuntu.

I just need to edit the grub menu and I'm done.

Thanks again.

---

