---
title: "Feisty FGLRX ATI X850 Xwindow error"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by skilzygw on 2007-04-23
So I followed the steps shown below which got me to see GDM was failing.  The error I get is because the Bus ID is failed to be found.  It originally had PCI:0:3:0 

I have tried all sorts of combinations but a scanpci shows no device found with that ID.

My problem Is the card is an PCI Express ATI X850 but my board is an NV6150 microatx board with onboard graphics.


Why can't it find the right bus id for my PCI Express card?  Does anyone know what those numbers should be?  I am using the DVI out to a widescreen LCD.


Thanks.


1. Boot CD as normal. 
2. Select Safe Graphics Mode
3. Press F4 and Select 1024x768x16
4. Press F6 and remove options for quiet and splash
Eventually you get the X server fail to start and end up in the command prompt
5. Plug in your wired network connection (wireless may work, but didn´t for me since I have intel 4965agn - but that´s a different story) so that it can dhcp to your router
6. sudo apt-get install xorg-driver-fglrx
7. sudo nano /etc/X11/xorg.conf 
8. In Section ¨Device¨ change ¨vesa¨ to ¨fglrx¨
9. CTRL-X to save
10. sudo /etc/init.d/gdm restart

---

### Post by skilzygw on 2007-04-23
Well I ran an LSPCI and it said secondary ATI display 03:0:0

So i added this line into PCI Bus ID then rstarted GDM which ofcourse proceeded to try and load and give me a frozen black screen.  Monitor was getting some sort of signal since it didn't give me the out of sync screen with orange led instead but actually had the green led.

---

