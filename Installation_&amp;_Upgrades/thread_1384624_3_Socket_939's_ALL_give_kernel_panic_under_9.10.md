---
title: "3 Socket 939's ALL give kernel panic under 9.10"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Jaxco on 2010-01-18
All X2's - same result with an Opteron Dual core as well, just decided to try it.

All Asus A8V Deluxe Boards

Various brands/amounts of RAM

2 connect wireless, 1 by LAN

Even attempting shut-off or updates or anything that requires admin permission causes lock-up.  Browsing generally no problem.

Often it locks up with no activity (no specific time interval)

ALL run flawlessly under 9.04

---

### Post by Jaxco on 2010-01-20
lol no guesses?

---

### Post by Jaxco on 2010-01-27
Guess I should just be content with 9.04

---

### Post by Jaxco on 2010-02-19
Still no clues?

---

### Post by chris_lukehart on 2010-02-19
before you install or live boot menu 

Steps:

1)press 'F6 key' 

2)check these settings 
        A)nolapic
        B)noapic

3) install ubuntu :popcorn:
-----------------------------------------
I have a socket 939 that is how i installed ubuntu but i could not get usb to work in linux?

---

### Post by chris_lukehart on 2010-02-20
after installation of 9.10 it does not apply the "nolapic or noapic" kernel options.

so what i did was:

1)press shift before booting it should give you grub2 loader

2)edit the kernel form grub2 to apply the kernel options  

3)press enter

4)edit the /etc/default/grub to apply the kernel options permently

5) update-grub ; reboot 

6) it should work and boot :popcorn:
That is how i booted in 9.10 after installation. 
---------------------------------------------------

usb does does work on 939 amd computer but it does work in windows xp

---

### Post by chris_lukehart on 2010-02-20
I realized my motherboard is by ASUS as well.  
It a hp pavilion a1230n computer with ati 200 integrated graphics. 
ATI Technologies Inc IXP SB400 SMBus Controller (rev 11) does not seems work in linux
Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller

---

### Post by Jaxco on 2010-08-03
I guess I am stuck with 9.04, I am still having major problems with this issue

---

### Post by Jaxco on 2010-08-03
I have been using ubuntu since 6.X - this is the first time it has not been backwards compatible.

---

### Post by Mark Phelps on 2010-08-03
Sorry I don't have a solution ... but I'm running an AMD 939 socket ASUS board (A8N32-SLI deluxe) and have had NO problems with it installing, booting, or running 9.10 -- but then, I chose the 32-bit version.

It's been a while, but I seem to remember trying the 64-bit version of 9.10 and I couldn't get it to boot.

---

