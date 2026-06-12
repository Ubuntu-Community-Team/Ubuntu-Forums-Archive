---
title: "plz help bcm4311 i read sticky still cant get wireless"
date: 2015-11-09
forum: MINT
---

### Post by tre2012 on 2015-11-09
let me start out by saying i just installed linux mint 17.2, I know its pretty much the same as ubuntu
i did have LM 16 installed prior, and had wifi.. i remember it was a PAIN to get it going when i installed it

so I was hesitant.. but I went for it... but ill just say this... a few things i have tried have made it where my ethernet even goes away.. i have to load up the install usb and do an integrity check then it works again

doing the lspci -v shows that under the broadcom bcm4311 802.11 b/g Wlan rev 01
under kernel driver it says b43-pci-bridge

I do not have the driver installed that it shows under driver manager.. i even followed steps to uninstall and it says it does not exist, or cant be found



when typing sudo apt-get install firmware-b43-installer
it says 
firmware-b43-installer is already the newest version

so its installed... correct?

well.. when i remove the ethernet, it gives me NOTHING about wireless.. only thing it lets me click on is VPN

im about 5 hours deep.. constantly messing with this.. to the point I wish I never upgraded from 16 to 17

is there ANYTHING that could help fix this issue?
it worked under linux mint 16
it shows I have a network card
shows I have the firmware

i will mention that i did install the 64 bit version of linux mint 17.2 xfce


edit

i read something about sudo modprobe b43
to get it working?
i tried that and it says error
../libkmod/libkmod. c: 556 kmod_search moddep() could not open moddep file '/lib/modules/3.15.0-38-generic/modules.dep.bin'

---

### Post by howefield on 2015-11-09
Thread moved to the "*MINT*" forum.

---

### Post by tre2012 on 2015-11-09
i re-installed.. soon as I got to desktop i typed in 
sudo apt-get install firmware-b43-installer

then restarted
then it was working

last time I ran all the updates, downloaded apps I wanted, then tried to get wifi working... so.. if this happens to you.. FIX IT FIRST THING!

---

### Post by ajgreeny on 2015-11-09
Well done!

Please mark as **SOLVED** from the Thread Tools menu up-top.

---

