---
title: "Gutsy failed to install in graphical mode"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by retrow on 2007-10-18
I downloaded the i386 torrent and burnt a install disk about 2 hours ago. When I booted from the disk, the install screen at the beginning didn't give me an option to 'Install' like it did for Fiesty. The only option I had was install in text mode or install in command line mode apart from check disk, memory test etc.

I selected install with text mode. Everything went fine until it started searching for 'apt'. I guess it was trying to connect to the internet and get packages, but it wasn't able to configure my network adapter. The process got stuck at 40% and didn't budge for 40 minutes. There was no option to skip that step, so all I could do was reboot. I tried installing it again, but again it failed to install in graphical mode, and while installing in text mode, it just halted at 40% on the 'apt' screen ](*,)

I am using a Dell Inspiron 530s, with Intel 95x11 graphics accelerator. Anyone had a similar problem trying to install Gutsy?

---

### Post by coarse.sand on 2007-10-18
Hey retrow, I'm having a similar problem. I have a Compaq R4000 with the Broadcom wireless adaptor, meaning I need the bcm43xx driver for wireless connection. When I put the Ubuntu 7.10 install disk in, I can select "Start or Install Ubuntu", which seems to be fine but eventually has problems with the bxm43xx "microcode" and sends me to a CLI as ubuntu@ubuntu, instead of the standard LiveCD Desktop I get when I installed 7.04.

P.S. It sounds like you may have downloaded the Alternative .iso? That has a text only install as far as I know, and it may be much smaller so it's trying to download its required files, thus freezing since you have no internet connection.

---

### Post by shad0w_walker on 2007-10-18
This sounds like you have picked up the alternative ISO somehow, that comes with the text based installer instead of a LiveCD option.

coarse.sand:

Is the WiFi a separate card/USB device? If it is try unplugging it whilst you install. I had some issues with BCM43xx stuff. When you have the system installed you should be able to plug it back in and install the driver as normal.

---

### Post by coarse.sand on 2007-10-18
Unfortunately it isn't a removable card. When I was installing 7.04 I had no problems with it, i would just grab an ethernet connection and install the driver with ndiswrapper after 7.04l had completed. This time around it does the standard LiveCD boot up but sends me to a CLI, and every minute or so sends me a message about bcm microcode either missing or failed.

I'm going to go hook the computer up to an ethernet connection now and see if that does anything for the install.

---

### Post by retrow on 2007-10-18
My installation went well with the alternate-i386. The problem I was having with installation getting stuck at 40% when it was "configuring apts" was solved by patience. I tried the same thing again, but this time when it got stuck at the 40% mark, I just left it alone and then after about an hour, it had completed the installation and was asking for inputs on migration of accounts from XP.

Upon restart when I selected Ubuntu 7.10 from GRUB, my screen went totally blank and my monitor displayed "This video resolution is not supported" and that freaked the crap out of me. But then I remembered the ctrl-alt-F1 I'd used earlier, which reverted the system back to text mode boot-up, and eventually it brought me to the login screen. After that it was all smooth sailing.

Another happy Gutsy user \\:D/

---

