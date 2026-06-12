---
title: "problem with grub (it is not seeing the other ubuntu installation)"
date: 2013-03-28
forum: Installation &amp; Upgrades
---

### Post by jessel on 2013-03-28
I have a desktop pc with ubuntu 32bit and windows xp already installed. The installation was such that there are two hard discs, one has windows, the other has ubuntu. The disc with ubuntu had separate root, boot, and home partitions.

I installed ubuntu 64bit onto a new partition, I thought that I checked the option to use the existing /boot partition, but my new 64 bit installation (which works fine) does not use the old /boot partition, and so I can only boot windows or 64bit ubuntu.

I have installed grub-customizer, and re-run it. It shows my old grub entries, but when I try to boot them I get an error.

How do I reinstall/modify/update grub so that I can boot either ubuntu system or windows?

Thanks,

Jesse

---

### Post by oldos2er on 2013-03-28
What is the error?

---

### Post by oldfred on 2013-03-28
You cannot share a /boot partition. If that is what you did you only have one set of kernels in /boot for one install. Most Desktops do not need a separate /boot partition. Some older systems with new large drives may need it.

Your new install should have installed grub2's boot loader to the MBR of your Ubuntu drive, but you have to manually selected that as part of Something Else.

---

### Post by jessel on 2013-03-28
oldfred:

How can i make grub2 see the other installation? I'm fine with using the new grub2 install, but I can't seem to make it see my other ubuntu install or whatever. I mean, I just want to make it boot the other installation (on /dev/sdb4) where the new installation lives on /dev/sdb3.


This is the error I get:
> 
error: file not found.
error: you need to load the kernel first.

Press any key to continue...

---

### Post by oldfred on 2013-03-28
Lets see details.  But if you used one  /boot partition, you only have one set of kernels to boot, even if the rest of the install is in another / (root) partition. It can be repaired by chrooting into it and adding the kernels.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by jessel on 2013-03-29
The problem was that i had two installations of ubuntu but could not boot them both. I only had installed the second installation because I wanted to test an installation before implementing it. What I did was to use clonezilla to back up my partitions to an image on a network drive then delete the "test" installation and re-install (but using the 64bit, not the 32 bit). This worked fine as you would imagine, since I specified my boot, root, and home partitions (I even deleted the "test installation" partition).

I did have to re-create the /etc/fstab, and I will have to re-install software, but programs like firefox & thunderbird are configured as they were.

If I had been smart, I would have used clonezilla to back up the boot partition before installing ubuntu beside the existing installation. Anyway, since I was able to use the 64bit version and verified that it does in fact work better for me, I skipped the step of fixing that installation because as I thought about it I had no long term plans of keeping it around.

As to the grub installation, it appears that grub-customizer does not allow the user to re-install grub. I like grub-customizer, becuase I just don't use grub often enough to keep a good working knowledge of it. Even re-reading the manual I still run into problems, and mostly I just want to move old kernel listing into an old versions folder...

Thanks for the help

---

