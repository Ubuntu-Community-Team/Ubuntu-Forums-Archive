---
title: "Install Problems"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by 1200max on 2013-03-09
I have got Ubuntu on a live USB and am looking to install it on a spare 80gb hard drive (F:) I have in my computer.  Currently I am running Windows 7 (C/).

I can boot up Ubuntu from the USB and the drive is shown when I open a terminal and type in sudo fdisk -fl the drive is shown as /dev/sdb.  I can open the install page where I can choose what sort of install I want.  I then click on the "something else" and, on the next page it will only give me the choice of /dev/sda which is my main C: drive which has Windows on and won't give me the /dev/sdb drive.

Any advice of what to do is appreciated.

  
Screenshots of what I get: 
[ATTACH=CONFIG]239962[/ATTACH][ATTACH=CONFIG]239963[/ATTACH][ATTACH=CONFIG]239964[/ATTACH][ATTACH=CONFIG]239965[/ATTACH][ATTACH=CONFIG]239966[/ATTACH]

---

### Post by grahammechanical on 2013-03-09
I only have one hard disk. so, although I have done many installs of Ubuntu I have never noticed this issue. May I suggest that you try installing with the Windows hard disk disconnected? This might be a better way to install ubuntu anyway. The Grub boot loader will then be installed into the MBR of sdb and not in the MBR of the Windows drive.

When you reconnect the Windows hard disk use the BIOS to boot into the Ubuntu hard disk and then open a terminal and run

```
sudo update-grub
``` That should detect the Windows OS on the other drive and put an option for it in the Grub boot menu. Regards.

---

### Post by black veils on 2013-03-09
use windows to check if it is a dynamic disk

---

### Post by 1200max on 2013-03-09
> **black veils said:**
> use windows to check if it is a dynamic disk

What is a dynamic disk?

---

### Post by black veils on 2013-03-09
in the Windows disk management tool, you will see if it is basic or dynamic, where it shows **type**. i dont know technically what a dynamic disk is, but you will need to change it to basic.

---

### Post by dongemy on 2013-03-09
me too i like this problem ..  but in third photo i dont have the choose "install Ubuntu inside windows 7 " .. i dont know why ??? plz help

---

### Post by 1200max on 2013-03-10
> **black veils said:**
> in the Windows disk management tool, you will see if it is basic or dynamic, where it shows **type**. i dont know technically what a dynamic disk is, but you will need to change it to basic.

Just checked this and it does show as BASIC.

Any other ideas?

---

