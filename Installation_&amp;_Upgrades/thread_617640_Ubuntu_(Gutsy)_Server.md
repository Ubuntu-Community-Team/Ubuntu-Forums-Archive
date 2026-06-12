---
title: "Ubuntu (Gutsy) Server"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by Jamie.Aston on 2007-11-19
Hi Guys,

I currently have a Windows Server 2003 PC setup as a Domain Controller (mainly use Active Directory for single sign on and folder redirect for my clients in the house), DHCP, WINS, DNS, Webserver (PHP & MySQL), FTP Server & File Server in my Attic (started off as my experiment machine for my MCSE and to learn PHP & MySQL). I also have an additional WiFi Router setup as an Internet Gateway, WiFi Access Point & VPN Server. I have just descovered Ubuntu and think it's great and want to replace all this kit with a single mITX low power PC that runs Ubuntu Server (Gutsy) and provides all the above functions including replacing my WiFi Router. Was thinking of starting off by using the built in LAMP installer and then adding the DHCP, DNS, NAT translator, FTP & SAMBA services as well as anything i need to support single sign on, Folder Redirect & DC for my windows and ubuntu clients (can't get rid of my Windows Machines yet as the Mrs uses them and i also need them for work - Triple Boot My Laptop). Now for the questions:

1. Does this seem like a sensible way to approach this ? (Know quite abit about windows but not alot about linux).
2. Can i plugin a USB WiFi adapter into my box and setup the box as a WiFi access point or would i be better off adding an additional network port and pluggin in a access point?
3. Is a 4GB CF card big enough for this kind of setup (2TB RAID5 array will be used for all storage and folder redirect (if this is possible to setup with ubuntu)) or should i go for an 8GB card?
4. Are there any gui tools to help me along?
5. Will be using a Jetway J7F4 1.5GHz C7 motherboard (Dual GBit LAN, 1.5GHz CPU, 1GB RAM, Adaptec Dell 6-Port SATA RAID Card), is this a good enough spec for this sort of setup?

Thats all i can think of (for now). Will be greatful of any help anyone can give.

Thanks In Advance
Jamie

---

### Post by Jamie.Aston on 2007-11-20
Bump!

---

### Post by Jamie.Aston on 2007-11-21
Anyone?

---

### Post by Nicu Alecu on 2007-11-22
My 2 cents (in reversed order):

5. I installed a 7.10 server myself this week, on a far weaker system, and it runs smoothly; I've even set up Gnome on it (yeah, I know, some people might be appalled for this, but I'm not that familiar with doing things in a terminal just yet, I'm an ubuntuer for only six month now! ). So the answer to your q is yes, go right ahead.

4. If by GUI tools you mean Gnome, you'll have to install it after finishing de server install (you can customize everything else after setting up gnome); if you were reffering to the install process, well, one can hardly call that a gui but it's farily easy to use so don't worry about initial setup, just be sure to install all the services you need: samba, AMP and stuff.

3. As for the card, it all depends on how many things you want to add to your server; I'd go for the 8G just to be on the safe side; I have to admit that your setup is somewhar unconventional, I would expect a certain amount of trouble along the way.

2. I guess you could use the box as the router and wifi access point, but quite frankly, I wouldn't do that; in fact, execpt for the server itself, my environment is pretty much the same as yours and I didn't even think of moving routing, dns and ap on the server for a very simple reason: if something breaks on the server (and it just might, we are both ubuntu newbies, right? :) ) I would want the rest of my systems to have internet access, so that I can dig for answers here! and it's not just for the setup process, you know. It's generally a good thing to have services running on separate devices.

1. I started in reverse order because you first questionneeds a "conclusion" type of answer: I honestly don't know how sensible such a setup would be, but it certainly is a nice challenge. Go for it and keep us posted!

---

### Post by Jamie.Aston on 2007-11-23
Cheers Nicu, think it one of those 'suck it and see' things that will become clearer when i start.

Thanks Again
Jamie

---

### Post by mellowd on 2007-11-23
The specs are more than good enough for your server. a 2TB raid5 setup eh? very nice and i presume very expensive as 1tb drives still carry a premium. I reckon a 1.5tb raid5 setup will be less then half the price right now at 750gb drives are a lot cheaper.

as for a wireless access point, I haven't done it yet but I plan to soon and I'm sure I've heard of an application that can help you do this. If not I'm sure you could do this manually but again I haven't done it yet.

---

### Post by Jamie.Aston on 2007-11-23
Will be using 5x500GB WD5000ABYS (RAID Edition Drives) for the RAID5 array as my RAID Card (Adaptec 2610SA) only supports up to a 2TB RAID Array.

Jamie

---

### Post by daengbo on 2007-11-23
> **Jamie.Aston said:**
>  currently have a Windows Server 2003 PC setup as a Domain Controller (mainly use Active Directory for single sign on and folder redirect for my clients in the house), DHCP, WINS, DNS, Webserver (PHP & MySQL), FTP Server & File Server in my Attic (started off as my experiment machine for my MCSE and to learn PHP & MySQL). I also have an additional WiFi Router setup as an Internet Gateway, WiFi Access Point & VPN Server. I have just descovered Ubuntu and think it's great and want to replace all this kit with a single mITX low power PC that runs Ubuntu Server (Gutsy) and provides all the above functions including replacing my WiFi Router. Was thinking of starting off by using the built in LAMP installer and then adding the DHCP, DNS, NAT translator, FTP & SAMBA services as well as anything i need to support single sign on, Folder Redirect & DC for my windows and ubuntu clients (can't get rid of my Windows Machines yet as the Mrs uses them and i also need them for work - Triple Boot My Laptop). Now for the questions:

1. Does this seem like a sensible way to approach this ? (Know quite abit about windows but not alot about linux).
2. Can i plugin a USB WiFi adapter into my box and setup the box as a WiFi access point or would i be better off adding an additional network port and pluggin in a access point?
3. Is a 4GB CF card big enough for this kind of setup (2TB RAID5 array will be used for all storage and folder redirect (if this is possible to setup with ubuntu)) or should i go for an 8GB card?
4. Are there any gui tools to help me along?
5. Will be using a Jetway J7F4 1.5GHz C7 motherboard (Dual GBit LAN, 1.5GHz CPU, 1GB RAM, Adaptec Dell 6-Port SATA RAID Card), is this a good enough spec for this sort of setup?



Samba is cabable of managing your network with little trouble, but last time I checked, Samba didn't handle true single sign-on as a PDC. This can be accomplished with LDAP-Kerberos (basically what AD is), but the setup is not for the faint of heart.

Bottom line: Do a LOT of reading on this issue and take copious notes **before you ever put the CD in the drive**.

1. The approach is fine, but you will be able to apply for a Linux network admin job by the time you finish (That means the learning curve will be steeeeep).
2. Check the wireless compatability before you start and look up how to set up a wireless network. It's easy in Gnome, but the Ubuntu server version doesn't have a GUI.
3. Definitely go for 8GB. How are you going to handle all the log and temp file writes with that?
4. The server won't have a GUI. I might suggest that you look over eBox (ebox-platfom.org) or Webmin as web interfaces to administer the box.
5. As long as the server doesn't do seven different jos at the same time, you should be fine. I doubt your home network is large enough to tax the system.

Best of luck

---

