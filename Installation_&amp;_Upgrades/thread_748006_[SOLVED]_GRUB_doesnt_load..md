---
title: "[SOLVED] GRUB doesnt load."
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by talib on 2008-04-07
Hello Every one, 

I am using Aspire 5315 machine with Vista os installed in it, 
I have installed Ubuntu as a dialbooing, 

I have used the Partation manager of live cd to creat a free space, and I installed the ubuntu, 
bow now the prob is that Grub bootloader doesnt load, 
when I start the laptop it gives me the following error

[I]Media test failure, check cable
No bootable device--Insert boot disk and press any key[/I]


But when I insert the LiveCD, i can login using the last option of the CD (boot from first hard disk) when I chose that the GRUB bootloader loades and it works fine.. 


:confused::confused:

---

### Post by housam on 2008-04-07
[[COLOR="Red"]_reinstall Grub_[/COLOR]]("https://help.ubuntu.com/community/GrubHowto#head-f60bd54bfea5b5afbbb8eab20586240d973cdde3")

---

### Post by dstew on 2008-04-07
A couple of thoughts...

It seems that the computer is trying to boot from a removable media device. Have you checked your BIOS to make sure the hard disk is before the CD-ROM or USB in the boot order?

Also, it is possible that grub was not installed correcty. It should be installed to the MBR of the hard disk (first hard disk if you have more than one). That might also explain the behavior of your system. I think [these instructions]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") are a bit clearer than those in the link posted by housam, but it would be good to read both to get an idea of how grub behaves.

---

