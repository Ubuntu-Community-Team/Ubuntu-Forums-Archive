---
title: "Logitech DiNovo Edge freezes in logon"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by GG_HTPC on 2007-11-27
i recently upgraded from Fiesty to Gutsy. Everytime I come to the logon window my keyboard freezes up (Bluetooth Logitech DiNovo Edge). I have to power cycle the keyboard to make it work. 

P.S. A Bluetooth icon is shown in my status bar. I dont remember seing it before.

---

### Post by mat-ray on 2008-01-06
Hi,

Did you ever get anywhere with this.  I have the exact same problem - although I've noticed that instead of resetting the keyboard that after about 20s of random clicking/typing the keyboard comes to life - and the little bluetooth icon disappears.

Mat

---

### Post by LarsP on 2008-01-20
I have the same problem(started with gutsy).

---

### Post by GG_HTPC on 2008-04-08
No luck. I just switch the keyboard off/on. I upgraded to 8.04 (Hardy) to test my soundcard but the keyboard still does not work.

---

### Post by iandotcom on 2008-04-08
I got this problem too with my DiNovo setup. If the probs with the one i'm thinking about, it usually starts working again when I take the USB connection for the bluetooth hub out, and put it back in again.

---

### Post by laluz on 2008-04-22
I have just connected the dongle and the whole set up works all the time. The keyboard is the dinovo Edge as well. 
The window manager is compiz with the KDE.

What does not work for me is the volume slide. When I touch it a small window with volume appears, that show 0 to 11%, but the volume is not really affected.
Also the special buttons are not doing anything, but it seems one need to set up them extra.

---

### Post by fraserj on 2008-04-26
I have this exact problem.
Environment: Ubuntu Hardy Heron 8.04 (Release), AMD64 version, brand new default "alternate" AMD64 installation (same issue happened ever since Gutsy, and every alpha, beta, and 8.04RC)

Descr: Logitech DiNovo Bluetooth keyboard/mouse do not work at the login screen.

Workaround: unplug the bluetooth dongle, re-connect the dongle.

Notes: uninstalling bluez-utils worked for Gutsy, I haven't tried it for 8.04 yet. Also, this same exact hardware setup works flawlessly with OpenSUSE 10.3; no bluetooth workaround required. I think bluez has problems with bluetooth hardware.

Any suggestions are welcome. I'm about to uninstall bluez and try again.

-------------------------
UPDATE: I FOUND A SOLUTION!!!!
per [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)
The following command will sort this problem in no time:
Type this command in a terminal:
sudo gedit /etc/default/bluetooth

Then look for the line that says:
HID2HCI_ENABLED=1

and change it to this:
HID2HCI_ENABLED=0

Problem solved.

---

### Post by jrickard on 2008-05-24
I have had the same problem since Gutsy actually.  It takes about 20 seconds of typing when first logging on before the keyboard is found.  Kind of irritating.  This thread has been out there awhile without a fix.

Jack Rickard

---

