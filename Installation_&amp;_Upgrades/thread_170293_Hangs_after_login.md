---
title: "Hangs after login"
date: 2006-05-04
forum: Installation &amp; Upgrades
---

### Post by Tuffy on 2006-05-04
When im trying to login to the OS the screen just turns completly brown. I can move the mouse around, but thats it. Is there anyway to fix this? Im running a dual-boot with windows xp, and tried to install Ubuntu on 50 GB of unallocated space.

Thanks in advance
~Tuffy

---

### Post by riverfr0zen on 2006-05-04
Hey Tuffy - I had possibly the same problem recently, after experiencing some inode issues with my disk, so this may help. 

I haven't had time to figure out the permanent solution, but it seems to be an issue with localhost not getting set up properly. So what I did is, log into the failsafe terminal, then

sudo /etc/init.d/networking restart

Then, exit the terminal and try to login to the regular gnome desktop. Hopefully this helps. Also, you can look in ~/.xession-errors for possible clues as to what is going wrong.

---

### Post by Tuffy on 2006-05-06
uhm.. ok I will try that, I was recently too adventorous while installing linux so i accidentaly overwritten a partition that i wasnt supposed to... so ive reinstalled windows and made a backup with acronis. so It may take awhile before i can test it..


Anyway thanks for the reply

---

