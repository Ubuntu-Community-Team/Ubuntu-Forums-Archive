---
title: "Icon and theme set look weird(ish) in live session"
date: 2020-04-29
forum: Installation &amp; Upgrades
---

### Post by koosplegt on 2020-04-29
Hi,
I am a Xubuntu user since version 14.04. Great distro, never gives me troubles. But now when trying to do a clean install for 20.04 I encountered a problem in the live session. The panel looks off (whitish instead of the usual darker tint of the Greybird theme) and the icons are also not the usual elementary set. I could also not correct this in the live session.The strange thing is: this only happens when booting of a live usb on my Lenovo Thinkpad L440. On my Thinkpad T430 everything is displayed as it should. 

I did not proceed with the install. Should I be worried? Maybe everything will be normal again after installation or might there be a problem here? I included screenshots below.

---

### Post by CelticWarrior on 2020-04-29
The Thinkpad L440 has an old Intel Graphics (Intel HD Graphics 4600); the Thinkpad T430 has a newer Intel HD Graphics plus Nvidia (Optimus).

Maybe this accounts for the difference.

---

### Post by koosplegt on 2020-04-29
Thanks for the reply. I looked the system information up with the terminal command 'inxi -G' and turns out to be an Intel 4th Gen Core Processor Integrated Graphics Controller.
If this is what causing troubles, should I wait for the first point release of Xubuntu 20.04 for a fix? This machine has no problems with other systems. I already tried MX-19 without graphics problems and I'm currently running Ubuntu MATE 18.04 on it which runs fine.

---

### Post by CelticWarrior on 2020-04-29
I would wait but it's up to you.

---

### Post by koosplegt on 2020-04-29
I guess I'll wait then. Thanks again!

---

### Post by Dennis N on 2020-04-29
If you've been using Xubuntu 14.04, don't expect it to look the same. It's all changed over to gtk3 now. I would go ahead and install; your 4th generation graphics are definitely supported - one of my computers has the same graphics system. You can adjust themes after install.

---

### Post by koosplegt on 2020-04-30
> **Dennis N said:**
> If you've been using Xubuntu 14.04, don't expect it to look the same. It's all changed over to gtk3 now. I would go ahead and install; your 4th generation graphics are definitely supported - one of my computers has the same graphics system. You can adjust themes after install.

To be clear: I do a clean install every time a new LTS version arrives. I do distro hop a bit, but always on the Debian side of things. Tried MX Linux and Ubuntu Mate recently and I also like to use BunsenLabs now and then (but the current version is still based on Debian 9). However, I feel the most comfortable with Xubuntu. So I wanted to do a clean install of Xubuntu 20.04.

---

