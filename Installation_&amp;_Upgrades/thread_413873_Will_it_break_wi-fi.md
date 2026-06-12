---
title: "Will it break wi-fi?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by jpatton on 2007-04-19
After getting through the kernel upgrade problem that killed my wifi (prism 2.5) does anyone know if upgrading to the current release will re-break it? I'm getting ready to ghost my laptop just in case, but thought I would ask if anyone had experienced any problems related to that.

Thanks,

---

### Post by spookypeanut on 2007-04-19
I have an rt61 pci card, which i had to manually build the kernel module for on edgy (taught me a lot of useful stuff :-). It did break when I moved to feisty, but only because feisty supported my card natively: I just typed in my wep details and I was away.

That said, I'm sure it's going to vary dramatically depending on each individual situation...

---

### Post by jpatton on 2007-04-19
> **spookypeanut said:**
> I have an rt61 pci card, which i had to manually build the kernel module for on edgy (taught me a lot of useful stuff :-). It did break when I moved to feisty, but only because feisty supported my card natively: I just typed in my wep details and I was away.

That said, I'm sure it's going to vary dramatically depending on each individual situation...

Was your card for a desktop? does it use the same chipset that many of the builtin wireless cards on laptop's use? A fresh install of Ubuntu 6.10 detected the builtin right off the bat, but the subsequent kernel upgrade broke it.

---

### Post by spookypeanut on 2007-04-19
it is a desktop card, i believe the same chipset is used in some laptop cards. my card seemed to be detected fine in edgy, but it didn't work. i didn't go into details of why: i believe there was a bug in the kernel module, but it could have been that it was mistakenly detected as something it was not. i just went through a very nice tutorial on how to fix it.

if and when you go for it, good luck :)

---

### Post by jpatton on 2007-04-20
> **spookypeanut said:**
> it is a desktop card, i believe the same chipset is used in some laptop cards. my card seemed to be detected fine in edgy, but it didn't work. i didn't go into details of why: i believe there was a bug in the kernel module, but it could have been that it was mistakenly detected as something it was not. i just went through a very nice tutorial on how to fix it.

if and when you go for it, good luck :)

FYI, the upgrade to ubuntu 7 did re-break my wifi, it had to replace the blacklist file, i would think it could merge the new blacklist with the existing blacklist. getting ready to add the entries that _should_ fix the wifi:

-blacklist prism2
-blacklist prism2_pci

REVISED: ADDED ALL BLACKLIST ENTRIES AS FOLLOWS
I didn't include all the appropriate entries here is the correct list

blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap

FYI wi-fi is now working, at least I hope it is since I'm connected to the internet without going through the wire ;)

FYI after the upgrade Ubuntu 7 forgot my updated splash screen :(

---

### Post by mcleaver on 2007-04-22
blacklist prism2

???

You'll have to explain this to me. my prism worked in 6.06 but not in 6.10 or FF and now GTKWifi informs me in 7.04 that I don't have a wireless card, even though wlan0 seems to exist.

WHat's going on? 

(Prism wifi in Fujitsu Lifebook P2020)

Martin

---

### Post by jpatton on 2007-04-23
> **mcleaver said:**
> blacklist prism2

???

You'll have to explain this to me. my prism worked in 6.06 but not in 6.10 or FF and now GTKWifi informs me in 7.04 that I don't have a wireless card, even though wlan0 seems to exist.

WHat's going on? 

(Prism wifi in Fujitsu Lifebook P2020)

Martin

Just so you know I'm not espousing to be an expert here, but from what I understand, my laptop's built-in wifi uses the orinoco driver. After a clean install of Ubuntu 6.10 wireless worked great, then when you would do the update, there were like 170 + or -, there would be an upgraded kernel.

That kernel, and don't hold me to the version, 2.16* has a problem detecting the wireless properly. In fact, after the update it said my wireless card had become a wired card! Either way it didn't work after the update. After searching through Ubuntu Forums, I found several articles related to what I thought to be the problem, and after trying a few wound up with something that worked for me.

Now if your card truly does use the prism driver, I don't think you should blacklist..lol..but that's my opinion. But blacklisting the prism2 driver on my laptop allowed my builtin wireless to work properly. I believe you can boot into previous kernels, if so, boot into the kernel where your wireless was working and run this:

sudo lsmod

Not sure if you need the sudo, but doesn't hurt, it should spew out a list of stuff, you should be able to pipe that through grep to find your wireless, something like this:

sudo lsmod | grep orinco

Here is the output of a couple of commands that display what wireless card I have, and what driver it uses.

jeffpatton@mobile-pc-01:~$ lspci |grep Wave
02:05.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
jeffpatton@mobile-pc-01:~$ lsmod |grep Prism
jeffpatton@mobile-pc-01:~$ lsmod |grep prism
jeffpatton@mobile-pc-01:~$ lsmod |grep orin
orinoco_pci             8064  0 
orinoco                43028  1 orinoco_pci
hermes                  8448  2 orinoco_pci,orinoco
jeffpatton@mobile-pc-01:~$ 

There ya go, for what it's worth, you will notice that my wireless says its a prism 2.5 but it is _not_ using the prism2 driver, but it does use the orinoco driver.

---

