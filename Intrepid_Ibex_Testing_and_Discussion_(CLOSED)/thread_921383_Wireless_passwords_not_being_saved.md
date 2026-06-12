---
title: "Wireless passwords not being saved"
date: 2008-09-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2008-09-16
Has anyone found that wireless/WPA passwords are not saved in 8.10? Maybe I need another package? There seems to be no option to save the password on the standard connection box window.

---

### Post by blakamin on 2008-09-22
Having the same problem... Very annoying

---

### Post by hotstepperk on 2008-09-22
Have the same problem myself. Im using a hp-530 comp and every time i log off n log in again, it asks for the network key. Very annoying!!

---

### Post by gaussian on 2008-09-22
Yes, this is annoying. 

See [http://ubuntuforums.org/showthread.php?t=921064](http://ubuntuforums.org/showthread.php?t=921064) and [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/206568](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/206568)

---

### Post by TDragon on 2008-09-22
Same here.. its nice to know that I'm not alone.
 
I tried going back to wicd, but couldn't get it to work well with the Intrepid beta.

---

### Post by gaussian on 2008-09-22
> **TDragon said:**
> Same here.. its nice to know that I'm not alone.
 
I tried going back to wicd, but couldn't get it to work well with the Intrepid beta.

I have wicd working perfectly for Intrepid, but I am (sort of) feeling guilty about using it. Part of the Alpha-Beta-RC process is to help Ubuntu developers debug their product. Downloading a third party program to circumvent a key component of average user's daily usability experience (NetworkManager) seems like cheating :)

---

### Post by retrow on 2008-09-22
Same problem (on Atheros card) here. I tried going to gconf-editor to see the network settings. The connection information for network w/o WPA encryption is saved, but the networks with WPA encrytion don't even show up under networking section.

[img]http://nuclear-imaging.info/files/image/wifiinformation_gconf.png[/img]

---

### Post by Duf_Sh on 2008-09-22
Maybe that has to do with the gconf key key-mgmt being set to none (although I **may** have the same problem with knetwork-manager, since this one doesn't even try to connect, even to unprotected networks, so I'm using the gnome applet which works pretty well, key-amnesia problem aside)

---

### Post by blakamin on 2008-09-23
I don't even have "networking" in gconf-editor!
(and I'm typing this using my wireless!)

---

### Post by OffHand on 2008-09-23
Probably this is what happens: [http://ubuntuforums.org/showthread.php?t=753900](http://ubuntuforums.org/showthread.php?t=753900)

---

### Post by TDragon on 2008-09-23
My dlink card is also based on the atheros chipset. I moved to this beta in the hopes of using the native drivers that come with the new kernel, but even with the latest wicd build (wicd.net/latest), I am having issues connecting. I can see networks (w/ or w/o wicd), but I can't connect. In fact w/ wext as the WPA driver, it will not authenticate. However, if I choose ralink, it will only connect using static IP settings and will show 0% as the signal at the bottom of the window. Oh well, i'll just wait it out and hope that its resolved by the official release of intrepid.

---

### Post by rwabel on 2008-09-24
I do have same problem with WPA

---

### Post by RheaHS on 2008-09-24
Anyone having a problem with the Broadcom cards?

---

### Post by Vaun on 2008-09-24
Yes, Broadcom 4328 is working.  WPA2 password in not being saved, so upon boot it must be entered.  I had to blacklist ssb module to get it working.  I didn't have to do that on Hardy.

---

### Post by unisol on 2008-09-24
i have a linksys wireless card. alpha6 live cd doesnt accept the wpa  password for my home network, but, allows me to connect to philadelphia wireless, to which i dont have an account. cant figure this one out.

---

