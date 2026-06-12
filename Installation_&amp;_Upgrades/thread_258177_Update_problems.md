---
title: "Update problems?"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2006-09-15
Any know when it's safe to install the new kernel with it's other updates? (see below)

* linux-image-2.6.15-26-386

* linux-restricted-modules-2.6.15-26-386

* linux-restricted-modules-common

* xorg-driver-fglrx

:confused:

---

### Post by randell6564 on 2006-09-15
> **flodis said:**
> Any know when it's safe to install the new kernel with it's other updates? (see below)

* linux-image-2.6.15-26-386

* linux-restricted-modules-2.6.15-26-386

* linux-restricted-modules-common

* xorg-driver-fglrx

:confused:

Depends on what kind of [graphics]("http://www.ubuntuforums.org/showthread.php?t=257353&page=8") hardware you are using i guess. I wanted to [know ]("http://www.ubuntuforums.org/showthread.php?t=258074")too

---

### Post by Jaxilian on 2006-09-16
> **randell6564 said:**
> Depends on what kind of [graphics]("http://www.ubuntuforums.org/showthread.php?t=257353&page=8") hardware you are using i guess. I wanted to [know ]("http://www.ubuntuforums.org/showthread.php?t=258074")too

I am using ATi Radeon X600 Mobility

---

### Post by hearnden on 2006-09-16
> **flodis said:**
> I am using ATi Radeon X600 Mobility

Regardless of your graphics card, these updates are still not safe.  On my machine the new kernel can't even read my hard drive partitions right, and booting fails with a kernel panic.  Spent MANY hours regressing to the previous version (46), because the upgrade overwrites your current 2.6.15-26 kernel in /boot.  Hehe, just when you figure out why your machine is hosed, you realise that you CAN'T ROLLBACK, and you can't use dpkg or anything because the boot process fails very early!  Luckily my laptop still hard the previous version, so I could copy them to a USB drive, and then get GRUB to load that kernel instead (replace 'root (hd0,0)' with 'root (hd0,1)' in GRUB boot menu).

Oh and it will probably kill your sound too. 

Thanks again Ubuntu update team!

---

### Post by randell6564 on 2006-09-16
> **hearnden said:**
>  because the upgrade overwrites your current 2.6.15-26 kernel in /boot.  


Thats strange, because every time that I have updated my kernel, I was always left with the old one that I could choose at boot time if the new version was not to my liking!

---

### Post by Jaxilian on 2006-09-16
> **hearnden said:**
> Regardless of your graphics card, these updates are still not safe.  On my machine the new kernel can't even read my hard drive partitions right, and booting fails with a kernel panic.  Spent MANY hours regressing to the previous version (46), because the upgrade overwrites your current 2.6.15-26 kernel in /boot.  Hehe, just when you figure out why your machine is hosed, you realise that you CAN'T ROLLBACK, and you can't use dpkg or anything because the boot process fails very early!  Luckily my laptop still hard the previous version, so I could copy them to a USB drive, and then get GRUB to load that kernel instead (replace 'root (hd0,0)' with 'root (hd0,1)' in GRUB boot menu).

Oh and it will probably kill your sound too. 

Thanks again Ubuntu update team!

For me it kinds works:

* linux-image-2.6.15-26-386 - Works

* linux-restricted-modules-2.6.15-26-386 - Works

* linux-restricted-modules-common - Works

* xorg-driver-fglrx -  Works

I guess I was lucky :grin:

---

### Post by hearnden on 2006-09-16
> **randell6564 said:**
> Thats strange, because every time that I have updated my kernel, I was always left with the old one that I could choose at boot time if the new version was not to my liking!

The kernels that I have are only preserved up to the fourth version number (i.e. I have an older 2.6.15.23 kernel in the boot partition and a corresponding GRUB entry).  But that because these updates are for versions within the 2.6.15.26 kernel version (i.e. 2.6.15.26-46 to 2.6.15.26-47), the update will overwrite any existing 2.6.15.26 kernel you have.

I don't know what it is about this update that has caused so many problems, but not everyone gets them, so it may work fine for you.  My sound is still broken though.

---

### Post by superba on 2006-11-17
> **randell6564 said:**
> Thats strange, because every time that I have updated my kernel, I was always left with the old one that I could choose at boot time if the new version was not to my liking!

err  uh uh..... How do you choose the previous kernel at boot?  Not that I'm a noobie or anything;  I know everything;  I just forgot some of it.

I believe a semi automatic update hosed my network big time and am not aware of what else it may have wounded.  How am I writing this, you ask?  Well, as part of my intranet, I have a trusty Win XP Pro up to date which works and doesn't kill its network.  

Some distros of 'nix offer a boot choices menu but I haven't seen one with v6.06, daffy duck;  maybe I should pay attention.

TIA.

Cheers!

---

### Post by hearnden on 2006-11-18
If you have GRUB installed then it should present you with a menu on boot to choose which kernel and mode (and which other OS if you have any).  The default v6.06 install uses GRUB, so it should be there unless you specifically chose a different bootloader (e.g. lilo) or maybe WinXP replaced GRUB with its own bootloader (easy to reverse though).

---

### Post by superba on 2006-11-18
> **hearnden said:**
> If you have GRUB installed then it should present you with a menu on boot to choose which kernel and mode (and which other OS if you have any).  The default v6.06 install uses GRUB, so it should be there unless you specifically chose a different bootloader (e.g. lilo) or maybe WinXP replaced GRUB with its own bootloader (easy to reverse though).

Thank you for your reply.  Win XP is gonzo on this box;  ergo, it couldn't have anything to do with what's happening.  GRUB is installed and following previous advice, I invoked G by pressing <esc> and got a 4 choice menu.  I sequentially booted using each one.  As you undoubtedly know, the choices were 2 kernel versions and a boot to cl of each.  None of the choices worked.  

This is really frustrating, for the rest of my network works.  I  moved the Ubuntu box to another port on the router and used a different, known good, network cord last night with no joy.  

Right now I'm mulling over blowing this install away and reinstalling;  maybe I'll use v6.10 instead of v6.06 this time.  May as well have a failed latest version.

Any other ideas?

TIA.

Cheers!

---

### Post by hearnden on 2006-11-18
Did anything interesting happen for each choice that didn't work?  e.g. error messages?

From the GRUB menu you can get to a GRUB command-line, which lets you manually specify boot options.  GRUB also has some levels of auto-completion, so you can to a minimal degree poke around your device to see that everything that should be there for booting is there.

---

