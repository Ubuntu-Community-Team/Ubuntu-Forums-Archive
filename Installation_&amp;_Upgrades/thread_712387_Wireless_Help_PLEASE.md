---
title: "Wireless Help PLEASE"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by SurferGTO on 2008-03-01
I'm pretty good at figuring this sort of stuff out but im about ready to throw things. ive had to reinstall ubuntu gutsy like 3 times for different reasons. it took me forever to figure out how to get my graphics card to work but the forums are awesome and i now can do it with my eyes closed. the install itself was a bit of a pain for stupid reasons (do to the low graphics mode i couldnt see the foreward buttons on the bottom of the screen to continue the install... that took me a while hahaha)

anyway now im trying to install ndiswrapper and i just cant freakin grasp what to do. ive downloaded the latest version (ndiswrapper 1.52) however most of the installation guides tell me to do things like move it into the usr directory, which it wont let me do. im sure this is pretty easy however my head is about to explode so a quick easy to understand answer would go a long way for my sanity. yes i have searched, ive tried multiple ways of doing this nothing seems to be working. please note im very very new to linux so mostly every step needs an explanation. dont just say stuff like "go edit this yada yada yada" because i really wont know what that means.

the initial problem is that when trying to connect to my home wireless network, ubuntu doesnt find ANY wireless networks in my area. Im sure its a driver problem and im sure i need ndiswrapper.

info: im using an HP Pavilion DV2000

---

### Post by Pumalite on 2008-03-01
There is no 'easy' way. You just have to follow the guides. Post exact problems that you encounter.

---

### Post by SurferGTO on 2008-03-01
i know.. im sorry i should have been more specific. im just frustrated haha. well ill go off the ndiswrapper site installation guide. basically im assuming when it tells me a directory has been created its been in the system file but my folder is on the desktop and i cant creat or move the ndiswrapper folder to the system file. so anything after that really doesnt work. does that make sense?

---

### Post by Pumalite on 2008-03-01
Maybe this helps:
cd ~/Desktop

---

### Post by SurferGTO on 2008-03-01
eh... nope not really... what am i supposed to do with that. really, i am a complete noob. kiddy gloves here.

---

### Post by Pumalite on 2008-03-01
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by SurferGTO on 2008-03-03
Ive seen posts about versions coming with ndiswrapper installed. does gutsy already have it?

---

### Post by SurferGTO on 2008-03-03
there is a point in the isntall guide that says to go into the ndiswrapper directory than into the debian directory. i have no such directory.

---

### Post by SurferGTO on 2008-03-03
I get to the point in one guide that tells me if ive had no luck to remove the stock ndiswrapper, than compile and install a new ndiswrapper, which all goes well. the next step says to redo some changes made by the setup by running

cd ~/bcm43xx
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo modprobe ndiswrapper
sudo ndiswrapper -m

when i do that i get Could not open location 'file:///cd ~/bcm43xx%0Asudo ndiswrapper -i bcmwl5.inf%0Andiswrapper -l%0Asudo modprobe ndiswrapper%0Asudo ndiswrapper -m' the location or file could not be found. 

im basically just running step by step what they say to do but they just dont seem to be working.

---

### Post by SurferGTO on 2008-03-03
bump.. i want my wireless!! Still cant figure this out

---

### Post by SurferGTO on 2008-03-03
I attempted to use an installer, which says it downloaded the broadcom drivers however they are not in my driver list... if it helps here is what hp.com has listed as my exact driver on their download page

"This package contains drivers for the supported Broadcom Wireless LAN adapters in the supported notebook models and operating systems. This driver supports 802.11i/WPA2 for a/b/g and certain b/g WLAN cards. For other cards, it provides Wi-Fi protected access (WPA) support. This driver also provides support for "125 High Speed Mode" for notebooks with Broadcom 802.11g and 802.11a/b/g cards that support "125M High Speed Mode."

 

Fixes 

- Fixes issue where the wireless LAN LED is slow to light up after the notebook resumes from Suspend mode. - Fixes intermittent issue that occurs when connecting to access points configured for WPA2/Pre-Shared Key.

 

Enhancements 

- Provides the Broadcom 4.150.22.0 driver. - Reduces processor utilization during scans."

---

### Post by SurferGTO on 2008-03-03
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

I followed that to the T however when I get to step 6 i still have nothing listed... i got no errors and apparently everythging went smooth... i dont get it

---

### Post by Pumalite on 2008-03-03
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by SurferGTO on 2008-03-03
Still no sucess with any of those guides either. the driver is installed, and as i said i never get any error messages or anything, however the iwconfig command shows i have no wireless connections. the driver shows up in the wireless windows drivers app, but theres nothing listed in the restricted drivers manager. i havent really had  aproblem with installing either ndiswrapper or the driver itself, it just simpley isnt recognizing it im assuming.

---

### Post by StaindFaith on 2008-03-07
I know how you feel with the extreme frustration about the wireless. In fact, I think mine might be a bit worse. I'm trying to install Ubuntu over the internet and when I get to the point that the setup starts configuring my network interface, it claims it's failed. So I tried another way, got a bcm43xx_microcode5.fw issue, and now I'm just getting sad. I'd try one of the alternative discs, or even just running an actual ethernet cable to the system, but I've got issues there:
A) No where to plug my ethernet cable into (the wireless here is free, but for some reason they've neglected to include actual highspeed ports (I'm in a hotel))
B) I'm out of blank CDs (My hotel is in Mexico)
Any ideas that you could provide would be awesome.
Oh, by the way, I'm running an Acer Extensa 4420-5874:
3Gb DDR2
Athlon 64 x2 TK-55 (1.8Ghz 2x256Kb L2 cache)
ATI Radeon Xpress 1250
Oh, and my Wireless adapter is Broadcom. xD (Lots of issues with them, apparently)

---

### Post by uberlube on 2008-03-07
try the how to in my sig. hope it helps :)

---

