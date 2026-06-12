---
title: "Active partition not found fix?"
date: 2014-10-14
forum: Installation &amp; Upgrades
---

### Post by chonni on 2014-10-14
[EDIT]

Solved. Simple fix. Thanks guys :).

Sorry, I know this is not technically a Ubuntu installation question, but I would be really grateful if anyone could help out with this.

Someone was chucking out an old laptop with no operating system on it and I thought, since my old one broke and I miss having one. I've used Ubuntu before and I really liked it so I thought it would make a cool little machine to tote around. 

When I started it up though, I got the message 'active partition not found' so it won't boot off the cd. Which is where my extremely limited computer knowledge fizzles out.

What I really need to know is 1) Can I fix it to install ubuntu on this thing or do I dump it, and 2) Can someone tell me in relatively simple terms how I can fix it? 


The machine specs are apparently: 

TOSHIBA PORTEGE A600 
 
Model Number - PPA61A-00J005 
CPU - INTEL CORE 2 DUO 1.4GHz 
MEMORY - 2GB's DDR2 SDRAM 
SCREEN 12" 
 
And it was running Vista. I don't have discs for it and have no way of obtaining them. 
My desktop computer is running windows 8, and that won't boot the Ubuntu live cd I made either but a quick google search mentioned you had to fiddle around with it so I didn't want to risk messing up my work computer. Since I really should be working anyway. 

Any help would be really appreciated, thank you

---

### Post by coffeecat on 2014-10-14
Welcome to the forum!

> **chonni said:**
> 
When I started it up though, I got the message 'active partition not found' so it won't boot off the cd. 

That message suggests it is trying to boot from the hard drive, not the optical drive. In order to get the machine to boot from the optical drive, you have to change the device boot order in the BIOS. When you first switch on, the initial splash screen usually tells you which key to press for "setup". This varies from make to make - it's often a function key or del or esc - but I don't know what it is for Toshiba laptops. If you can get into the BIOS, set the optical drive as the first boot device and save. Then try booting from the CD.

---

### Post by yancek on 2014-10-14
The site below gives an explanation although another site said the F12 key, watch the screen on boot as suggested.

[http://www.thedumbterminal.co.uk/?action=showArticle&articleId=101](http://www.thedumbterminal.co.uk/?action=showArticle&articleId=101)

---

### Post by chonni on 2014-10-14
Thanks so much guys. This particular laptop doesn't have a startup screen with they keys for setup/safe modes so I couldn't even get into that - it was the esc key. Got it switched over, all booted up and installing as I type. :).

---

### Post by mörgæs on 2014-10-14
Good, please mark the thread solved using 'thread tools'.

---

