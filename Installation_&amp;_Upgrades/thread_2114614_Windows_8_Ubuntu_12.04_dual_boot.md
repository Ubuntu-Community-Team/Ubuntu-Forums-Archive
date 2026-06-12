---
title: "Windows 8 Ubuntu 12.04 dual boot"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by kathrync on 2013-02-10
Hey,

I am trying to install Ubuntu 12.04 to dual boot with Windows 8 on a friend's laptop.

I don't seem to have had any problems with partitioning the disc or getting Ubuntu on to it (as in, if I load live-Ubuntu and look at the disc I can see all the files) but I can't seem to make it boot.  At the moment, it just goes straight into Win 8 without giving me any option for Ubuntu.  I can't find an option for Ubuntu in the BIOS either.

I have turned off the secure-boot option and the fast-boot option, and I have run boot-repair twice but to no avail.

This is the URL from the last pass with boot-repair [http://paste.ubuntu.com/1634100/](http://paste.ubuntu.com/1634100/)

There was an error (given in full at the bottom of the URL) which says "Locked ESP detected".  It is asking me to create a boot/efi partition, but as far as I know there already is one.

Any help appreciated!

---

### Post by darkod on 2013-02-10
ESP is short for the EFI System Partition. If that message Locked ESP means anything, it might have blocked grub-efi to install onto it. As you can see at the top of the bootinfo results, there is no ubuntu folder on sda2, the ESP.

Also, there are some files saying crypt on the ESP, which might mean encryption of a kind.

Make sure to read the specification and manual very carefully, so that you know what the machine actually has configured.

I don't work with UEFI so I can't help much.

---

### Post by kathrync on 2013-02-10
Just to add;

I also tried the solution described here [http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)

However the described file was not present anywhere...this is possibly the problem, but I don't know how to solve it!

---

### Post by kathrync on 2013-02-10
> **darkod said:**
> ESP is short for the EFI System Partition. If that message Locked ESP means anything, it might have blocked grub-efi to install onto it. As you can see at the top of the bootinfo results, there is no ubuntu folder on sda2, the ESP.

Also, there are some files saying crypt on the ESP, which might mean encryption of a kind.



That makes sense.  Unfortunately, I don't know enough about UEFI or Windows 8 (I didn't have these problems with my own UEFI Win7 dual-boot system) to sort it out.  Hopefully someone else will be along soon!  Thanks anyway :-)

---

### Post by oldfred on 2013-02-10
there are several others with locked ESPs.

grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.

[http://ubuntuforums.org/showthread.php?t=2100349&page=3](http://ubuntuforums.org/showthread.php?t=2100349&page=3)

Please create login to launchpad and add your issue to the bug report.

---

### Post by kathrync on 2013-02-11
> **oldfred said:**
> 

Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.



Thanks!

Just to clarify, do you mean backup, reformat and restore the EFI parition, or something else?

---

### Post by oldfred on 2013-02-11
Just the efi partition. Not sure how large it really is. Some vendors have some of the recovery boot efi files in the efi partition and others have those files in other partitions. Not sure what all is in the Windows but partition is not large so it should be easy to totally backup which is a good idea anyway.

Then totally delete the efi partition. Then create a new fat32 partition  with the boot flag which with gpt makes it the efi partition.

       In GPT fdisk or gdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

---

### Post by kathrync on 2013-02-13
Thanks, that makes sense.  

Now I just have to wait for my friend to finish her coursework so I can give it a go!  I'll let you know how it goes :-)

---

### Post by kathrync on 2013-02-24
Cheers guys, that worked :-)

Now having another problem with it though.  I upgraded the kernel and the grub entry for Linux didn't update.  

This is quite easy to fix by running boot-repair after an upgrade, however my friend is new to Linux and I am trying to keep it as clean for her as I can.  Is there any way I can prevent this happening next time there is a kernel upgrade?

Edited because my text smileys with round noses don't work on forums that use graphical smileys!

---

### Post by oldfred on 2013-02-24
It is supposed to automatically update. If it did not then that is bug. 

Some also are having issues where a update does not incorporate the nVidia drive, but those have the grub entry but video does not work.

---

### Post by kathrync on 2013-02-26
Well, we got it up and running again.  I still don't know what caused the problem with grub not recognising the kernel upgrade, but it seems to be ok now.

Thanks all!

---

