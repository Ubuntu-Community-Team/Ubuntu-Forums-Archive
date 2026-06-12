---
title: "Problem installing on laptop"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by LighterThief on 2012-03-15
I've been running Dual boot Ubuntu on my desktop for a week or so now and quite like it. However, yesterday I tried installing ubuntu 11.10 on my laptop but run into a problem trying to set up the wireless connection during the instalation. My desktop runs from a wired DSL line which then goes to a linksys wireless router which my laptop uses so I can move around the house with it. After a couple of tries my laptop picked up that there was a wireless signal but kept telling me I was using the wrong pass key. I logged into my router and double checked all the settings and pass and everything appeared to be in order but yet I kept running into the same problem. That's when I got on my PC and run 'ifconfig' and noticed it didn't list 'wlan0' which i'm guessing it should. I googled around for the better part of 90 minutes and still couldn't find anything that helped me solve the problem.   I have no problems connecting with my laptop using Win7 and in the past when i have run an older version of Ubuntu on my laptop (Custom version of 8.10 iirc) with the same setup I had no problems setting it up either. I don't have that much experience with Linux so if someone could help me out or even point me in the right direction it would be greatly appreciated.

---

### Post by wojox on 2012-03-15
Plug in an Ethernet cable and do your install. You can then download your wireless driver from the repo's after.

---

### Post by varunendra on 2012-03-16
> **wojox said:**
> Plug in an Ethernet cable and do your install. You can then download your wireless driver from the repo's after.
Since the laptop is detecting a wireless signal, it means the driver has been already picked up and working. But yes, it may be a wrong one in some cases.

@*LighterThief*,
Please open a terminal, and run & post the outputs of the following commands:
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
cat etc/network/interfaces
rfkill list all
iwlist scan
```
While posting the outputs, click on **# **at the top of the edit box (in which you create new posts) to auto-generate [ code] and  [ /code] tags, then copy-paste the output code in-between those tags.

---

### Post by LighterThief on 2012-03-16
Did you want me to do that from my desktop or the laptop once I install with it pluged in to the ethernet cable? I'm going to try the laptop again this afternoon

---

### Post by varunendra on 2012-03-16
From your laptop.

---

