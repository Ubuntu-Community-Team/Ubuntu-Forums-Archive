---
title: "How to install Ubuntu Only on ASUS Laptop F554L (UEFI, EFI)"
date: 2015-10-14
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2015-10-14
Hello :-)

It took me about a day and a half and more installations and experimentation than I want to count.

The task : **Delete Windows 8 and Install Ubuntu by itself, with customized partitions**.

It all comes down to the partitions you create in order to be compatible with UEFI, so that the BIOS will be able to find the proper boot partitions, otherwise the laptop does not even boot.

I had to make a LIVE CD to do all the installations.  USB stick, didn't work after the first time.  It exited with "Kernel panic".

The relevant to the booting ability are the first 2 partitions  with mount points "**/boot/efi**" and "**/boot**".  They were created by the option "Delete Disk and Install Ubuntu ...".

However I could not create the other partitions with that option.  So I had to reinstall by "copying" the first two partitions when I chose the option to create my own partitions during installation.

I have attached the picture of the Gparted Partition Configuration.

Good luck to anyone who tries.

Many thanks to the community for all their support.

**Edit :  **

One small addition.  After the installation any partition that you make that is not /home will belong to root.  In my example the partition that was mounted under "/home/evan/Data" belonged to root and I couldn't access it,unless I used "sudo nautilus", but even then my programs could not write on that partition.

So what you have to do is change the owner of any partition that you want to be able to have access to with :
"sudo chown -R username:username mountposition.

In my case it was :
sudo chown -R evan:evan /home/evan/Data

---

