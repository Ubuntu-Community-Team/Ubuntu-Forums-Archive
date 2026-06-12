---
title: "Add Windows XP on slave drive to Grub Boot Menu??"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by Chatterbox7985 on 2006-12-20
Hi.

I recently installed Ubuntu as the only OS on one of my hard drives.  It's set as the master drive.  However, I would also like to be able to boot into Windows XP, which is installed on a completely separate drive.  I've set the Windows XP drive as the slave.

Since Ubuntu and Windows XP are on completely separate drives, how can I edit the boot.conf file to add Windows XP, so I can boot from that as well?  Ubuntu is on /dev/hda1 and Windows XP is on dev/hdb1, as listed in QParted.  Any help would be greatly appreciated.  Thanks!!

-TJ

My boot.conf file looks like this:

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

---

### Post by K.Mandla on 2006-12-20
It might be a little tricky, but this wiki page might give you some ideas: [uwiki]GrubHowto[/uwiki]. If you know the drive is hdb1, I think it's just a matter of making another entry in the menu.lst file, and making sure the root (hdX,X) pointer is correct.

If that fails, try searching for "edit grub." There are a lot of results, and one of them should push you in the right direction.

P.S.: It might also be helpful to see if you can find someone else's menu.lst file, that's already set for a dual boot. It might give you a closer idea as to what the entry will look like, and you might just be able to edit that root (hdX,X) parameter and set it free. Good luck!

---

