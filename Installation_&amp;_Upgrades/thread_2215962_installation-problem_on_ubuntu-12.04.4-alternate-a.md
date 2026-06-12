---
title: "installation-problem on ubuntu-12.04.4-alternate-amd64"
date: 2014-04-09
forum: Installation &amp; Upgrades
---

### Post by h9-watt1ias-ub on 2014-04-09
Hi,

I'm trying to install via Ubuntu 12.04.4 Alternate 64-Bit-Installation on my new notebook (because i want to use encrypted lvm-volumes). Therefore I donwloaded the image, used the start media creater to copy it on an usb-stick and startet installation. Unfortunatly after "Detecting Network-Devices" installation stops (violett screen with white bar on the very bottom of the screen).

Console/Terminal 4 says:
ieee80211 phy0: brcmsmac: fail to load firmware brcm/bcm43xx-0.fw

This is my notebook Lenovo ThinkPad Edge E535 NZRFPGE.

Thank's,

Matthias

---

### Post by sudodus on 2014-04-09
It seems to be a problem with a driver for a Broadcom device (wifi I guess from the output)

Is it possble to connect the computer via wired internet (ethernet) during the installation?

Is it possible to switch off the wifi during the installation (with a button or via the BIOS/UEFI menu)?

---

### Post by h9-watt1ias-ub on 2014-04-09
Hi, didn't helped (I'm not absoluty sure wether the button really turned of the wifi..)

I tried the usb-stick on another notebook - the next step (that is missing on the new notebook) is the network configuration (DHCP and so on). Is there boot-parameter to stop the installer from using the wifi?

More strange: I tried normal (non-alternate, 64bit) live-ubs-stick and it worked fine ...

---

### Post by sudodus on 2014-04-10
> **h9-watt1ias-ub said:**
> Hi, didn't helped (I'm not absoluty sure wether the button really turned of the wifi..)

I tried the usb-stick on another notebook - the next step (that is missing on the new notebook) is the network configuration (DHCP and so on). Is there boot-parameter to stop the installer from using the wifi?

More strange: I tried normal (non-alternate, 64bit) live-ubs-stick and it worked fine ...

I'm glad that the normal 'desktop' installer works for you :-)

The configuration of the network is done in different ways in the desktop and alternate installers. Maybe it would work, if you can switch off the wifi in the BIOS/UEFI menu system. I don't know if a boot option can fix it. But you need not worry about that now.

---

### Post by h9-watt1ias-ub on 2014-04-10
Oh no - the desktop LIVE-stick works, but not the desktop-installer (it stops after the second step, showing the requirements (power supply, internet connection, free disc space, do you want to install 3rd party programms?...); and it stops on "direct-installation via startup as well as installation from the live-system.

Very strange....

---

### Post by sudodus on 2014-04-10
Yes. Very strange. But there are still ways to go.

- Can you enter into the BIOS/UEFI menu system? Then you can try to switch off the Broadcom wifi. After installation, it should be possible to install a driver for it.

- Are you willing to try some non-standard installer and install a portable system (that can be modified later on for your wifi and maybe your graphics)?

---

### Post by mastablasta on 2014-04-10
and what happens if you have a wired internet?

in this case installer want to connect to internet, but before it tries to do that it serarches for a way to do it and finds a wi-fi. it is attempting to load the drivers for it automaticly but it fails at that.perhaps it identified the wi-fi wrong or perhaps the drivers it needs are not available to it. and option would be to somehow supress this message or urge to connect to internet. 

what happens if you try it with mini.iso?

---

### Post by h9-watt1ias-ub on 2014-04-11
Found a solution :-)

Here ([http://www.ubuntu.com/certification/hardware/201204-10860/](http://www.ubuntu.com/certification/hardware/201204-10860/)) it says I should install 12.04.3 . So I downloaded that alternate-installer - and it worked! Yeah. Now I only have to fix a wifi-problem (but that's another topic - I'll try it on my own first and open a new thread if nesseccary).

Just to answer your question: I was able to turn of wifi in BIOS but it didn't helped. And I (would have) been willing to try some non-standard installer or a portable system (I really like experimentation).

Thanks & By

---

### Post by sudodus on 2014-04-11
Good luck and welcome back with a new thread if nesseccary :-)

Finally, please click on Thread Tools at the top of the page and mark this thread as SOLVED

---

