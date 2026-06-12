---
title: "Minimal install won't work."
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by Irongolem on 2010-06-04
I have tried burning every version of the mini.iso on CD and USB keys and none of them work. They get up to the point just before the language select and then the screen goes black and nothing else.

Everything works in a virtual machine on my laptop, but the CDs and USBs just don't work.

Does anyone know what might be causing this?

---

### Post by sidzen on 2010-06-04
You may wish to verify the MD5 on the CD iso -- it could be a bad burn.

1)  Find the device ID of your cdrom or cd-rw, in termal or console (Ctrl-Alt-F1thru6;  Ctrl-Alt-F7 to get back to the GUI)
[PHP]wodim --devices[/PHP]It'll probably return something like */dev/hdc* or /dev/sr0
Put your CD into the drive -- don't mount it -- while in the CLI (command line interface) and type
[PHP]md5sum /dev/hdc[/PHP]  (for the first example)
Wait
It'll either return the md5 sum (good) or something saying "Input/output error" (bad)

Passing on what I've learned from secipolla, to burn an iso from the CLI, be in the directory of the ISO and 
[PHP]wodim -sao speed=4 [name of iso file][/PHP]Without the brackets. 
Cheers/Salud/Skoal! & Stay Pane-free!

---

### Post by Irongolem on 2010-06-05
I verified the CDs and they all burned correctly, so that's not it. Has to be another problem.

---

### Post by sidzen on 2010-06-05
What is your system?  What was on your hard drive previously?  How did you prepare the HD?  Need more info, Irongolem.

---

### Post by Irongolem on 2010-06-06
> **sidzen said:**
> What is your system?  What was on your hard drive previously?  How did you prepare the HD?  Need more info, Irongolem.

System: HP 6910p laptop - 2ghz C2D, 2 gigs of DDR2,  Intel GMA X3100 integrated graphics, 250 gig 5400 RPM hard drive.

Hard drive has only had Ubuntu 10.04 on it, and it was prepared via the auto-partition feature of the Ubuntu live CD install.

The thing I find odd is that I get this black screen problem with the minimal install, alternative install, and server install, but not the desktop install. I tried them on my girlfriends computer and they all work fine, but on my laptop they just won't work.

---

### Post by Irongolem on 2010-06-07
No one have any ideas on this one?

---

### Post by sidzen on 2010-06-08
Sorry to do this, but I don't like HPs -- suggest you go to [http://www.linlap.com/wiki/hp-compaq+6910p](http://www.linlap.com/wiki/hp-compaq+6910p) and maybe [https://help.ubuntu.com](https://help.ubuntu.com), in that order.  

Best wishes, Irongolem!

---

