---
title: "Already Frustrated"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by Satchul on 2010-03-05
After using Windows since the end of the DOS days I,
Downloaded WUBI to-day to a brand new external HD..
Was able to boot to Desktop.
Mouseover'd all icons showing.
What looked like a little umbrella told me no internet connection.
I have a wireless connection for Windows OK on a D-link router.
Attempted connection for ubuntu and got lost.
Loaded how-tos on another PC tried to follow directions but here is what I found.
There is no "Network Manager" icon in the upper right corner to click on.
Is there any chance the instructions are now outdated for a newer version of the software and some of the category headings are different.?
Also terminology is all different to what I am used to.
I need to get my wireless configuration working and hopefully things will get better.
 
Can someone help me here please.
 
Thank You

---

### Post by mikewhatever on 2010-03-06
The network manager should be present. Try right clicking the panel, select 'Add to panel', and add the notification area.

---

### Post by leeper69 on 2010-03-06
You should have what looks like a gray resistor in your panel at the top or bottom of your desktop next to what looks like a gray speaker. when you put your mouse pointer on it you should get a banner that will say wired network connection if you click your right mouse button a small window will pop up. if the enable network check-box is empty click on it to enable your network.
 Hope this helps!

---

### Post by Travlur on 2010-03-06
Thank you for the replys.
 
Mike, I added the Notification Area and was able to navigate to Network Manager.
However no Automatic discovery of my wireless connection was found, so I am going to fiddle with configuration.
I have no idea what "Infrastructure or Ad Hoc" means.
Is there an appendix of ubuntu terminology somewhere.
 
leeper, I followed your instuctions and "Wired" is enabled (by default ) but I am trying to get my "Wireless Connection" working so am not hard wired.

---

### Post by mikewhatever on 2010-03-06
Take a look -> [http://www.bellaonline.com/articles/art3343.asp](http://www.bellaonline.com/articles/art3343.asp).

You should probably post the output of lspci command. Chances are, you have a Broadcom wireless card, which needs a closed source driver enabled.

---

### Post by Travlur on 2010-03-07
Thanks again Mike.
It looks like terminology will be my downfall.
If I don't understand how to use your advice I am wasting mine and your's time.
It took me 15 years to absorb Windows software versions.
I have uninstalled the WUBI program from my system, perhaps when I get home I'll try a clean install of ubuntu on an unused PC and give it another go.

---

### Post by mikewhatever on 2010-03-07
In most home scenarios, all machines are connected to a router, which is an infrastructure network.
In adhoc network, machines communicate with each other directly, without a router.

---

