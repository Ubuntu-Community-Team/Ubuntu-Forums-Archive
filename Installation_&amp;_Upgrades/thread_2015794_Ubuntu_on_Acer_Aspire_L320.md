---
title: "Ubuntu on Acer Aspire L320"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by ishueli on 2012-07-03
Hello Everyone,

I would be interested to know if anyone has installed Ubuntu on Acer Aspire L320. I am trying to install Ubuntu 12.04 on this PC but the installation stalls. The error seems to be with the wireless modem. It asks me to go to website 'https://wireless.kernel.org' site and download the correct firmware. Unfortunately I am not an expert in these things so would appreciate if someone can assist me in this installation.
I have another HDD with pre-installed Ubuntu 12.04 (done on Dell PC) which I connected to PC and rebooted. Ubuntu starts without any problems but wireless does not work. The error being 'firmware missing'.
Some meaningful help will be most welcome.

Regards

---

### Post by msammels on 2012-07-04
Ouch,

I've never heard of this error before. Are you trying to connect using the Network Manager (top right hand corner)?

---

### Post by ishueli on 2012-07-04
No...I inserted Ubuntu installer CD and started the installation. During installation when screen appears with ubuntu writen on it, the dots below would stop filling at some stage. At this time if youi press up or down arrow key you will see what the installer is doing in the background. I Picked the error from what was mentioned on the screen. Will try to post the error soon.
 
The system comes to a complete stop. You have to hard shut down.
 
Somehow on the external HDD I have Ubuntu installed and managed to boot the disk on the same computer. In one of the google searched I found a command to replace the driver from Broadcom BCM 4318 network adapter and the wireless started working fine. I somehow do not remember what exact command I run but it did the trick.
 
However I cant install Ubuntu on the internal HDD of Acer Aspire L320.

---

### Post by msammels on 2012-07-04
OK, have you tried to partition it manually, using gparted?

---

### Post by ishueli on 2012-07-04
This is the error I get - 
 
[FONT=Courier New]b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all the instruction on this website.[/FONT]

I found an article on web on the same problem faced on HP laptop. Wil try this out to see if it helps on Acer Aspire L320.
 
[http://clusterbleep.net/blog/2012/05/09/ubuntu-12-04-splash-screen-lockup-with-livecd/](http://clusterbleep.net/blog/2012/05/09/ubuntu-12-04-splash-screen-lockup-with-livecd/)

---

