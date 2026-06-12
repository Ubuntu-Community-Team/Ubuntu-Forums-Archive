---
title: "hang up on the install splash screen"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by buttpaste on 2011-11-07
I have a Toshiba Satellite c655d-s5126 I had windows 7 and Ubuntu dual booting no problem made the stupid mistake of installing windows 8 dev preview wiping out both oinstalls. Trying to go back now to the dual boot have windows 7 up and running no problem and a 100gb partition waiting for ubuntu to be installed on it but when I use unetbootin to make a live usb stick and try and boot from it I get stuck at a splash screen that says ubuntu with 4 little dots they cycle from white to orange a few times the access light blinks for a little while then just stops the four dots stay orange and nothing I have to hard reboot the computer.

---

### Post by fantab on 2011-11-07
> **buttpaste said:**
> I have a Toshiba Satellite c655d-s5126 I had windows 7 and Ubuntu dual booting no problem made the stupid mistake of installing windows 8 dev preview wiping out both oinstalls. Trying to go back now to the dual boot have windows 7 up and running no problem and a 100gb partition waiting for ubuntu to be installed on it but when I use unetbootin to make a live usb stick and try and boot from it I get stuck at a splash screen that says ubuntu with 4 little dots they cycle from white to orange a few times the access light blinks for a little while then just stops the four dots stay orange and nothing I have to hard reboot the computer.

Ok... seems like you may have to remake the usb stick, as it may have not been done properly.

Write Ubuntu to USB again and retry. 

Let us know if you still have problems after doing the above.

---

### Post by buttpaste on 2011-11-07
Yeah same issues I have reformatted the usb drive several times and tried Fedora, Ubunutu, Kubunutu, and Linux Mint. all with the same results.

---

### Post by buttpaste on 2011-11-07
Oh and I was able to get in to the install screen with a Ubuntu 10.04 CD that I burned but it didn't see my wireless or network card so not Ethernet or Wifi access.

---

### Post by fantab on 2011-11-08
> **buttpaste said:**
> Oh and I was able to get in to the install screen with a Ubuntu 10.04 CD that I burned but **it didn't see my wireless or network card so not Ethernet or Wifi access.**

Then instead of USB try Ubuntu Oneiric liveCD, there could be something wrong with either with you USB stick or the way it is read. By the way have you adjusted your BIOS to boot USB first?

You shouldn't mind much if your installation does not see any networking during Installation... you can always update after you have installed your distro.

My Ethernet is never ever is detected by the Installation Media during install... but after installation it just works.

---

### Post by buttpaste on 2011-11-08
Installed from a 10.04 USB install no wireless no Ethernet nothing.... I don't get it nothing changed from when the dual boot was working.

---

### Post by buttpaste on 2011-11-09
[http://ubuntuforums.org/showpost.php?p=11185273&postcount=26](http://ubuntuforums.org/showpost.php?p=11185273&postcount=26)

This post solved the issue I was having.  In short changing the BIOS boot order solved the hangup issues. I now have a dual booting computer again :)

---

