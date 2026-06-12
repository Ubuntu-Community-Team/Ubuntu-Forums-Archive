---
title: "How do I format a hard drive with 19.04 already On It?"
date: 2019-09-23
forum: Installation &amp; Upgrades
---

### Post by pipercub45 on 2019-09-23
I want to reinstall 19.04 on a hard drive that already has 19.04 on it.  How do I format the drive so I can start over?  Thanks

---

### Post by GhX6GZMB on 2019-09-23
Just do a reinstali from DVD/USB .iso image. Your drive will be formatted during the install process.

---

### Post by Dennis N on 2019-09-23
If it's living with Windows on the same disk, and you want to keep Windows, use the something else option when choosing installation type. Then select the root partition for Ubuntu, click change, and fill in details: use as ext4 journaling filesystem and mount point of partition set as /. Leave grub install location as it is.

---

### Post by yancek on 2019-09-24
You can format it during the installation process or you can use GParted which is on the Ubuntu installation media to format the partition before beginning the install.  If 19.04 is the only OS on the machine this should be a simple task.  It will of course, overwrite any data on the partition.  If you have another OS make certain you get the correct partition.

---

### Post by pipercub45 on 2019-09-24
Thanks for the replies!

I have other problems.  The computer is not recognizing the DVD player in BIOS.  Once I get that sorted out loading 19.04 will probably work just fine.

---

### Post by pipercub45 on 2019-09-28
I lied (not on purpose).  I have a hard drive which had 19.04 on it and still might.  I can't access it.  And another hard drive with 18.04 on it installed which will load.  If I run the DVD with 19.04 on it there are 10 choices listed and a .tex and read
me file.  I tried some of them but nothing started an installation file.  I also have a flash drive on the computer with "balena-etcher-electron-1.5.45-linux-x64.zip" and "system volume information".  I'm lost.

---

### Post by pipercub45 on 2019-09-29
I'm lost

---

### Post by yancek on 2019-09-30
If you are able to boot 18.04, do that and open a terminal.  From the terminal run the commands below and post the output here if you still want help.

> sudo fdisk -l
sudo parted -l

This will give us more detailed information to assist you.
How did you put 19.04 on the usb?  If you boot the usb, you should not see what you report.  If you look at it from another Linux OS (Ubuntu 18.04) you will see directories and files but you will not be able to boot or install that way.  Did you install the current version of Ubuntu yourself?

The 'belena-etcher' file you mention is software to be unzipped and used to create a bootable system on a usb.  Did you download that to one of the Ubuntu installs?  Did you use that to create the bootable 19.04 usb?

---

### Post by pipercub45 on 2019-10-06
I used something called "rufus" and had the "iso" file 19.04.  I followed instructions and all is well.

---

