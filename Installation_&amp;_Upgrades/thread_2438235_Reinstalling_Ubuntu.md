---
title: "Reinstalling Ubuntu"
date: 2020-03-07
forum: Installation &amp; Upgrades
---

### Post by pengyou2 on 2020-03-07
I have used Mint for a few  years, but always as a p&p (plug and play) novice.  There are some apps that work in Ubuntu but not in Mint, so I installed Ubuntu.  Here is where my story begins.

1. Now, I cannot access the 2 data drives I was using before.  I can read them, I can open music files and play them but I cannot write to them.  Someone mentioned that I should have closed the drives first.  Any suggestions on how to fix this?

2.  I just bought an nvme m2 drive.  I am going to install that and then put Ubuntu on that - in search of the faster boot up!  At the same time I want to install a new video card, an nvidia, as well as usb/nic card.  If I install the new  hardware, will Ubuntu ask me about it?  Also, what do I need to do to the present OS disk so that I can still access it after the new os is installed?

I am working through a set of videos to learn Linux, but I would appreciate if you could help me "speed things up" with some commands.

---

### Post by oldfred on 2020-03-07
What format are the other drives?
If NTFS, you have to turn off Windows fast start up which sets the hibernation flag. Linux NTFS driver will not mount hibernated partitions to prevent damage.
If Linux format you have to give yourself ownership & permissions.

If you install nVidia driver, you probably will have to use nomodeset to boot in low graphics mode, so you can use System Settings to install nVidia driver. Or boot recovery mode and use command line to install nVidia driver. Do not install from nVidia, but only from Ubuntu repository.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Are current installs UEFI or BIOS.
You need to use same boot mode and how you boot install media is then how it installs.
But most with newer systems that support NVMe are UEFI based hardware & then all installs should be UEFI.

See link in my signature below for more info on UEFI install & repair.

---

