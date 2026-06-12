---
title: "how to remove ubuntu 7.10"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by taekwondosnw on 2008-03-25
ok i installed ubuntu 7.10 next to vista. then i upgraded to ubuntu 8.10 (beta) (i believe) now i have all three on my computer 

EXAMPLE OF MY PROBLEM

[IMG]http://img401.imageshack.us/img401/7174/hpim0917ey4.jpg[/IMG]


it's the grub menu^^^

now how do i get rid of 7.10? and keep vista and 8.04 )beta?)

---

### Post by solaceinsilence9 on 2008-03-25
GOSH! please resize the pic if possible! Anyway though, in order to get rid of the old version of Ubuntu you need to simply delete the Partition it is on. The simplest way to do this, and the way I handle partitions is to download a program called Cute Partition Manager. After you download it make a bootable CD. Put it in your CD tray and restart your computer. Boot from the CD-ROM and it will load the program. It will list all of your partitions on your hard drive. So just select 7.10 and press F8 (I believe it tells you which Function key is which) to delete it. 

Hope that helps.

---

### Post by solaceinsilence9 on 2008-03-25
I tried what I posted above and it works for deleting Ubuntu, but for some reason it didnt get rid of the GRUB menu. It just loaded the Grub menu and then I got a Error 17. So sorry for the somewhat correct info.:confused:

---

### Post by taekwondosnw on 2008-03-26
well i want the grub menu so... i guess what you said will work? still?

---

### Post by mrhammad on 2008-03-26
Yes you can delete the partition on which Grub of Ubuntu 7.10 is loaded bcoz now grub that is loaded is actually in 8.10 partition.
Also you can edit /boot/grub/menu.list of 8.10 to remove the titles of 7.10 ;)

---

