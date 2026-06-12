---
title: "restoring previous multi boot loader"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by five on 2006-03-30
After installation of ubunto, with some errors, I want to unistall it,

at the moment grub works, it start ubunto (text) , win 98 and winxp , that ok, at grub sceen, when I select windows , it bring me to a second screen, the win xp multi boot loader ( to select win 98 or XP ). 

Now, how can I uninstall grub and restore the previous xp multi boot loader?

I have tried with XP cd, console, fixboot d: and nothing happened.
I think that using fdisk c: /mbr will destoy the multi boot isn't it ?

What should I do.
 
Thanks.

---

### Post by nerderello on 2006-04-02
from what you have said, you want to get rid of grub and use winxp's boot.ini .

Grub lives in two places. It lives on the master boot record (mbr) of the hard disk (every hard disk has one of these). The rest of grub lives in the /boot/grub folder in Linux. The mbr part of grub uses the files in /boot/grub to display menus and to cope with various filesystems.

You say that you tried the fixmbr option in the winxp cd, but that this did not work. I can only guess that you have two hard disks (each with its own mbr) and you fixed the mbr of the hard disk that you do not boot from.

If this is not the case, then you could try the fdisk /mbr option. Both of these windows techniques are there to replace grub from the mbr and put some windows code in its place. The windows code simply points at the first byte of the first sector of the windows C: drive.

Have fun

Nerderello
ps. you do realise that a correctly setup grub will happily cope with WinXP and Win98 and Linux and a whole bunch of other operating systems?

---

