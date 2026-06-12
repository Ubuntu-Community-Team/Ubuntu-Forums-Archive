---
title: "Setup of router on startup"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by Mr. Gruff on 2005-07-01
I'm trying to get my internet connection set up through a router, and I can start it manually, but I'd like to have it up on startup. To start it up I have to:
iwconfig wlan0 essid <ESSID>
iwconfig wlan0 key <key>
dhclient wlan0

Then, I have to manually set up the DNS IPs, which have a tendency of resetting every ~30mins.

How can I automatically set up the connection? Any help would be very much appreciated. BTW, I'm a total newbie to Linux.

---

### Post by rachii on 2005-07-01
wow, i never had to do all that (except when i was in fedora)  ubuntu took care of everything for me.  

if you goto System-Administration-Networking   does your wifi card show up and is it configured and all that in there

also do you have a straight up nic card as well?  your computer might be defaulting to the nic and then not setting up your wifi (this is what happened to me) if that is the case this should fix it:
-if so in the networking window make Default Gateway Device = your wifi device
-and click properties for the eth0 card and uncheck the "this device is configured" -box

---

### Post by intangible on 2005-07-01
Does: **System->Administration->Networking** not work properly for you?  If not, let me know, I'll try to help :)

---

### Post by Mr. Gruff on 2005-07-03
[QUOTE=intangible]Does: **System->Administration->Networking** not work properly for you?  If not, let me know, I'll try to help :)[/QUOTE]
 Hmm, if I set it up through the networking app, it doesn't work, and I still have to go through the terminal. (the app automatically sets the network type to restricted, but it is open, and the ESSID is set to "any", despite it being specified). The DNS is still resetting (possibly due to DHCP of the router?). 

I have a NIC, but it's disabled.

---

### Post by intangible on 2005-07-05
I'm not sure of the right way to do this, but "sudo chattr +i /etc/resolv.conf" will block dhclient from writing to the file so your dns stuff won't be lost.

I was thinking if you added the DNS ips through the network config utility, it would place them in the right place so they don't get overwritten.

---

### Post by alastair on 2005-07-05
You can add the wifi interface to the file :

/etc/network/interfaces

and it should be setup at boot e.g.

iface wlan0 inet dhcp
wireless_essid <ESSID>
wireless_key <KEY>
wireless_keymode restricted
wireless_ap <AP MAC>

This will be where "ifup/ifdown wlan0" will get the setup.

---

### Post by Mr. Gruff on 2005-07-07
[QUOTE=alastair]You can add the wifi interface to the file :

/etc/network/interfaces

and it should be setup at boot e.g.

iface wlan0 inet dhcp
wireless_essid <ESSID>
wireless_key <KEY>
wireless_keymode restricted
wireless_ap <AP MAC>

This will be where "ifup/ifdown wlan0" will get the setup.[/QUOTE]
 Thanks for all your help. I managed to get the DNS problem sorted with this thread: [http://www.ubuntuforums.org/showthread.php?t=39606](http://www.ubuntuforums.org/showthread.php?t=39606)

Alastair, that worked brilliantly. Internet now loads up on startup.

---

