---
title: "Gutsy livecd boots blank screen w/ G92 8800gts"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by [MoG] Didier on 2008-01-16
Hello,

      I've just built my system and I need to boot from the 7.10 livecd, however after attempting to start the livecd from the options menu the splash screen loads, then drops me off at a blank screen. Heres my system:

Intel q6600 2.4ghz CPU, MSI p6n Diamond MOBO, Corsair XMS-2 4gb RAM, 2x GeForce G92 8800 gts 512 (currently with SLI connector on)

     Whats important to understand is that I'm very new to using the Ubuntu command line and issuing commands with it. I don't even really know how to get there from the livecd. I've gotten it by chance after hitting ctrl+alt+F1 at some point while the livecd's trying to load. If you please, could you be very specific in your suggestions, and try to go step by step as much as possible? It would help me understand what's going on better. Thanks.
     That said, I've been to the other posts suggesting that I add or delete boot parameters at the end of the command displayed when I hit f6 at the options menu and none of that has worked. I've also tried running the xorg reconfiguration wizard once I got to the console. I'm not sure if that worked or not because once back in the console I don't know the command to boot Ubuntu. I think it's a xorg configuration or driver issue, but I wouldn't know the first way to tackle it after what I've tried.
     It's very important that I be able to boot the livecd. Using the alternate install disc isn't really an option for me, because I have to use the livecd to move data off of the HDD that I intend to format/install ubuntu onto, and onto another HDD.
 
Can anyone help steer me in the right direction? Thanks, it's much appreciated. 

-Devin N.

---

### Post by Partyboi2 on 2008-01-16
you could try going to the terminal Ctrl+Alt+F1-F6, reconfigure xserver with
```
sudo dpkg-reconfigure xserver-xorg
```
choose the nv driver and work your way through the questions when you have finished 
type
```
startx
```
if that do not work then instead of choosing nv choose vesa instead. Hopefully this will get you to a working desktop
If that does not work you could press F6 at the main menu and remove quiet and that should show you where your system is stopping at.

---

### Post by [MoG] Didier on 2008-01-16
I've already tried both of these, none of them work, though now i know how to get into the terminal. When I use startx the system tries to load but hangs and then fails.

---

