---
title: "Black Screen when instalation starts"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by Jonas Reiff on 2006-12-17
hi

Right now i got ubuntu 6.10 x86_64 but i want to install the x86 version, becorse this got to many problems. So i have downloadet the i386 version and it boots fine. The start menu shows up, and if i run the cd chek it says that the cd is fine, but if i choose to first option(install ubuntu or somthing like that). There just show up this bar, as it would if it install somthing, but suddenly the screen turn totaly black, and there is nothing i can do, my pc is stil working. 
This also happen if it try the safe mode!
How can i solove this problem, pleas help :)

---

### Post by Jonas Reiff on 2006-12-18
cant any one help mu pleas.

---

### Post by taurus on 2006-12-18
Well, you should use the alternate CD because it works better...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by Jonas Reiff on 2006-12-20
I have downloadet the alternativ, and it installs just fine, but when i try to boot my new system, it just shows a totaly black sreen, as before. The computer is still running. if i choose to boot in recovery mode, its start a console just fine, but if i write ''startx'' then i got the black screen. I think the problem is that ubuntu cannot regonise my moniter. Its a Acer Al1912.
Is there som way i can fix this ?

---

### Post by Jonas Reiff on 2006-12-21
Is there no way too solove this problem, do i realy have to choose another dist ? Even thoug i dont want too, i like ubuntu alot.

---

### Post by taurus on 2006-12-21
Boot into recovery mode and try

```
dpkg-reconfigure -phigh xserver-xorg
startx
```
Is X working now?

---

### Post by RoaringOasis on 2006-12-23
I've encountered the same issue. I attempted the reconfig, but it seems to be (for me) that the autodetect is setting xorg.conf for resolutions wich are outside of my monitors range. I've currently dropped everything down to 800x600 and the xserver is finally coming up for me. I'll post if I discover anything else.

For now, I would suggest that you boot in recovery mode from grub, edit your xorg.conf file and remove the highest resolution, working your way down until X shows up properly.

-RO

---

