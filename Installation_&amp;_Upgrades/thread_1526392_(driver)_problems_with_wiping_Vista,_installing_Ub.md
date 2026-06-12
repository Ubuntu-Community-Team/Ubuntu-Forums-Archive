---
title: "(driver) problems with wiping Vista, installing Ubuntu?"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by kamion_rooster on 2010-07-08
I just bought a netbook, HP DV2-1039WM, which comes with Vista.  I wiped the hard drive and installed Ubuntu 9.10.  A problem has arisen in that it doesn't see any wireless card.  There is a button on the side with an indicator light that is used to enable/disable wireless.  The light is amber and, according to the manual, it is supposed to be blue when wireless is working.  The manual just says "push the button" to turn it on, which doesn't do anything.  

So, I'm pretty new to linux in general.  I recently installed a dual boot on my desktop with Windows 7/Ubuntu, which doesn't have any problems.  Are there driver/hardware issues with the setup I am trying on this netbook?  The HP website only has drivers for windows OSes listed.  Theoretically, I could reinstall windows and/or do a dual-boot, but I'd rather just keep only Ubuntu on it if possible.

---

### Post by Gregorybekkers on 2010-07-08
Find out what kind of wireless card you have.
it is possible that there is a driver in "Hardware"
but isn't enabled by default.

---

### Post by robabdul on 2010-07-08
I hoping someone can help me with my driver query too.

I also have Vista installed on my laptop and want to switch to Ubuntu.

Will ubuntu recognise my hardware, my sound card, wireless card etc.

The reason I ask is because usually when you purchase hardware, drivers are provided for windows and Mac OS's but not for ubuntu.

How does that work guys?

---

### Post by Gregorybekkers on 2010-07-08
well...,
if you have a good hardware vendor it has linux driver on it's webpage.
i know that Nvidia and Realtec have it.
but it depends on your hardware.
otherwise you have to write it yourself (or someone else just google it)

---

### Post by Mark Phelps on 2010-07-08
> **kamion_rooster said:**
> I just bought a netbook, HP DV2-1039WM, which comes with Vista.  I wiped the hard drive and installed Ubuntu 9.10.  A problem has arisen in that it doesn't see any wireless card.  There is a button on the side with an indicator light that is used to enable/disable wireless.  The light is amber and, according to the manual, it is supposed to be blue when wireless is working.  The manual just says "push the button" to turn it on, which doesn't do anything.  

It doesn't do anything because the drivers to interface with that button were installed in MS Windows but not in Ubuntu.

I've worked this problem on several different laptops, and in ALL cases, there was no way to get the "wireless button" to work in Ubuntu.

Perhaps someone with more detailed knowledge of hardware drivers can provide some help.

---

### Post by kamion_rooster on 2010-07-08
I don't mind if the button never works.  I was just using that as an example to describe what is wrong.

Being new to Ubuntu, can anyone please tell me where to check to see what drivers are available so I can see if it might already have a correct one?

I'm not even sure I can find the name of the wireless card.  None of the product specs seems to list it.  It looks like the HP driver is here:
[URL="http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-82549-1&lc=en&dlc=ar&cc=us&os=2100&product=3948084&sw_lang="]http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-82549-1&lc=en&dlc=ar&cc=us&os=2100&product=3948084&sw_lang= 
[/URL]

---

### Post by Laurelai on 2010-07-10
Same problem as these guys, i bet they have the same wifi card i do

Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

I have installed the drivers for this card and the button will not turn on the card, no networks are detected and the wireless light is amber, I have checked the bios for any wireless settings and there are none. when windows was installed, ( ive tried xp vista and 7 on it ) you had to install a program to even be able to turn the button on, even if the drivers were installed the button would not work untill this other hp application was installed.

---

### Post by Laurelai on 2011-02-08
I actually found the solution to this on freenode in #fedora and i thought i should share the answer , install rfkill and use it to turn your card on.

---

