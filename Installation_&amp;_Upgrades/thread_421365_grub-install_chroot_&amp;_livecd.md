---
title: "grub-install chroot &amp; livecd"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by blazerte on 2007-04-24
WinXP installed first then feisty beta4 with grub. Upgrade to final feisty. 
All is fine. But whoops, something's weird with WinXP install so want to 
re-install XP. But I know it will trash the MBR so first check that 
grub-install works.

Boot to live Kubuntu, As root:

mount -t ext3 /dev/sda2 /mnt
chroot /mnt
grub-install /dev/sda

Get error that it can't find /dev/sda in chroot. 
And yet I mounted /dev/sda2 earlier ???

Rebooted to Kubuntu on /dev/sda2 and grub-install works fine there.
But this will not help when XP overwrites the mbr.

The live cd is kubuntu feist beta4, not final but I doubt that's the problem.
Am sure I've booted to a live cd, chrooted and reset the mbr before, but 
maybe that was back in the lilo days.

???

---

### Post by phidia on 2007-04-24
Open the /boot/grub/menu.lst file for your install and take a look at how grub calls out the drive & partition that the ubuntu install is on. I'll bet the notation after "root" is _not_ sdX,X because although there are exceptions-which makes this complicated grub generally doesn't use "s" as a drive symbol.

e.g my sata drive is seen by grub as hd2

And in using grub-install you may want to try grub-install (hdX)

---

### Post by blazerte on 2007-04-24
grub-install hd0
gives the same error message:
/dev/sda2: Not found or not a block device.

grub-install just doesn't like being called in a chroot.
But after looking at it's man page again, I realized you don't need chroot.
This worked:

Boot to live Kubuntu, As root:

mount -t ext3 /dev/sda2 /mnt
grub-install --root-directory=/mnt /dev/sda

I'm thinking my chroot fixation came from doing that with lilo a long time ago.

So now I can re-install WinXP.  
(what a pain; the drive lettering is all screwy with 2 removable usb devices becoming C:, D:, the cd-rom is E:, and  the hard drive (sda) is F: My wife insists that the hard drive be C:  )

---

### Post by blazerte on 2007-05-01
Later, for some reason, had to add --recheck to the grub-install invocation.
Without got an error about the drive not recognized by BIOS.

Boot to live Kubuntu, As root:

mount -t ext3 /dev/sda2 /mnt
grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by liniaal on 2008-01-15
thanks!
i had to move ubuntu (albeit 7.10 :P) from one sata disk to another, and i had the same result.

---

