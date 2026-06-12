---
title: "Installed Xubuntu twice - GRUB messing with Windows XP"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by thomashw on 2008-09-27
The first time installing Xubuntu Linux, I installed linux onto a seperate HDD, and had a previously installed Windows XP installed on a SATA drive. I installed GRUB onto the SATA drive so I could leave it as the primary, but I ended up having to use a recovery program to get my files off of the drive before having to reinstall Windows. (The files became corrupted for whatever reason.)

After my reinstall of Windows, I tried again, but installed GRUB to the linux drive and left the Windows alone. I then put the linux drive as the primary, but Windows wouldn't boot (I changed the GRUB settings, but it would restart my computer when I tried to boot from the Windows drive.) I then put the primary back as the SATA drive, but GRUB had done something to my bootloader for Windows and it would no longer boot. I tried repairing the boot sector of Windows with the CD, but nothing worked.

I'm on my third installation of Windows XP. I'm wondering how I can install Xubuntu without it TOUCHING my Windows XP install? I have a completely seperate HDD for Xubuntu to go on, and I would prefer to configure GRUB AFTER I install Xubuntu so I know it hasn't done anything to mess up my Windows XP install.

What should I do to keep both completely seperate (for now)?

---

### Post by cariboo on 2008-09-27
the windows boot files need to be in the first partiton of the first hard drive and you can put Ubuntu where ever you want. You have to install grub on the master boot record of the first hard drive in order for it to work properly. If you leave things setup as you have them set up now and install grub to the mbr of the first hdd you shouldn't have any problems. your installation will only bother windows if you tell it to.

If you had corrupted files on your origional install of windows, it might be an idea to find out why this happened.

Go to hard drives manufacturers web site and download and then run the diagnostic utulities on your hard drive, there may be a problem that needs attention.

Jim

---

### Post by thomashw on 2008-09-27
Hi Jim,

I've reformatted my hard drive, and my current Windows install is working flawlessly. I only run into problems when I install Xubuntu.

I just want to install it on my second HDD, and be able to boot Xubuntu by changing the boot order in the BIOS.

I just don't want GRUB to touch my Windows install - should I just unplug the SATA drive while I install Xubuntu on the second drive?

Thank you for the help so far.

---

### Post by confused57 on 2008-09-27
> **thomashw said:**
> Hi Jim,

I've reformatted my hard drive, and my current Windows install is working flawlessly. I only run into problems when I install Xubuntu.

I just want to install it on my second HDD, and be able to boot Xubuntu by changing the boot order in the BIOS.

I just don't want GRUB to touch my Windows install - should I just unplug the SATA drive while I install Xubuntu on the second drive?

Thank you for the help so far.

Maybe this thread will help:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by thomashw on 2008-09-28
Awesome. I'll take a look. Thanks a ton.

---

