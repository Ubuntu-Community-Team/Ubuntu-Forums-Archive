---
title: "Post install no mouse or kbd action"
date: 2014-02-05
forum: Installation &amp; Upgrades
---

### Post by lestoilnr on 2014-02-05
Installed ubuntu 13.01 amd64.  Pc is gateway sx2185 with and E1-2501 duo core cpu with on chip radeonhd 8240.  100G free space was made on C;\ in windows8.  Fast boot and uefi were disabled. Dvd checked ok.  Mouse and keyed worked during install. Install did not ask about mouse or kbd.  Reboot get message starting screen in low graphics mode and mouse/kbd not detected.  What step can I take to fix this?

---

### Post by egeezer on 2014-02-05
Your chip may not be supported yet.  Check this list:
  	 	 	 	    [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3][I][URL="https://help.ubuntu.com/community/RadeonDriver"]https://help.ubuntu.com/community/RadeonDriver


[/URL][/I][/SIZE][/FONT][/COLOR]

---

### Post by lestoilnr on 2014-02-07
resolved by seeing post from december 2013 regarding same pc.  User was told to press 'e' at grub, then scroll down to 'nomodeset'.  That worked of course after rebooting multiple times to get usb keybd working again in win8 and grub. Had also tried ps2 keybd.
Once got to  Ubu desktop, installed grub-customizer.  Then could boot win8 and ubuntu. Thanx.

---

