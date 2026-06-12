---
title: "simple little install questions."
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by degarb on 2010-12-16
When you upgraded from 9 to 10 did you need to reinstall everything?  I haven't tried this. Fear, fear, fear, man.

Also, if I add grub to primary on a 2002 computer, while Ubu in on external HD.   Wouldn't the computer need an OS to see the hard drive or not?  So doing this could break the machine?

At install, can't I specify and alternate drive for at least /home?  And would this break the machine if sde became sdf?

---

### Post by matt_symes on 2010-12-16
Hi

> **degarb said:**
> When you upgraded from 9 to 10 did you need to reinstall everything?  I haven't tried this. Fear, fear, fear, man.

Yes, that was a fresh install though. You can use tricks like dpkg --get-selections and dkpg --set-selections to help though. It also helps having /home on a separate partition.

> Also, if I add grub to primary on a 2002 computer, while Ubu in on external HD.   Wouldn't the computer need an OS to see the hard drive or not?  So doing this could break the machine?Install grub to the MBR of the external hard drive and set up external hard drive as first boot option in the BIOS, internal as second.

> At install, can't I specify and alternate drive for at least /home?  And would this break the machine if sde became sdf?Yes, but use UUID's and not device names in fstab.

Kind regards

---

### Post by degarb on 2010-12-16
> **matt_symes said:**
> Hi



Yes, that was a fresh install though. You can use tricks like dpkg --get-selections and dkpg --set-selections to help though. It also helps having /home on a separate partition.

Install grub to the MBR of the external hard drive and set up external hard drive as first boot option in the BIOS, internal as second.

Yes, but use UUID's and not device names in fstab.

Kind regards


Sorry, I tried this, but machine will not boot from external drive.  I am worried grub will freak if no linux found because it may need good bios to see it.

What other stuff that takes a lot of space can be moved off main drive? bin?

---

### Post by degarb on 2010-12-16
"I stick in my usb drive, open a terminal and run

dpkg --get-selections > file

and I save that file to my usb drive and take it home.

Once home, I boot up my system which is running a fresh install of breezy and run:


cat file > dpkg --set-selections

and then 

sudo apt-get dselect-upgrade

and apt will download and install all the packages that are installed on my borhter's box. I can then save everything in /var/cache/apt/archive to a cd (wiki.ubuntu.com/AptMoveHowto/simple) and bring it to him."


I guess sudo apt-get dselect-install would move them to new machine?

---

### Post by degarb on 2010-12-16
Now if you moved /home and upgraded 9 to 10, would you loose the home, and need to redit the fstab?

---

