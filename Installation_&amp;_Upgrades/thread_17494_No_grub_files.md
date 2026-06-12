---
title: "No grub files"
date: 2005-02-28
forum: Installation &amp; Upgrades
---

### Post by nix on 2005-02-28
Hi, I'm just new to Ubuntu coming from gentoo (vidalinux).
AMD 64 with Asus A8V-E motherboard.  Trying to install Ubuntu64  4.10 onto 1st SATA disc.

I am wanting to triple boot with XP and gentoo (have vidalinux grub boot manager).

The problem is that when I do the install - not to install grub (with Ubuntu) and it reboots, there is nothing in /boot directory.  No grub, no vmlinuz, initrd etc.

Are these somewhere else??

I have repeated this on 2 occasions and am downloading 4.10 again just in case.

Have also done the install WITH installing grub, no difference.

What is going on!!

Anyone with similar problem??

Thanks for any help.

---

### Post by kafton on 2005-03-01
Wen you reboot, do you reboot into ubuntu or gentoo? If you are booting into ubuntu the vmlinuz etc. files are installed into /boot.  Did you add a stanza for ubuntu in vidalinux grub boot manager? 
I currently triple boot gentoo, ubuntu, and mandrake 10.0 -but no windows- with no problems .
Ed

---

### Post by nix on 2005-03-02
Hi Kafton,
Thanks for the comments.

Just worked out what is wrong.  I was trying to find the grub files using gentoo.  For some reason, not visible (? no access allowed) whereas I am able to see other files.
Ubuntu has a different way of labelling hard drives and SATA drives in boot field in grub.
It labelled my /boot on my SATA drive (at 5th partition, first drive in sequence ) as (hd1, 4).  ie it is seeing the SATA drive second.
So it installed the MBR on my second drive (PATA)!!

So if I changed the boot order in the bios I found ubuntu grub loader, which then needed tweaking wrt the drive locations in order to boot!!
Anyway, copied grub loader details to vidalinux grub loader, adjusted and have a functioning triple boot - no problems  ](*,) 

Now I'm just trying to get nvidia to work - how to remove modules which are being loaded??  is there an equivalent to /etc/modules.autoload.d/kernel ...

Thanks.

---

