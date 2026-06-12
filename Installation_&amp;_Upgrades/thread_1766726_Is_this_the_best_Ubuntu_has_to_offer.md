---
title: "Is this the best Ubuntu has to offer?"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by Phaze08 on 2011-05-24
So, I've always heard Ubuntu was great, and I ran it for a while a week or so ago and I really liked it and thought it was very cool. Some things though refused to work, such as when I tried to set up a vpn for my work network, it said unable to connect, even though I know I had all the settings right, as I'm the one who set up the vpn server at work lol. Also, it never seemed like my video card worked just right....I have an Nvidia, which I always heard works best on Ubuntu, but I installed all the proprietary drivers that I could find and all of them said 'This driver is activated but not in use.' Have these things been fixed, or are they being addressed? Another thing that I observed is that it took me around 3 hours to get my wireless driver to work.I really like Ubuntu, but if its not going to work right, I can't run it. Especially the vpn part, which I need for work as I am the Administrator and need to access my network on occasion. Any input you guys have would be great, thanks.

Not complaining, btw, just checking on the state of Ubuntu.

---

### Post by mörgæs on 2011-05-24
Regarding the Nvidia drivers, there is a discussion here:
[http://ubuntuforums.org/showthread.php?t=1743386](http://ubuntuforums.org/showthread.php?t=1743386)

I have not used VPN, so I can not help with this, sorry. Might be worth trying 10.10 for comparison.

---

### Post by enkrypt3d on 2011-05-24
The Anyconnect Cisco VPN client works great for me... Not sure what client you were using..

Also install Nvidia's drivers from their website. Make sure you have the kernel headers and source installed. Be sure to run the driver install script with Xorg STOPPED. It wont work if X is running.

---

