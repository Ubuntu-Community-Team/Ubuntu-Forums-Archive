---
title: "X crashes/doesn't work."
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by bugz0r on 2006-10-26
I followed everything at this site([https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)) and when I restart the computer X crashes/doesn't work. I have ATI Radeon X300 video card and I believe there was something about the "vesa" driver.

---

### Post by KaeseEs on 2006-10-26
I also am having issues with X after the upgrade.  At first attempt, X wouldn't work at all.  After reconfiguring xserver-xorg, I got X to at least run, but only at 640x480@61Hz.  Oddly, this refresh rate wasn't even available pre-upgrade.  I'm on a Thinkpad T60 using and ATI x1400.  The default rez before was 1400x1050.

---

### Post by Binary Jay on 2006-10-26
Restore the working xorg.conf you had backed up... you DO have a working backup of xorg.conf right?

---

### Post by mwolfe on 2006-10-26
I had the same problem.. restoring to a previous xorg.conf file fixed it for me.. unfortunately xgl didnt work but i didnt think it would.. I am trying to start over with doing a clean install on another partition however and having nothing but problems.. it seems like the installer and all that keeps getting worse in ubuntu.. i dont understand.. i had to switch my monitor to regular vga instead of dvi or i couldnt see anything.. and then that install didnt work so i tried the regular ubuntu desktop install cd and it won't even boot into X, it gives me an error message.. i'm using an ati x600. Its odd because i've got a 2 year old knoppix disk that will boot this stuff without any problems. I love ubuntu but its still trailing in some aspects.

---

### Post by rfruth on 2006-10-27
Same problem here, my mini tower has a X300 card & I have no b/u of  my xorg.conf file, can someone (anyone) give me theirs (open GL is fine) please, I'm dead in the water right now (have a bootable Dapper CD)   :rolleyes:

---

### Post by ilushkin on 2006-10-27
same problem with ati mobility 1300

---

### Post by DigitalDuality on 2006-10-27
same here, Nvidia 5500

---

### Post by acerlinux on 2006-10-27
for those guys who got the problem please try:

sudo aptitude install xserver-xorg-video-all

or you know your video card type that you could install the corresponding driver only. then change the xorg.conf to use that driver. unfortunately, the  3D desktop will not work without the 3d accelaration. but at least you may use the x server firstly, then solve another problem.

hope this helps. it does take effects for my old laptop with ATI M 7500.

If here some one knows how to install an open source driver for my old ATI card, please let me know.

---

### Post by buddachile on 2006-10-27
*...then change the xorg.conf to use that driver...*

how do you configure xorg.conf to use the driver in question?

---

### Post by rfruth on 2006-10-27
Thanks much, X is now running for me !
to set xorg.conf to its defaults run   sudo dpkg-reconfigure -phigh xserver-xorg  ((per the xorg.conf file itself))

---

### Post by KaeseEs on 2006-10-27
Restoring each of several backups of xorg.conf didn't fix anything for me - oddly, some instituted a weird diagonal line transform of my screen.  What did fix the problem was symlinking /bin/sh to bash, then building a deb from ATI's proprietary driver, installing it, and relinking /bin/sh to dash.  GLX and acceleration still don't work (though the system thinks they do - apps that require them run, but at speeds which make it obvious processing isn't being done in hardware), whereas prior to the upgrade they worked when X was run from within GDM, but not when run via startx/xinit.  I'm just glad I can fire up Opera and VLC now.

---

