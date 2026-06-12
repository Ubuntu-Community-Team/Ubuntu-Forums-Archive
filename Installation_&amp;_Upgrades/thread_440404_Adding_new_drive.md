---
title: "Adding new drive"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by myname on 2007-05-11
Just read though a few of the hard drive upgrade posts, and I'm a little confused.  I've been using Ubuntu since September, and am now upgrading/adding a larger harddrive.

My current system is Edgy on a 80GB drive.  here is what I would like to do:

1)  install a new 320 gig drive, format it.
2)  Move my data (mp3, images, etc., or just my ~/ directory if easier), and email to this new drive
3)  do a fresh install of Feisty on the 80 gig drive
4)  keep my ~/ directory on my 320 gig drive, but have feisty see the ~/ on the 320 and not the 80

Is there also a way to get my installed apps (/usr/bin I think) moved to the 320 and retain that?

Any help/suggestions?  I know how to do this in Windows, but want to know/learn how to do it in linux.

--Kevin

---

### Post by sup on 2007-05-12
Hi, that should be fairly easy. 
4) during install, do not let the install program partition your harddrive, do it manually. set your new 320 disk (should be recoginzed) to be mounted as /home and let the old 80 be / (and do not forget to create a swap partition on 80 - and if you want to dualboot, you will need at least 10-15GB of a ntfs partition in the beginnning of 80 drive
other then that, just plug your new drive in and copy all the files - do not forget to format it before that though, the best is probably ext3, even though you can use about any filesystem you please as long as it is supported by Ubuntu.

---

### Post by jtnoob on 2007-05-12
I have a 160 gb sata drive. I would like to partion it manually, but when I do it won't boot. I would like to have 15gb for the OS, 1gb swap, and the rest for storage. I am unfamiliar with the drive extensions for linux (e.g. /boot, /dev, etc.). How shouldI set this up?

thanks

---

### Post by bulldog on 2007-05-12
> **jtnoob said:**
> I have a 160 gb sata drive. I would like to partion it manually, but when I do it won't boot. I would like to have 15gb for the OS, 1gb swap, and the rest for storage. I am unfamiliar with the drive extensions for linux (e.g. /boot, /dev, etc.). How shouldI set this up?

thanks

Download and burn the gparted live cd ISO and boot from it.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Make the partitions as you want them,15GB for /,1GB swap and maybe a /home and a /data partition.
Set them to format as ext3 except the swap,format swap as swap.
Apply and wait till the process is finished.
Exit gparted and boot ubuntu install cd.

Mount your created partitions as they should,set them to format again,and proceed with the install.

[An empty hdd won't boot,only when an OS is installed it can boot]

---

### Post by myname on 2007-05-12
> **sup said:**
> Hi, that should be fairly easy. 
4) during install, do not let the install program partition your harddrive, do it manually. set your new 320 disk (should be recoginzed) to be mounted as /home and let the old 80 be / (and do not forget to create a swap partition on 80 - and if you want to dualboot, you will need at least 10-15GB of a ntfs partition in the beginnning of 80 drive
other then that, just plug your new drive in and copy all the files - do not forget to format it before that though, the best is probably ext3, even though you can use about any filesystem you please as long as it is supported by Ubuntu.

Just to be sure I won't lose any data, I want to clarify this is what I will do:

1)  install new 320 gig drive
2)  format it as ext3, or whatever
3)  copy ~/ to it
4)  boot linux CD and install, do not let linux partition
5)  set /home to be on 320 gig
6)  set / to be on 80 gig
7)  install

When I boot after the install, I should see all the files I copied on ~/ which is on my 320 gig, correct?

--Kevin

---

### Post by jtnoob on 2007-05-12
Thanks for the help. I had gone through the entire install process. Does "error 15" mean there is no OS?

---

### Post by bulldog on 2007-05-12
Here you can find what error 15 means.

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

---

### Post by sup on 2007-05-13
> **myname said:**
> Just to be sure I won't lose any data, I want to clarify this is what I will do:

1)  install new 320 gig drive
2)  format it as ext3, or whatever
3)  copy ~/ to it
4)  boot linux CD and install, do not let linux partition
5)  set /home to be on 320 gig
6)  set / to be on 80 gig
7)  install

When I boot after the install, I should see all the files I copied on ~/ which is on my 320 gig, correct?

--Kevin
Yeah, I think you got it right. At least, when you copy the files to 320 drive, the data wont get loss in any case.

---

### Post by myname on 2007-05-14
That's what I thought, I just wanted to be sure that Ubuntu is not going to format/mark the 320 drive as /home during the installation process.  That would make my backup go buh-bye.

---

