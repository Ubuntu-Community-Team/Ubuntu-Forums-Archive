---
title: "Should Fedora or Ubuntu be installed first for dual boot?"
date: 2017-03-23
forum: Installation &amp; Upgrades
---

### Post by Music_Guy on 2017-03-23
I am currently running Ubuntu 16.04 (BIOS boot). I want to set up my  computer for EFI booting, dual booting into Ubuntu and Fedora. Any  thoughts on which OS I should install first? Also, since I have never  dual booted before, will the computer name be that of the first install,  or will it depend on which OS is running?

---

### Post by TheFu on 2017-03-23
Use different computer names for each install.

Don't think it matters which you install first, but I'd want to setup the partitioning for both PRIOR to either install. Would probably want a shared swap partition for both/all, if dual/triple/quad/.... booting.

---

### Post by Dennis N on 2017-03-23
In UEFI mode, I would install Ubuntu first, then Fedora, so that you get Fedora's boot menu when you start the computer. Fedora menu can boot Ubuntu, but from Ubuntu menu you cannot boot Fedora, unless you make a custom menu entry for it that corrects the problem. What happens is you end up in "emergency mode". 

The name of the computer will be what you specify at install for each OS, so depends on which OS is running. You can change the name after installation if desired.  

Note: If you used BIOS mode you can install either OS first without a problem.

In my opinion, UEFI is the better option. I would go with it.

---

### Post by oldfred on 2017-03-23
Fedora default install uses LVM, not standard partitions.
Some that multiple boot suggest choosing to install using standard partitions not the LVM. One advantage of LVM is only when it is the entire hard drive.

But, you can boot Fedora with LVM from Ubuntu's grub in standard partition but have to add LVM drivers and mount the LVM before running sudo update-grub in Ubuntu.

You can always directly boot either system from UEFI. BIOS/MBR systems only boot the one install's boot loader in the MBR. With UEFI all systems install boot loaders in the ESP - efi system partition and UEFI is also a boot manager or menu where you can choose system to boot. Grub is both a boot manager and boot loader.

Do not use /boot with Ubuntu. I believe LVM typically has a separate /boot outside LVM. 
And UEFI still requires the ESP - efi system partition, normally first partition on gpt partitioned drive.

---

### Post by Music_Guy on 2017-03-23
Thank you @Dennis and @oldfred. I was planning to use the LVM Fedora install; however, based on oldfred's comment, I did not research it enough. Since Ubuntu will be my primary install and Fedora is just for playing around, I'll go with the non-LVM install.  :)

---

### Post by Dennis N on 2017-03-23
> **Music_Guy said:**
> Thank you @Dennis and @oldfred. I was planning to use the LVM Fedora install; however, based on oldfred's comment, I did not research it enough. Since Ubuntu will be my primary install and Fedora is just for playing around, I'll go with the non-LVM install.  :)

Good choice. Let us know how it goes. 

I started experimenting with Fedora with Fedora 22. Not that easy to set up as I wanted. Then read about Korora, and when Fedora 22 expired and Fedora 23 was released, I used Korora 23 instead. Much nicer and easier to use out of the box. Now have Korora 25. 

The thing with lvm is that you need to learn the commands to handle it. I have 3 working lvm installs right now (all Ubuntu family distros). Here is a good guide specifically written for Ubuntu:

[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by Music_Guy on 2017-03-23
Thanks again Dennis, for the advice. I'm really interested in LVM, but I  don't want to spend the time now to learn it. I did look at the guide -  it seems to be pretty comprehensive. I'll have to study it before I  jump in. For now, just to begin to learn Fedora, I'm going to proceed as  I planned. I also checked out Korora. Again, I'll have to study it  more. I have no problem installing other distros, so I can certainly  overwrite Fedora if it is too much of a hassle. If I do, Korora will be  my next choice. And by the next time I do an install, I'll have a better  understanding of LVM, and will likely take that route.

---

