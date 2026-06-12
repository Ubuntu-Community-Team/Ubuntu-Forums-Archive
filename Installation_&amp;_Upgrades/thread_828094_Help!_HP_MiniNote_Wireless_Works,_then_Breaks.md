---
title: "Help! HP MiniNote Wireless Works, then Breaks"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by demoiselle on 2008-06-13
Hi,

I'm a new user of Ubuntu, inspired to change because I really, really don't want to run Vista on my new HP MiniNote 2133. Before my MiniNote arrived, I got a sucessful installation (through Wubi) of Ubuntu on my old laptop. Now I'm trying to get it running (dual boot with Wubi) on my MiniNote.

I have followed all the directions on the HP MiniNote Ubuntu Wiki. I got everything working, including the wireless. I was a happy camper, and installed the software that I needed. 

But then the wireless broke. Suddenly, after I restarted, the computer searches and searches for a singnal, detects the wireless network, but cannot connect. Then it start asking for the passcode over and over, but no matter how many times I enter it, the computer can't complete the connection.

The first time this happened I thought perhaps as a newbie I had done something wrong, so I did a clean install last night. I went to bed, and everything worked perfectly. This morning, everything worked perfectly. But 20 minutes ago, when I turned my mininote back on, the same problem began again -- the wireless is broken.

How can I diagnose what is wrong and fix it? Why, when everything was working fine, does the wireless quit?

I appreciate any, ANY advice. I love Ubuntu, and I don't want to have to use Vista whenever I need the web - which is most of the time when I am on the computer.

demoiselle

---

### Post by dstew on 2008-06-13
Do you have several different access points available? Is it trying to connect to a different access point, perhaps with the same name? If roaming is enabled, and your usual signal is weak, it might try to connect to another. If you disable roaming, maybe you can get it to stick.

Can you connect to an unencrypted access point? Can you connect with a wired interface?

---

### Post by demoiselle on 2008-06-13
> **dstew said:**
> Do you have several different access points available? Is it trying to connect to a different access point, perhaps with the same name? If roaming is enabled, and your usual signal is weak, it might try to connect to another. If you disable roaming, maybe you can get it to stick.

Can you connect to an unencrypted access point? Can you connect with a wired interface?

I can connect with ethernet. Usually there are only two access points available -- our home, and one other. When I am in Vista, the computer consistantly detects and connects to our home network. When in Ubuntu, at this point, the computer sometimes "sees" the network, and sometimes doesn't.

Changing roaming doesn't seem to fix anything.

---

### Post by demoiselle on 2008-06-13
Can anyone advise me? I'm really stumped. I don't understand what could be interfering with the wireless!

---

### Post by violajack on 2008-06-16
I'm not sure if you're still working on this, but user moom on the mininoteuser forums posted a way to compile new drivers for the wireless.  I was having the same problem where the ndiswrapper would work once and then refuse to connect on a reboot despite numerous attempts to keep poking it into joining something.  I compiled a new b43 following the instructions moom linked to here: [http://64.233.167.104/search?q=cache:7RWE-cL0g1AJ:www.myscienceisbetter.info/cgi-bin/mt/mt-search.cgi%3Ftag%3Dubuntu%26blog_id%3D1+compat-wireless+ubuntu&hl=en&ct=clnk&cd=3&gl=us](http://64.233.167.104/search?q=cache:7RWE-cL0g1AJ:www.myscienceisbetter.info/cgi-bin/mt/mt-search.cgi%3Ftag%3Dubuntu%26blog_id%3D1+compat-wireless+ubuntu&hl=en&ct=clnk&cd=3&gl=us)

It is working for now, and I am connected through a WPA protected network.  I haven't rebooted yet to know if it will survive, but I'm hopeful.  It's at least worth a try.  

FYI I'm on a 1.2 US mini note.

ETA link to mininoteuser thread: [http://forums.mininoteuser.com/viewtopic.php?f=11&t=194&start=20](http://forums.mininoteuser.com/viewtopic.php?f=11&t=194&start=20)

---

