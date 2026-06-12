---
title: "Latest update broken wireless (Acer Aspire 5551)"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by Martyn Thompson on 2012-06-06
Hello people, 

I have sort of gotten used to updates breaking my wireless however this is a new one on me... 

I am using the brcmsmac driver for the broadcom BCM43225 802.11b/g/n (rev 01) chip/card. 

The problem I am having now is that the connection keeps tripping out every few seconds. It does re-establish again within a few seconds but is really hacking me off,  it would be impossible to work with.  

Fortunately I have a USB card to use in these situations but if anyone has a fix or hack for this I would be grateful.  I have done a search for this on this forum but most recent comments are 2008 so might not be valid for newer drivers.  

Any advice out there? 

Thanks, 

Martyn.

---

### Post by darkod on 2012-06-06
I'm not a network expert but this says it should work with the standard STA driver:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Did you give it a go?

I think the STA shows up in the Additional Drivers list on a new install. Not sure how it works on an upgrade though.

You might remove (purge) it anyway and reinstall it. There are few approaches in that link.

---

### Post by Martyn Thompson on 2012-06-06
Darkod,

I will give that a try... I did install the STA driver once earlier tonight without success but will give it another go... 

Thank you. 

Martyn.

---

### Post by Martyn Thompson on 2012-06-06
Just to let you know, 

I re-installed the STA driver as suggested but was getting nothing.  I had a look at 'dmesg' and nestled amongst all that was a comment about wl not understanding a command I had set to pass to it to enable channels 12 and 13 (I am in the UK).  

Anyway, I commented out the command in /etc/modprobe.d/config.conf, modprobed wl and the wireless light came on (yay!) and a few seconds later the connection established and has stayed connected. 

I think this is a lesson to self - remember any settings you mess with! 

Thanks again Darkod.  Without your guidance I wouldn't have known where to start trying to fix. 


Martyn.

---

