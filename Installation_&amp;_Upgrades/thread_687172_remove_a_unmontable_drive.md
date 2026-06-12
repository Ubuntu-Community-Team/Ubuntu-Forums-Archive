---
title: "remove a unmontable drive"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by sylver1109 on 2008-02-04
Ok, i have install Xubuntu on a fakeRAID 0 with dmraid in dual boot with XP. all installation is going fine with the documentation on the website.

but I have a drive on my desktop name 'Volume 26G' (I installed in French) and it can be mount because $MFT has invalid magic...

I know it's because he try to mount /dev/sda1 and it's one of my drive on the RAID0. I know if I want to access my other partition (like windows partition) I need to mount /dev/mapper/isw... and it's all going well if try,

But my question is : how I remove the 'Volume 26G' of my desktop?

just for information: /dev/sda1 is not in the /etc/fstab list

Thx

---

### Post by Partyboi2 on 2008-02-04
Is this what you are wanting to do?
[http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/](http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/)

---

### Post by sylver1109 on 2008-02-04
It's realy close. but i have install Xubuntu.. soo the command  gconf-editor dos not exist. if you have the same tricks for Xfce it could be grate. but I was loking for a more 'all version' solution... I continue to look, thx.

---

