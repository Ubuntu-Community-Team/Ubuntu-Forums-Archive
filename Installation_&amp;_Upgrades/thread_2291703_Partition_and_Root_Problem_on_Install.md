---
title: "Partition and Root Problem on Install"
date: 2015-08-22
forum: Installation &amp; Upgrades
---

### Post by WeeJocky on 2015-08-22
Hi All,

As an absolute new user of Linux I didn't know whether to ask on this one or the New to Ubuntu, so apologies if I chose wrong.

I have attempted to install Ubuntu in a dual boot environment with Windows 7.

Whenever I start Ubuntu, I get the message "Failed to partitin as Superuser as likely too many partitions in the partition table".

If I click OK, I then get a message which says "No root File (as Superuser) please correct from partitioning menu."

I have managed to run the Demo, and all I can say is that it looks vastly different to that of the "proper" installation so far.

Can anyone help please ---- but please bear in mind I am a long in the tooth "windows user" and somewhat (VERY) un-technical on Linux.

Thanks,

Ian

---

### Post by v3.xx on 2015-08-22
Is this a possibility?

[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics#Primary_Partition_Rules_and_Conventions](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics#Primary_Partition_Rules_and_Conventions)

---

### Post by WeeJocky on 2015-08-22
Hi v3.xx,
Thanks for such a quick response, and for an interesting article. Is this a possibility ----- Haven't got a clue!!!

I did say I was new to Linux ----- approx. 6 Hours new at the time of writing this, and nearly 30 years in windows, so do please forgive my ignorance of what I am doing and where I am going.

All I can tell you is that it was a brand new drive, (Toshiba 500Gb) and I created two roughly equal partitions (C:\ drive for Windows and D:\ drive for Linux. Both "Quick Formatted" by Windows prior to a clean install. The clean install was done prior to attempting the installation of Ubuntu.

My laptop goes through the motions and correctly offers a dual boot, but upon choosing Ubuntu, (ignoring the error messages) I end up with a reddish screen with a few wee icons in the top right of the screen, mainly to do with available WiFi, but nothing like the screen display I got when I ran the demo.

Does it require Internet access on booting, as I have not yet bothered to configure those settings.

Regards,

Ian

---

### Post by yancek on 2015-08-22
You can't format a partition to be used by Linux in windows as a default windows installation is incapable of doing that and is incapable of writing to or reading a Linux filesystem.   You need to select to format the Ubuntu partition during the install.  You also need to select a partition for the installation (root of the filesystem) which is symbolized by "/".
 
When you installed windows, how many partitions do you have for it?

The link below has a lot of useful information on Linux drive/partition naming conventions and also a detailed tutorial on installing Ubuntu in dual-boot.  I would suggesting reading through it before trying again. 


[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by WeeJocky on 2015-08-22
Hi yancek

Many thanks for this link. Pity there are no obvious pointers to it at the time of downloading the ISO.

Still, it appears there are "bits" which either weren't made available to me during the installation, or I disregarded them.
I also remember I partitioned and formatted the drive prior to commencing my clean install.

I am now off to start it all again, and shall come back and report on the success or failure of the second "go" accordingly.

Thanks again,,

Ian

---

### Post by dino99 on 2015-08-22
Before starting any installation, a good idea is to do some preparations, mainly about cleaning/shrinking/degramenting if necessary: so boot win7 and do what you think is needed.
What you have not said is: how win7 have been installed, efi/gpt ? or normal old bios ? beause you need to select the same options for installing an other OS (search & read the 'oldfred' posts/threads about 'installing ubuntu alongside windows7)

Then remember that with 'bios' there is a 4 primary partitions limit (uefi bypass it), and windows wants to be the first in the place.
So when the windows installation have been cleaned/shrinked/...  set the free space as an 'extended partition' where you then can install ubuntu.
Also note that formatting is always done on unmounted partition. So boot the utility 'gparted live' from sourceforge (put it on usb stick) and prepare the ubuntu partitions:

you need 3 partitions:
- / (which is root) as ext4 format, and about 15 to 20 Gb
- swap, about 4 Gb
- /home as ext4 format to store your settings & data (as large as possible)
note how gparted have identify them: something like /dev/sdx, you will then pick them when the installer will ask you where to install (its the 'manual' choice, named 'something else' option)

Now you are ready to boot the ubuntu iso, and follow the installer to start the installation. It will ask you again later, where to install the boot loader (grub), and you will select /dev/sdx, x = the / address.

---

### Post by yancek on 2015-08-22
> Many thanks for this link. Pity there are no obvious pointers to it at the time of downloading the ISO.


That would be because the person who wrote the tutorial has no connection with Canonical or Ubuntu.  There are tutorials at the Ubuntu site but the ones I've seen are simpler.

Creating a partition from windows before starting should work, formatting the partition from windows isn't possible.

---

