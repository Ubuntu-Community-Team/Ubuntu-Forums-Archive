---
title: "Username and password unknown"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by Lordship on 2007-11-10
I'm having trouble, can anyone help?:confused: I have taken the following steps to reset my password but am still unable to login

cd /home
ls
passwd 
<new password>
reboot

---

### Post by Nano Geek on 2007-11-10
Try this. It should work for you. 

If you can, it is preferable to just boot using a backup kernel or into recovery mode and update from there. If you can't:
[LIST]
[*] Boot up a live cd, or separate Linux install
[*] Mount your Hardy drive somewhere (replace **** with name of drive, e.g. hda1 or sda2 etc.) 	Code:
 	sudo mkdir /media/ubuntu
sudo mount /dev/**** /media/ubuntu 
[*] chroot into your Hardy drive
 	Code:
 	sudo chroot /media/ubuntu su 
[/LIST]
Then run  **passwd**, follow the instructions, then you're done.

Based off a post by PriceChild.

---

### Post by Lordship on 2007-11-12
It's on a separate PC so I don't mind performing a new Ubuntu install but it won't boot up a live CD from start.

---

