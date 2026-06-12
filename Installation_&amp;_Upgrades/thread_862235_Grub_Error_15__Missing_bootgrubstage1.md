---
title: "Grub Error 15  Missing /boot/grub/stage1"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by clbaines on 2008-07-17
I did an upgrade from 7.04 to 7.10 using the upgrade
manager. I had some problems but I finally got a clean
upgrade. My system is a Dell laptop Inspiron. Ubunto
is the only os and is not a dual boot. Now after the
upgrade it will not boot. I read several posts concerning
my error 15. I booted from dvd and mounted root. I have
no /boot/grub/stage1 file.
I did the following command sequence.
sudo grub
find /boot/grub/stage1
root (hd0,2) I foun this from another command.
setup ('hd0,2)

Now the setup runs but says /boot/grub/stage1 No 
after running.

Can I boot to root again and use vi or vim to create
/boot/grub/stage1 and run setup and get it to work?

Any other solutions?

---

### Post by logos34 on 2008-07-17
Boot frm the live cd and try this:

Mount root:

> sudo mkdir /media/sda3 
sudo mount -t ext3 /dev/sda3 /media/sda3(*I'm just assuming that's root since you used 'hd0,2' above.  Correct if necessary)

> sudo mount --bind /dev /media/sda3/dev
sudo chroot /media/sda3Backup your menu.lst:
> 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bakReinstall Grub:

> sudo grub-install /dev/sda 
sudo update-grub

exitGive that a shot.

---

### Post by flint_ on 2008-08-15
Greetings,

One thing that I found entertaining was while fooling around with grub, and moving my boot disk to another partition, and being in Hardy, is that my fstab -l suddenly started reporting the drive as "sda" instead of "hda".  This caused all sorts of headaches when I performed the setup(sd0).  Suddenly the beast would boot but simply could not deal with the /etc/fstab which had all the devices listed as hda as opposed to sta's.  Changing all of the hda's to sda's fixed the problem, but it was interesting for a while.

The lesson here is watch for the change from hda to sda.

Regards,

Flint

---

