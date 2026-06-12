---
title: "WinXP deletes GRUB MBR after each reboot since dynamic disk used"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by lugduweb on 2006-10-08
Hi !

I was having a standard dual boot with WinXP (first IDE disk) and Ubuntu (second SATA disk), but now I can't boot my computer since I've enabled "dynamic disk" feature under WinXP.

The computer can't boot on GRUB anymore. I can chroot into Linux with a LiveCD and then correct the grub problem. When I log in windows XP it works, but when I reset, the GRUB menu is lost again :-P, so I have to go into the LiveCD and do it all again !
Could somebody help please ?

Note that might help others, on how to "chroot in Ubuntu with a LiveCD (here a Gentoo LiveCD)" :
mkdir -p /mnt/gentoo
sudo swapon /dev/sda2                  // my swap under ubuntu
sudo mount /dev/sda3 /mnt/gentoo       // my "/" under ubuntu
sudo mount -o bind /dev /mnt/gentoo/dev
sudo mount -o bind /proc /mnt/gentoo/proc
chroot /mnt/gentoo

grub
 find /boot/grub/menu.lst // search root disk partition
  [gives me (hd1,2)
 root (hd1,2)           // selects root
 setup (hd0)            // writing MBR again, seems to work
Then, it's OK, I can reboot and go back into a working XP...

But... when I reset XP... GRUB vanishes again !!!
So, how can I solve this problem ? Please help !

I've looked in google and found things about grub-ldm (is this the right patch tool - had troubles with pgp key) and also WinXP DISKPART where you can use the "RETAIN" command to re-create a MBR (but did not work for me).

So if someone could help me on that... It's really tricky !:confused:

---

### Post by lugduweb on 2006-10-08
I found a link with a bug entry in GRUB (but is it really a GRUB problem if WinXP crashed everything as if it was the only OS of the world)...
[http://savannah.gnu.org/bugs/?15048](http://savannah.gnu.org/bugs/?15048)

ATM, I've downloaded this software but I can't use a PGP (don't know why but it did not work even after having registered and created a key).
So, where can I find a binary of grub-ldm for K7 (or i386) ?

---

