---
title: "Installing ubuntu as dual boot alongside windows 8"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by Karen Forrest on 2012-12-17
Hi I am trying to set up a new laptop. It's a lenovo G580 and came with windows 8 on it. 
I can't get into the boot menu and so I can't get the computer to boot from my liveUSB. I've spent a couple of days now hunting around the internet for ideas and trying different things. 
I found my way to the PC settings page and tried booting from a different device - but only windows will boot.

I am not very tech-savvy - so some of what I have been reading doesn't make sense! I have been using ubuntu for a couple of years, so I'm not a complete newby - and have set up several laptops with a dual boot before. 

Any chance of some simple idiot proof advice?
Thanks,
Karen

---

### Post by SuperFreak on 2012-12-17
Found this by Google:[https://forums.lenovo.com/t5/Lenovo-3000-and-Essential/BIOS-for-G580-notebook/td-p/890169]("https://forums.lenovo.com/t5/Lenovo-3000-and-Essential/BIOS-for-G580-notebook/td-p/890169") Hope it helps

But now I have been able to to display the BIOS.
press F12 during POST -> Press the TAB from the [boot menu] -> [App Menu]
--- App Menu -------------
| 1. Diagnostic Splash |  <- Normally there is only No.1.
| 2. Setup                       |  <- Item to display the BIOS.
| 3. Diagnostic Splash |  <- Item No.1 is a duplicate.
-------------------------------

---

### Post by oldfred on 2012-12-17
You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive or DVD in UEFI mode. That way it will install in UEFI mode.

       Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
Use Windows to shrink the Windows partition to make room, but do not create new partitions with Windows. Reboot into Windows to let it run chkdsk or other fixes it does after a resize before installing Ubuntu.

But grub has a bug and does not create a correct chain load entry. Easiest way to create correct entry is to use boot repair.
       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
'Windows ...) (on /dev/sdXY)'

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Backups are always important and having a live repair CD/DVD/Flash for the current version of every operating system is very important.

       Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by Karen Forrest on 2012-12-18
That has been really helpful - at least in directing me to the right information.  I have made progress - but I still can't boot from USB.

I found how to access the bios setup and the boot menu - there's a special button labelled "One key recovery" which takes me straight there. I edited the setup - it is UEFI which I didn't change, but I enabled USB booting. Now when I go to the boot menu it recognises my USB stick as one of the options - but when I select it, it still boots windows from the hard drive. 

I have checked the USB stick is working and I can load ubuntu from it on another computer. I made it with the ubuntu-secure-remix-12.10-64bit.ISO and Startup USB Creator on my current ubuntu laptop. 

The new laptop is for my husband and currently he is telling me that if I can't get ubuntu running he will swap computers and leave me with the windows one...

---

### Post by grahammechanical on 2012-12-18
This is confusing me a little bit:

> but I enabled USB booting. Now when I go to the boot menu it recognises my USB stick as one of the options - but when I select it, it still boots windows from the hard drive.

Did you set the boot order so that the BIOS/UEFI looks first to the USB stick/DVD and then to the hard disk? If the machine is set to look for an operating system on the hard disk then it will load the OS that it finds on that hard disk and not look for an OS on the USB stick.

Regards.

---

### Post by oldfred on 2012-12-18
Some have had to turn secure boot off. 

Then from flash drive UEFI menu should show two choices, one UEFI and the other legacy/BIOS/AHCI or whatever. You will want to use UEFI as how it boots installer is how it installs.

---

### Post by Karen Forrest on 2012-12-18
Thanks - have changed the boot order now as well, but still get windows. 

In the bios setup secure boot is enabled, but I can't change that - I can't get the cursor to move there. Is there another way to disable it?

---

### Post by Androzani1 on 2012-12-18
Is it not a keyboard BIOS?

---

### Post by oldfred on 2012-12-18
Some have posted that you enable UEFI boot. Which to me would be enabling secure boot, but on that system it was enabling UEFI boot without secure boot. And if you have it in Legacy or BIOS boot then you cannot change UEFI settings.

---

### Post by Karen Forrest on 2012-12-20
Thanks for all that - I finally have ubuntu on the new laptop.
I couldn't change the secure boot setting - even in UEFI boot. But then I thought I'd see what happened if I selected legacy boot instead - and that worked.

Now to get the internet connection working....

---

### Post by oldfred on 2012-12-20
If you installed in legacy boot your have the BIOS install, but your Windows is in UEFI mode.

But Boot-Repair can convert your BIOS install to UEFI install by uninstalling grub-pc (for BIOS) and installing grub-efi (for UEFI). It will then add a correct  chain load entry from the grub menu to the Windows efi, so you can just set ubuntu as the default in the UEFI menu and boot either system.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)

grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
'Windows ...) (on /dev/sdXY)'

   Boot-Repair's correct entries
Windows UEFI loader

---

