---
title: "Dapper Upgrade w/ Netgear WG511"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by dwessell on 2006-06-01
Hi all..

Just did an upgrde (As everyone else, I expect). In Badger my wireless card was on WLAN0, now I show ETH1 as a wireless. However, the card is not being fired up during the boot process.

I had previously been using it with ndiswrapper. And I show the ndiswrapper still being in use *sudo ndiswrapper -l*..

Do I need to point back to WLAN0? Or reload ndiswrapper, and somehow tell it to look for ETH1? 

Any suggestions would be helpful, and if I can provide any other information, let me know.

Thanks
David

---

### Post by kerskine on 2006-06-01
I have a similar problem. My WG511 worked fine with Breezy, but doesn't with Dapper. I can see the card using "[FONT="Courier New"]cardctl status/ident"[/FONT] but I get a "device not found" when I try to bring the interface up (using eth1). The prism54 driver is loaded. Please help!!

---

### Post by dwessell on 2006-06-02
I think we're hosed for a few days.. I've searched the forums, and right before the release there are posts about them not working, but no fixes.. So I'm guessing it'll be a few days before someone gets a fix posted...

dw

---

### Post by kerskine on 2006-06-02
That's just swell. Some people seem to have luck running via ndiswrapper, but I'd prefer using the "native" driver.

---

### Post by kerskine on 2006-06-02
OK - I've gotten wireless to work. I installed "network-manager-gnome" and it installed some libraries that seems to recognize the WG511 and start a network connection. 

Hope this helps :)

---

### Post by dwessell on 2006-06-02
[QUOTE=kerskine]OK - I've gotten wireless to work. I installed "network-manager-gnome" and it installed some libraries that seems to recognize the WG511 and start a network connection. 

Hope this helps :)[/QUOTE]

Kerskine... Before you installed that, was it starting your wireless card at boot? Mine isn't.. I did a brand new install of Dapper to see if that would fix it.. But the card isn't being fired up at all.


dw

---

### Post by Hebus95 on 2006-06-02
I installed ndiswrapper-utils from a brand new installation of dapper. It worked very well with the wg511v2 chipset.
Since i replaced the original i386 kernel with the k7's, it no longer works, despite of the recompilation of the ndiswrapper module.
I tried unsuccesfully the versions 1.11, 1.16 and 1.17

---

### Post by dwessell on 2006-06-02
I really think that mine is that Dapper is not attemping to load the PCMCIA card.. Can anyone point me in the right direction for making Dapper attempt to load the card?

dw

---

### Post by dwessell on 2006-06-03
Anyone who's gotten this card working in Dapper, can you post how? I'm not getting anywhere..

Thanks
David

---

### Post by Hebus95 on 2006-06-16
In my case the problem was from mrv8k.
So i prevented it to be loaded at startup :

echo "blacklist mrv8k"|sudo tee -a /etc/modprobe.d/blacklist

---

### Post by Xano on 2006-06-20
I have got problems with the Wg511 (version 3, made in China) and 6.06 as well. I've tried ndiswrapper and it said the driver was loaded sucessfully. Finally I realized the card wasn't powered up when Ubuntu was booted.

Are there any other people who have problems with PC cards not getting started? (not only this specific card, but others as well)

---

### Post by jmeuf on 2006-06-22
Hi,
I have a WG311 card installed with ndiswrapper. I have a problem at boot time when loading ndiswrapper (configuring network ... in the graphic interface): the boot hangs, not every time, but very often (90% of the time).

I tried the following installs of Dapper:
 - 6.04 from CD
 - 6.06 beta from CD
 - 6.06 LTS by upgrade from 5.10
For all installations, I got the problem.

Under 5.10 it worked perfectly.

I tried the recommendations from Kerskine (installation of network-manager-gnome), I have ndiswrapper-utils installed, and still get the problem.

When, by chance, the system boots, everything works fine.

Any idea ? Thanks.

---

### Post by allgaeu_yeti on 2006-08-11
Hi all
when using ndiswrapper with "netgear wg511 made in china" the problem is that by default the standard prism54 module is loaded too. This prevents the ndiswrapper module from working correctly. A possible way to prevent this is: 
put a line in /etc/modprobe.d/blacklist:  blacklist prism54
To test it beforehand you can "sudo rmmod prism54; modprobe ndiswrapper" and then configure the wlan0 Interface as usual. Driver's success is indicated when the LED on the card  is green and the other yellow one shows network traffic.

---

### Post by dm64 on 2006-08-24
I found that after upgrading I needed to add the line to blacklist the prism54 driver.

After that, because I already had the ndiswrapper driver installed uner breezy my card began to work!

So ensure you have blacklisted the prism54 and reboot - with some luck your card will come to life!:D

---

