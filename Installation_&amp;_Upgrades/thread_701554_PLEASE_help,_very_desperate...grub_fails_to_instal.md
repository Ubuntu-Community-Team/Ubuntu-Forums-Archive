---
title: "PLEASE help, very desperate...grub fails to install!"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by CUrza on 2008-02-19
Ok, here's the basics: I am a complete noob. I created two partitions, named C and D, for running Windows XP and Ubuntu. I installed and updated Windows as an NTFS system on C this morning. Then, I went to Ubuntu and used the partition editor to resize D into 20GB and 5GB swap space (just a guess, I read I only needed 2GB swap but I dunno...moving on). So, I go to install Ubuntu. I click "Manual" on the partitions screen. I choose my 2nd partition, the one called D. I make it a ext3 partition, and in the mount point form I type "/" just like it says. I then edit the 5GB partition to be swap space, and click next. I choose not to import my info from XP. I look at Advanced, and the box to install the boot loader is checked, and the place to install is listed as hd0. At 94%, the error "Executing 'grub-install' (hd0) failed. This is a fatal error." Then I tried to reinstall on hd1, thinking maybe that would do something different, but no. I know there is a thread on this but I am very new and I do not understand any of this. Could someone please help? Also it says my HD is a SCSI3, if that helps...thanks in advance

---

### Post by santaslittlehelper on 2008-02-19
Hi

This happen to me once I really don't remember how come. I am not really helping much. :)
It should be pretty straightforward.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

This might not be a real solution but something to try and should work no matter the setup, you could create a /boot partition it's pretty straightforward too.

You can prepare you're partitions from the livecd if you want to. From a terminal type "gksudo gparted".

/dev/sda1  windows
/dev/sda2  extended partition
/dev/sda4  /boot 100 MB
/dev/sda5  / 10 GB
/dev/sda6  swap 1 GB \I just keep to 1 GB no matter what but you can read up on it if you want.
/dev/sda7  /home \what ever amount.

Choose Manuel when you come to prepare disk space and set it up accordingly to the way you did the partitions.

---

