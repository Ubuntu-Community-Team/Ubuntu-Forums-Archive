---
title: "Ubuntu 9.1"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by evropej on 2009-12-15
Ok, i have a acronis backup so i can try many options. First, booting from live cd works but its a lot slower than 9.04. Oh, 9.04 ran just fine both 32 and 64 bit. I downloaded both 32 and 64 bit versions of 9.1 and they both hang after install. Windows based install do the same things as cd based installs. The install process starts and i thin finished to when I get to a prompt saying su:grub>. Both versions do this. I am a newbie to ubuntu so i have no idea what commands are need to manually start the os if thats the issue. I just cant believe that this version was deployed this way. Or it just my system? Any help would be appreciated. :D

---

### Post by evropej on 2009-12-15
anyone?
seriously, what is the deal here?

---

### Post by presence1960 on 2009-12-15
if 9.10 is installed: Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

