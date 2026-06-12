---
title: "Feisty Wireless WPA"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by thrillhouse on 2007-04-20
Hi I just upgraded over Edgy this morning.  In Edgy, connecting to my WPA-PSK wireless router was not a problem.  After upgrade, network-manager just spins until it can't connect (none of the green balls light up).  

Heres the pertinate line of lspci:
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

In the Restricted Drivers Manger lists "Atheros Hardware Access Layer (HAL)" as enabled and 'In Use' with a green dot as its status.

---

### Post by petermck on 2007-04-21
Got the same problem. It didn't work in 6.10 either. It seems as if the ath0 interface is not getting a  n IP address.

---

### Post by swadey on 2007-04-21
I've got two machines (both using the atheros driver) with exactly the same issue: working WIFI + WPA-PSK in Edgy, unable to connect in Feisty.

Any ideas out there?

---

### Post by gewitty on 2007-04-21
Similar problem here also. After installing the Feisty upgrade over a fully working Edgy, I now cannot get my wireless connection working at all.

I also have severe slow-down problems when booting (takes about 4/5 minutes!) and also when loading most applications (Firefox, Thunderbird, etc). These seem not to respond, but after a minute or so, they suddenly start up.

The upgrade appeared to go OK, but there seem to be a few critical things that are now broken.

As a relatively new Linux user, I haven't a clue what to do next. I spent several weeks learning about Edgy and getting it set up the way I wanted it, but it looks as if I may have to go back to square one again with a complete re-installation of Edgy.

Any ideas on what may have happened and how I can sort it out would be very welcome.

---

### Post by swadey on 2007-04-21
Well, this is definitely a bug: I just turned on SSID broadcast on my router and, voila!, all of my feisty machines can now connect properly with WPA-PSK.  Seems like the handling of hidden SSIDs has broken since Edgy.

---

### Post by gewitty on 2007-04-21
Tried enabling SSID broadcast and that got me connected again, but my KWiFiManager monitor is going haywire. It appears to show the signal strength constantly cycling from zero to full, although the connection seems stable.

Curiously, the apps that I reported earlier as being very slow to load, now seem OK, but I can't see any connection between this problem and the wifi issue. I'm way out of my league here, but could this be a memory leak?

---

### Post by nickswift on 2007-04-22
I have a slightly different problem - using Feisty with hostapd. 

Am able to get a non-Windows XP device to connect but XP clients cause an EAPOL Key Timeout.

This used to work in Edgy.

Nick

---

### Post by bhtooefr on 2007-04-22
I had the same problem...

Just fixed it by broadcasting the SSID and switching it from TKIP to AES (at the router.) Bug in nm-applet?

Relevant lspci line:

04:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

I've also noticed that it freezes at loading ACPI modules and starting hald for a couple minutes.

---

### Post by gavlees on 2007-04-22
I don't know if this is a related problem (I'm fairly new to Ubuntu and a bit of a Linux dunce) - 

Upgraded to Fiesty yesterday and, of course, had problems with my stupid Broadcom card.
Used the bcm43xx_compwiz18.1-all.deb file and everything seemed to be peachy.

Then, after a reboot, the internet began to run reeeeeally sloooooowly...like 1K per second slowly.

Does anyone have any ideas how I can fix this?  

Everything worked brilliantly on Edgy and there's nothing wrong with the WiFi on my Windows partition.

---

### Post by gavlees on 2007-04-22
Okay, update - if I go to System->Admin->Network then disconnect and reconnect the wireless card, everything works great.

Is there a way round this?

---

### Post by malyfotograf on 2007-04-22
I have a Bcm43xx and had the same problem with WPA. After few hours of research and playing with various drivers etc. I found this (in German): [http://forum.ubuntuusers.de/viewtopic.php?p=693638#693638](http://forum.ubuntuusers.de/viewtopic.php?p=693638#693638)


 I reinstalled the system, compiled the newest version of ndiswrapper (1.42) - now Broadcom card work perfectly with WPA-PSK.

---

### Post by lett on 2007-04-26
Exactly the same in my case. No hidden SSID = WPA works. Does someone know if there is solution for that?

---

### Post by bhtooefr on 2007-04-27
I'm tempted to play around with different packages - downgrade to the 6.10 version of network manager, mainly.

---

### Post by merlin666 on 2007-04-27
> **malyfotograf said:**
> I have a Bcm43xx and had the same problem with WPA. After few hours of research and playing with various drivers etc. I found this (in German): [http://forum.ubuntuusers.de/viewtopic.php?p=693638#693638](http://forum.ubuntuusers.de/viewtopic.php?p=693638#693638)


 I reinstalled the system, compiled the newest version of ndiswrapper (1.42) - now Broadcom card work perfectly with WPA-PSK.

I would like to get wireless and hopefully also WPA encryption to work with broadcom chip in EDGY-64 bit. I did not find a good link to instructions yet, how can I get this accomplished?

---

### Post by depp on 2007-04-27
using ndiswrapper from repo caused the same problem here. manually compilation and installation of ndiswrapper 1.4.2 from source solved the issue.

---

