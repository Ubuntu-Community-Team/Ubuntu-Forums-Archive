---
title: "SUSE / Ubuntu fighting over MBR?"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by megamaced on 2006-09-25
I'll try and make this as short as possible :)

I've got openSUSE 10.0 on the primary hard drive and Ubuntu 6.06 on the second hard drive. SUSE's bootloader is written on the MBR. Ubuntu does not have a bootloader at all (SUSE's bootloader wrote over it :-?  )

At the moment, everything is fine. SUSE's bootloader can boot Ubuntu's kernel. Fine.

BUT: Ubuntu wants to upgrade it's kernel through system updates and I am worried that either **A )** SUSE's bootloader will no longer boot Ubuntu or **B )** Ubuntu will replace SUSE's bootloader and I will no longer be able to boot SUSE  :o 

What should I do?

---

### Post by daschl on 2006-09-25
if you manage your bootloader over an other opsys than you probably have to manage it manually. 

you can write a short script that only mounts the /boot of your /dev/hda, checks what new kernel version is installed (uname -r) and updates the menu.lst!

that shouldn't be to difficult. if someone knows a "professional" tool for this i'd like to know it too :D

---

### Post by Stone123 on 2006-09-25
I dont think it will happend, update-grub will only update config files.

---

### Post by lha on 2006-09-25
> **megamaced said:**
> I'll try and make this as short as possible :)

I've got openSUSE 10.0 on the primary hard drive and Ubuntu 6.06 on the second hard drive. SUSE's bootloader is written on the MBR. Ubuntu does not have a bootloader at all (SUSE's bootloader wrote over it :-?  )

At the moment, everything is fine. SUSE's bootloader can boot Ubuntu's kernel. Fine.

BUT: Ubuntu wants to upgrade it's kernel through system updates and I am worried that either **A )** SUSE's bootloader will no longer boot Ubuntu or **B )** Ubuntu will replace SUSE's bootloader and I will no longer be able to boot SUSE  :o 

What should I do?

A) If you remove the kernel you are currently using, SUSE's bootloader won't be able to boot Ubuntu.

B) It won't happen.

I prefer to install Grub for every distro I have. You could install Grub for Ubuntu somewhere on your secondary hard drive and chainload Ubuntu's Grub from SUSE's Grub. This lets both distros to upgrade their own Grub menus when you get a new kernel.

---

### Post by megamaced on 2006-09-25
> **lha said:**
> ou could install Grub for Ubuntu somewhere on your secondary hard drive and chainload Ubuntu's Grub from SUSE's Grub. This lets both distros to upgrade their own Grub menus when you get a new kernel.

That's exactly what I need to do. :)  But how can I get Ubuntu's GRUB to re-install on the boot sector of the second hard drive?

---

### Post by lha on 2006-09-25
> **megamaced said:**
> That's exactly what I need to do. :)  But how can I get Ubuntu's GRUB to re-install on the boot sector of the second hard drive?
[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively")

---

### Post by candtalan on 2006-09-25
> **megamaced said:**
> I'll try and make this as short as possible :)

I've got openSUSE 10.0 on the primary hard drive and Ubuntu 6.06 on the second hard drive. SUSE's bootloader is written on the MBR. Ubuntu does not have a bootloader at all (SUSE's bootloader wrote over it :-?  )

At the moment, everything is fine. SUSE's bootloader can boot Ubuntu's kernel. Fine.

BUT: Ubuntu wants to upgrade it's kernel through system updates and I am worried that either **A )** SUSE's bootloader will no longer boot Ubuntu or **B )** Ubuntu will replace SUSE's bootloader and I will no longer be able to boot SUSE  :o 

What should I do?


I am not entirely sure I have a similar system, but anyway:
I have a PC with a single HD with multiple distros including windowsxp installed as multi boot. This is  a demonstration machine. The boot loader is grub, and I use the suse loader because it happens to be the prettiest  :-)

I have just updated edubuntu (6.06) which included a kernel image update and it required a restart following. However, the suse bootloader worked fine, no problems when immediately choosing edubuntu to (re)start. I also have Ubuntu and Kubuntu and others on this PC so the sequence will have been completed a number of times without me noticing a problem.
hth

---

### Post by megamaced on 2006-09-26
Well I created a rescue disk in SUSE just in case the worst happened. I installed the new kernel in Ubuntu and restarted my computer. Thankfully Ubuntu did not overwrite the MBR but SUSE's bootloader didn't know about the new Ubuntu kernel. So I booted into SUSE and entered the new Ubuntu kernel and now it works fine :)

BTW, Ubuntu's bootloader had a Memtest86 and a failsafe option that isn't showing in SUSE's bootloader. How can I get that to appear?

---

