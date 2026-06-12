---
title: "bootloader problems"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by fireurza on 2012-07-12
im installing using the alternate method and for some reason thats the only one ive been able to even load. i install just fine set up my password and username and everything is fine until it gets to the bootloader install then it fails... i try a few more times to install grub and still fail... so i continue without and on restart go into the repair broken system and install grub from there... now i set up a password and username but when it restarts again and i select ubuntu 12.04 it tells me my login is incorrect when im entering what i did when i created it

---

### Post by darkod on 2012-07-12
Are you installing on raid?

Why are you creating another username and password after you went in to install grub2. You only create one, first user during the install. Later you don't need to create one. First make the system boot fully, and then you can continue creating new users.

You can try using boot-repair and see if that helps.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by fireurza on 2012-07-12
no they hard drives are not in raid... im not creating a new user or anything i went through the entire process in the alternate install up to install grub and grub failed to install. i went to the terminal in the live cd in try xubuntu and followed the steps i looked up to install grub2 with apt-get. after that it just loads to the grub2 screen and has only "grub >" displaying cant select disk... second time i tried i went into the rescue mode on the alternate disk and installed grub through that and go to log in and my username and password that i setup during the installation does not work and when i go to look it up using 
cd /home/
ls
there is no username displayed it just goes straight to the next line asking for a command

---

### Post by drs305 on 2012-07-12
If you can see the GRUB menu can you boot into the Recovery mode? If so, you can try to add your user via the terminal:
```
adduser *username*
```

---

### Post by fireurza on 2012-07-12
ill try that i can go into the recovery mode and then root...

---

