---
title: "Upgrade : big trouble at boot"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by dam973 on 2013-07-10
Hello everyone,
everything was working fine until yesterday when my xubuntu 13.04 updated and downloaded a new image 3.8.0-26 and a bunch of other stuff. Today when i star my computer normally it get stuck. I can start it using the repair mode and after a slow start with the console , i say start normally , it send me to console , i type startx and i can start (after cliking an error message saying "gnome session error").
The small problem is i can't access my other disks , fdisk -l detect theml but i can't mount them...
You have some help? :(
Thanks

---

### Post by dino99 on 2013-07-10
each kernel installation needs: 2 headers + 2 images
check that is true about the latest kernel installed

can you boot normally with an older kernel ?

---

### Post by dam973 on 2013-07-10
With older kernels(35)  i got the same results. 
I post you the installation list of the update

---

### Post by dam973 on 2013-07-10
Please...Help! :(

---

### Post by dam973 on 2013-07-10
Now i think i figured out what is wrong . Ubuntu at boot has big trouble detecting my Hard drives . it says dev/sda timeout something like that. The  it dont boot directly to the desktop but i have to start xfce from command line. But it works. But then it doesnt detect my disks. But i can mount thme manually from the command line. What is going on? :(

---

### Post by dam973 on 2013-07-10
Ok and now i have this big letters when i plug an hdmi screen andi didnt have that before. And i can't start windows in my dual boot because it seems to have damaged that too...

---

### Post by dam973 on 2013-07-10
Great and my sound is broken too. Well i think i just gotta reinstall .

---

### Post by dam973 on 2013-07-11
Ok thank you all for your help . :s

---

### Post by NM5TF on 2013-07-11
have you tried using a "boot repair cd"???

do that before a reinstall...it may fix it...

search the forum...it's everywhere....

---

