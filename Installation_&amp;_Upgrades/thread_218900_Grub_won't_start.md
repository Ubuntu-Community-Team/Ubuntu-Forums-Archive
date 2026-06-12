---
title: "Grub won't start"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by Mads on 2006-07-19
I have installed Dapper off the Live CD onto my SATA 120gig drive and when reboting the system stopped 'not operating system found'

I installed Xandros to see if there was a problem with my SATA drive. There wasn't and Xandros loaded fine.

So I tried another install of Ubuntu dapper and when I get is the Xandros loader, with no sign of Ubuntu despite the fact after mounting the drive on the live CD all the ubuntu files are there.

I tried to CHROOT and grub-install but I get the following messge back ' not found or not a block device' 

Please help! :(

---

### Post by zxee on 2006-07-19
> I tried to CHROOT and grub-install but I get the following messge back ' not found or not a block device'


That message means grub doesn't recognize your partition. Please post your /boot/grub/menu.lst and specify which partition dapper is installed to.

---

