---
title: "Windows 7 replacing XP in dual boot"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by mikeody on 2010-01-12
Hello All,
There has been lots written recently on this subject but I am still very confused and am asking for help.
I have Karmic on one drive and XP on a second drive dual booting perfectly and I am very happy. Both drives have been backed up.
I now have a new copy of Windows 7 and want to simply replace XP with Windows 7 whilst maintaining dual boot.
Can anyone please give me a list of actions required - or point me to somewhere that I can find such a list ?
I felt fairly comfortable with GRUB 1 but GRUB 2 is somewhat an unknown quantity for me.
Thanks.

---

### Post by x33a on 2010-01-12
I think windows 7 will overwrite your mbr and then you'll simply have to reinstall grub.

you could give supergrubdisk a try.

---

### Post by e-Gee on 2010-01-12
After installing windows 7 just boot from live cd and from terminal tipe this :

sudo fdisk -l

sudo mount /dev/sda1 /mnt

sudo grub-install -–root-directory=/mnt/ /dev/sda

and restart computer on first boot in to ubuntu go to terminal and type :

sudo update-grub

And that is it

---

### Post by mikeody on 2010-01-12
Thanks e-Gee,
All seemed to go well until :
"and restart computer on first boot into Ubuntu go to terminal and type : sudo-update grub"

Windows 7 installed successfully and I worked thru the instructions via a terminal on the live cd. I removed CD and then restarted.

I then get :

GRUB loading
error : file not found
grub rescue >

How do I actually get to "update-grub" ?
Thanks.

---

