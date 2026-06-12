---
title: "moving ubuntu to a new drive"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by jeanlucmalet on 2009-12-12
I just received a new hard drive and I want to move my ubuntu (9.04 upgraded to 9.10) to it,
I still have grub1 installed
I created a partition,
$ sudo su
# cd /
# mount /dev/sdb1 /media/ubuntu
# cp -avx . /media/ubuntu
# mount /dev/ /media/ubuntu/dev -o bind
# mount /proc /media/ubuntu/proc -o bind
# chroot /media/ubuntu
# vi /etc/fstab 
changed the uuid occurences to the uuid of the new partition
# vi /boot/grub/menu.list
changed the uuid occurences of old boot drive to the new one
# grub-install --recheck /dev/sdb1 
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage2 not read correctly.

I googled without success, I RTFM of grub without finding this error message.....
any idea?
thanks
JLM

---

### Post by MelDJ on 2009-12-12
try this: [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by jeanlucmalet on 2009-12-12
after more tries I found that grub isn't behaving correctly if ran into a chroot.... that's lame
[http://who.is.free.fr/dokuwiki/doku.php?id=grub](http://who.is.free.fr/dokuwiki/doku.php?id=grub)
however using the sequence 
```
grub --batch
root (hd1,7)
setup (hd1,7)
```
did the trick.... well still prefer lilo upon grub (more since I got unusable boot disk after removing the ubuntu from the old drive, I had to recompile ms-sys to restore the mbr, at least with lilo when you remove lilo's files you can still boot on the others os.....)

---

