---
title: "GUTSY - Broadcom Fix!"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by mschap on 2007-10-27
Ok for those of you ready to go back to Fiesty because you cannot get your Broadcom WIFI card to work under Gutsy.  Here is a method that worked great for me.  So here goes;

First go into System -> Administration -> Restricted Drivers Manager

Make sure you DESELECT the button for the Broadcom card and it will remove fw-cutter.

Once it is finished do a restart of the computer.

Your card should NOT work at this point.

Then follow the instructions for the post ["Edgy Broadcom bcm4318 HOWTO! [Now updated for Fiesty] ]("http://ubuntuforums.org/showthread.php?t=285809&highlight=Edgy+Broadcom+bcm4318+HOWTO")"

The instructions are as available there but I have posted them below as well.

Edgy Broadcom bcm4318 HOWTO! [Now updated for Feisty] 

Unknown whether this or similar works with the AMD64 and other versions of ubuntu, if you have success please post it in this thread.

Download ndiswrapper from Synaptic
System -> Administration -> Synaptic Package Manager 
Search for ndiswrapper 
Download "ndiswrapper-utils-1.9" and "ndiswrapper-common" (Edgy Users may only have 1.8, this is fine for the howto - someone tell me if edgy ndiswrapper has or has not been updated) 

Blacklist native bcm43xx drivers
Type:
Code:
sudo gedit /etc/modprobe.d/blacklist
Add the line:
Code:
blacklist bcm43xx
After saving type at the terminal:
Code:
sudo rmmod bcm43xx

Get windows drivers and install them
A) Download and extract windows drivers to a folder of your choice. Drivers can be found here 
B) Drivers from original disk are also fine, the previous link is just a newer version
Install them in ndiswrapper:
Code:
sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf
Check to see if hardware found
Code:
sudo ndiswrapper -l
If hardware not found and you are sure you followed the howto you have a different card and this howto will not work. 


Setup ndiswrapper to load driver (and itself) at startup
Edit the following file:
Code:
sudo gedit /etc/modules
Add a line which says:
Code:
ndiswrapper
Restart 

During restart the "Wireless On" light for your laptop should turn on or flash depending on your setup (Well it did for me: your results may vary)
If light does not show try pressing wireless button (incase left in off mode) 

Setup Wireless Card in Networking (Manual setup is also fine)
System -> Administration -> Networking 
Enable wireless connection and configure all the settings 
Disable wired connection (wireless and wired connections may not work simultaneously - your mileage may vary in this regard, if it doesnt work, it should after extra tinkering that isnt covered here) 
Use the internet/LAN! 

This was posted from my laptop which used the above method.
Kudos to lolcese for driver link (moved since previous revision of this howto)

Hope it helped!

---

### Post by portach king on 2007-10-29
OK, well this worked very well for me. 
I'll update whether my broadcom also works on my college network, as the restricted drivers did not at all. 

Thanks for sharing the info. This post deserves a BUMP

---

### Post by allo2u on 2007-10-30
Thanks for the quide!
I'm using 64 bit Gutsy on an Asus A6T laptop with broadcom bcm4318 rev2 and finally got the card to work with the drivers I attached to this message.
So, confirmed working by at least one 64 bit user! :)

---

### Post by portach king on 2007-11-01
BUMP AGAIN.

Finally! I can absolutely confirm that Gutsy now connects flawlessly with my college's wireless network thanks to this guide. I'm writing from it now, and it's been running for perfectly for the last hour and twenty minutes.
I'm delighted.

---

### Post by Thingbuilder on 2008-03-23
Thanks for posting. 
This fixed the poor performance and unreliability I was experiencing with fwcutter. 
HP Pavilion zv6000. 

TB

---

