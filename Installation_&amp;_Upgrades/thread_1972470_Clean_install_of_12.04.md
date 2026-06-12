---
title: "Clean install of 12.04"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by dfrandin on 2012-05-03
I've just tried two clean installs of 12.04 (Desktop/64bit). Both were on the same machine/same hardware (two different harddrives). Both installs went error-free, but after completion, the onboard ethernet connection shows up in network manager, as does the installed Sprint GSM broadband modem, but the installed Broadcom BCM4311 802.11.b/g WLAN does not, ie: No "wireless network" entries. The "hardware drivers" shows that the Broadcom STA wireless "blob" driver is loaded and active. lspci also shows the card correctly. lsmod shows the wl module loaded. 

The second install I added the MATE repo and installed MATE (I detest Unity/Gnome3), and MATE's network manager doesn't show any wireless entries either. 

The Dell laptop these two installs were done on, normally runs Ubuntu 10.04/64bit flawlessly with the same hardware that seems to be borked on 12.04.. Since I only upgrade my systems on LTS versions, and then only do clean installs of the new OS version, then install apps via markings file from the old LTS install, I'd hoped this was going to be a painless install like I've experienced with 8.04 and 10.04.. I sure hope Ubuntu isn't regressing from the excellent progress it's made in the last several years.. apart from Unity, that is... What am I missing??

Dave

---

### Post by bayouoldguy on 2012-05-03
Broadcom Wireless problems....look @ this thread: [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868).( Read all ! ). Most of us users w/Broadcom wireless have had to install the old B43xx drivers to get working...."G" ( the supplied "STA" driver set still has some
issues w/ old Broadcom B4311 ,etc. cards ).

---

### Post by dfrandin on 2012-05-04
ok..thank you. will read the thread given.. I gotta ask though, I use the STA driver on the same machine under 10.04 and it works fine there.. Has 12.04 changed for the worse on Broadcom support??

---

### Post by bayouoldguy on 2012-05-04
do not know that answer, had to use the old  B43xx driver in a Dell D620 with BCM4311 card to connect to my Linksys wireless. Ran the 12.04LTS on a USB stick ( Live run, not install), & had to hardwire & download the old driver & install info. Ref:http://ubuntuforums.org/showthread.php?t=1807243....."G"

---

