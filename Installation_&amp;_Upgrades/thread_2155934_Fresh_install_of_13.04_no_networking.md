---
title: "Fresh install of 13.04 no networking"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by low_rider on 2013-06-20
I've been working on this one for a few days now and i'm stumped.  I recently installed Xubuntu 13.04 and can't get my network running (wireless or ethernet).  I've poured over the forum posts in hopes of finding something but i've not had any luck.  I'll post all the relevant data here in hopes that someone has any ideas.  Both the ethernet and the wireless come up just fine, but when it comes time to connect to anything outside the hardware it fails.  The amber light on the ethernet port never blinks which means it hasn't been sending any data.  The wireless actually manages to find 1 of the 3 or so wifi networks around but it can't find mine and i'm not sure I could connect to the found network even if I had the password.

---

### Post by ubfan1 on 2013-06-20
Looks like you have the right driver (b43), and the fact you can see other networks indicates you have the necessary firmware for it.  Is your router broadcasting its ESSID?  If not, in networkmanager, try a R click and select "connect to hidden network", fill in your info and see if that works.  Also run a scan and check the channels and signal strength -- sudo iwlist scan      Change your channel on the router if you have other networks on the same channel with a signal strength near yours.  Turn off IPV6 (set to ignore).

---

### Post by low_rider on 2013-06-20
Ok, so my router is broadcasting its essid and i tried the connect to hidden network anyway.  I also tried the iwlist scan and got no results.  I've tried this one several times and have never been able to find the one network that the Network Manager finds so i don't know if Network Manager scans things differently.  I've tried turning off IPv6 and still nothing.

---

### Post by ubfan1 on 2013-06-21
Try moving your PC to nearby the router, and ensure the antennas are clear of obstructions.  Sounds like your signal is too weak to be selected.

---

### Post by low_rider on 2013-06-21
Update: I installed Debian squeeze which uses the linux 2.6.32 kernel  now the ethernet works correctly.  The wireless is performing better as  well; I can find my router now just can't get through on dhcp.  I've not  really tried too much in the way of fixing this yet, but I'll keep you  updated on what goes on there.  Currently it looks like the router is  acknowledging my dhcp request and then my computer is refusing it for  some reason.  I believe that the original issues I was having stemmed  from the modules included in ubuntu 13.04's linux kernel (v3.8).  It  sound like there were lots of people having trouble with the r8169  driver and I think that it might have been persisting despite me  uninstalling it and installing the r8168 driver from realtek.  I think  there may have been a similar issue with the b43 driver.  At any rate  this seems to be occurring in linux kernel (>=3.2) since I  experienced the same issues in Debian Wheezy (7.0) and Ubuntu 12.04LTS.   I'll keep looking into this and see if maybe there is a kernel bug.

Oh as a note for ubfan1, I did try moving my pc closer to the router and it didn't have any effect.  I know that all the hardware works properly since I've managed to get it working on different OS's.

Thanks!

---

### Post by kwalters on 2013-06-23
Apologies if I am teaching granny to suck eggs; but you have not mentioned wireless security. If your network has it, have you entered the right password for  the right sort of security.  Try removing the security temporarily using the admin interface with your router; if you can then connect properly, the problem lies there

kwalters

---

### Post by low_rider on 2013-06-24
kwalters,
Thanks for the reply.  I've checked the wireless security and that is not the issue here.

---

