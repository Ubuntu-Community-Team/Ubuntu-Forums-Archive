---
title: "Grud Rescue Error After Update"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by campb.andrew on 2011-06-07
_**[SIZE="3"][COLOR="Red"]GRUB RESCUE ERROR AFTER UPDATE[/COLOR][/SIZE]**_

Sometime ago last year, i installed Ubuntu 10.04 on my Compaq Presario 2100 Laptop via Wubi. My CD Drive wasnt working. I had installed it on a separate partition on my hard drive so i could dual boot with Windows XP. I thought this would have worked well. And it did until i decided to update to 10.10. I selected my hard drive option...or what i thought was the correct one and left it to update overnight. I woke up the next morning to a grub rescue error and no way to boot into XP or Ubuntu. :( 

I think i've screwed over the laptop. I can't boot from a flash drive, and i doubt an external HD would help since it wouldnt boot from the usb. And as i mentioned before, the CD drive doesn't work. So i can't reinstall from a cd or usb.

Is there anyway I can recover either of my OS's? I don't mind Ubuntu or XP being my main OS.

---

### Post by bcbc on 2011-06-07
I'm not aware of any way to fix this without being able to boot some sort of CD or USB.

If it's a laptop you should be able to pop out the drive and plug it in to another computer - or hook it up via an external drive that allows pluggable drives or a cable. Maybe not trivial but may be your best bet.

Then follow the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") solution for Problem #1 to update the bootloader in the MBR (and later also apply the Permanent fix mentioned under Problem #2).

---

