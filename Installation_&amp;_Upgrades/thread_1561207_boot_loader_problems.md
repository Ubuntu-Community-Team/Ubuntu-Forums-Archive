---
title: "boot loader problems"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by cfdusr on 2010-08-25
Hi,
 
I just spent my entire day installing and configuring 10.04 on my desktop at work. I am using gnome and I also set up NFS and NIS clients on the machine. 
 
However, I accidentally left the installation CD in the CD drive and rebooted the machine. Though I did not go through the installation, I may have abruptly stopped the booting from the CD, which changed the grub bootloader menu.
 
I see extra options in the boot menu. Now when I choose a normal boot option for ubuntu 10.04, the system reaches the "ubuntu ..... " screen and hangs. 
 
I was able to boot the system in the recovery mode. I see all the users and NIS and NFS setup. So it appears that nothing has been disturbed on the ubuntu partition.
 
I am not sure if I should reinstall grub boot loader? or try starting gnome from recovery mode, or try something else to get the normal booting into gnome working.
 
Any suggestions, help, references would be welcome.
 
Thank you
cfdusr
 
PS: I have a dual boot system with windows XP on the other half of the partition.

---

### Post by cfdusr on 2010-08-25
To clarify on the extra menu option on the boot menu. This is what the boot menu looks like
 
ubuntu, with linux 2.6.32.24-generic
ubuntu, with linux 2.6.32.24-generic ( recovery mode )
ubuntu, with linux 2.6.32.24-generic
ubuntu, with linux 2.6.32.24-generic ( recovery mode )
Memory test (memtest86+)
Memory test (memtest86+, serial console)
Windows NT/2000/XP (loader)  (on /dev/sda2)

---

