---
title: "Dual Boot Vista External HD"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by shaffan33 on 2008-04-29
So I want to try out Ubuntu for the first time.  I've been reading into it a good amount and came to the conclusion that a dual boot would be the best option.  However, I do not have enough free space so I was going to buy an external hard drive.  I am running Vista on my laptop now, so I was wondering if anyone could help me get this installed.  I am not looking for a huge hard drive, just something cheap.  All help is greatly appreciated! Thanks!

---

### Post by martrn on 2008-04-29
> **shaffan33 said:**
> So I want to try out Ubuntu for the first time.  I've been reading into it a good amount and came to the conclusion that a dual boot would be the best option.  However, I do not have enough free space so I was going to buy an external hard drive.  I am running Vista on my laptop now, so I was wondering if anyone could help me get this installed.  I am not looking for a huge hard drive, just something cheap.  All help is greatly appreciated! Thanks!

Hi,

If you are installing ubuntu to an external hard-drive which I presume would be a removable hard drive how are you going to boot it ?  I have know of a similar problem once where someone installed ubuntu to an hard drive and when grub was placed on the Master boot record, they couldn't boot into windows or ubuntu without the external drive.

Anyways I suppose you could partition your internal hard drive with a small boot partition and dual boot windows / linux but make sure you either make a boot partition or don't install grub.

If you are buying an external hard drive, any will do and would reccomend if you can just do it and give ubuntu a go.

---

### Post by acelin on 2008-04-29
> **shaffan33 said:**
> So I want to try out Ubuntu for the first time.  I've been reading into it a good amount and came to the conclusion that a dual boot would be the best option.  However, I do not have enough free space so I was going to buy an external hard drive.  I am running Vista on my laptop now, so I was wondering if anyone could help me get this installed.  I am not looking for a huge hard drive, just something cheap.  All help is greatly appreciated! Thanks!

DUDE dont mix it! Mixing NTFS and /or fat 32 with a Ubuntu installation will eventually screw up the windows partition. Make sure it is 100% Ubuntu, or it will mess up. My Western Digital hard drive died like this, just because Windows did something funky to it. I could never format the Windows partition with any program, but the Ubuntu installation worked fine. All you have to do is install Ubuntu to the external ( make sure the external is plugged in as you boot) and when you get to partitioning, make sure to make the home computer's HD's as not used. At the last step is the most important part- setting the boot manager, grub, to be on the external and not the main computer, otherwise you wont be able to boot Vista. YOu have to set the master boot record to the external. Search and you will find how to do this around here.

---

### Post by shaffan33 on 2008-04-30
> **martrn said:**
> Hi,

If you are installing ubuntu to an external hard-drive which I presume would be a removable hard drive how are you going to boot it ?  I have know of a similar problem once where someone installed ubuntu to an hard drive and when grub was placed on the Master boot record, they couldn't boot into windows or ubuntu without the external drive.

Anyways I suppose you could partition your internal hard drive with a small boot partition and dual boot windows / linux but make sure you either make a boot partition or don't install grub.

If you are buying an external hard drive, any will do and would reccomend if you can just do it and give ubuntu a go.

Thanks!  Any idea where I can find steps for this?

---

### Post by martrn on 2008-04-30
> **shaffan33 said:**
> Thanks!  Any idea where I can find steps for this?

1.  Installing a small boot partition - No I don't do it on any of my systems.

2. For not installing grub :-

How to use Windows Vista’s Boot Manager to boot Linux
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx")
[http://www.justlinux.com/forum/showthread.php?threadid=150601]("http://www.justlinux.com/forum/showthread.php?threadid=150601")

Try googleing booting linux from vista's boot manager.

Its not recommended a lot around here as most people will dual boot and install ubuntu to a second internal hard drive or install ubuntu as the major os, and its a windows problem to support.

---

