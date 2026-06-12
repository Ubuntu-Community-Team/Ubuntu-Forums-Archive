---
title: "Ubuntu wont start after SuSE upgrade"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by Eriksmits596 on 2007-10-06
Hi!
For a few weeks ago I installed SuSE 10.2 on a Tri boot configuration with Ubuntu and Windows. It worked amazing:) But now when the SuSE 10.3 was released, I did an update. So now when I have 10.3 installed, ubuntu fails to start...
Error message:
> root UUID=e9f82a3a-b5e4-4d0c-96c8-351f52bb882e ro
Error 23: Error while parsing number
Press any key...
[SIZE="4"]**Can anyone help me? **[/SIZE]  
Thanks:KS /Erik

---

### Post by Pumalite on 2007-10-06
From whomever owns the Grub, post:
sudo fdisk -lu
cat /etc/fstab
blkid
cat /boot/grub/menu.lst

---

### Post by Eriksmits596 on 2007-10-06
what do you mean with "From whomever owns the grub"?

---

### Post by Pumalite on 2007-10-06
Better stick an Ubuntu Live CD for blkid.

---

### Post by Eriksmits596 on 2007-10-06
Excuse me, but I dont understand:(

---

### Post by taurus on 2007-10-06
Try replacing the "UUID=e9f82a3a-b5e4-4d0c-96c8-351f52bb882e" for Ubuntu's root partition with the actual device like /dev/sda1, assuming /dev/sda1 is where Ubuntu is.

Now, see if Ubuntu boots this time.

---

### Post by Eriksmits596 on 2007-10-06
thanks

---

### Post by Eriksmits596 on 2007-10-06
now it works! i changed the code to sda2 and it worked:) thanks

---

