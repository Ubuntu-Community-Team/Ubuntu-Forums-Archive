---
title: "Fresh install, reboot then find no bootable media"
date: 2020-12-10
forum: Installation &amp; Upgrades
---

### Post by hitechnology on 2020-12-10
Hi all.

Looking for some help. I did a fresh install using a USB stick and Rufus and ubuntu-20.04.1-desktop-amd64.

 Install went well. Updates were preformed. Kodi installed and setup. I moved from my test bench and into my equipment rack, obviously removing power to do so. Now when I turn on I get the error saying no bootable media found. 

I checked in the BIOS and its pointed to the SSD that's installed. No other drives are installed. 

This same thing happened when I tried to install LibreELEC. For years it ran OpeneELEC and I broke it trying to update to LibreELEC. 

PC is a Zotec ZBoxnano-ID63. I realize its older but its used only for playing movies using Kodi from my server. 

SSD Mushkin ECO 2 60GB MKNSSDEC60GB

Any thoughts are greatly appreciated.

---

### Post by hitechnology on 2020-12-10
Did some more testing. I removed the SSD and plugged it into my Windows PC with a dock. It was recognized. Then placed it back into the Zotec and it fired right up. I can restart just fine but when i power off or pull power it doesn't find the OS and displays the no bootable media error. Plug back into Windows PC dock and it works again.

---

### Post by ubfan1 on 2020-12-10
Maybe check for any firmware updates offered for the SSD? And for your motherboard too.

---

### Post by hitechnology on 2020-12-10
I will try that. Not sure how to do it in Ubuntu but will try a google search. 

Don't know much of anything about Ubuntu.

---

### Post by grahammechanical on 2020-12-10
It is just a thought, but is the CMOS battery holding its charge? With the power supply connected to the mains electricity the CMOS battery stays charged. Disconnect the power from the mains electricity, now does the CMOS battery stay charged or does it lose its charge.

Regards

---

### Post by hitechnology on 2020-12-10
Well tried updating BIOS and could not figure how to do it. 

Was speaking with a old friend that is knowledgeable in computers to see if he had any ideas and for fun, I unplugged the PC and plugged back in and it booted fine! Have turned it off severaral times and unplugged several times and its working fine now. Its inside my rack now and working well. Just doing some tweaks to Ubuntu to make Kodi run right. 

Have no idea what it was. 

Thanks for the help. Much appreciated.

---

