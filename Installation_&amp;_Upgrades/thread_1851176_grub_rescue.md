---
title: "grub rescue"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by jiffipop on 2011-09-27
I NEED HELP 

i think when i left windows on last night with a partition manager open that my cat slept on the keybord and erased the partition containing ubuntu now i dont know what to do

the only way i can use the computer is if i boot ubuntu via disk and click try if i try to install it again it stalls 

i cannot boot to windows xp any more as it comes up grubrescue> 

help please before my wife kills me 

she didnt want my playing with ubuntu lol

---

### Post by YesWeCan on 2011-09-27
Darned cat! :p
Try restoring the standard MBR boot code. That'll probably get XP booting again.
Using live CD:
[COLOR="DarkSlateBlue"]sudo fdisk -lu[/COLOR]
check the name of your hard drive. It is probably sda if you only have one, them use it in:
[COLOR="DarkSlateBlue"]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]

---

