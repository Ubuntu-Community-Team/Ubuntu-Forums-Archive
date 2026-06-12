---
title: "Run from CD"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by zeke1312 on 2011-06-30
New to Ubuntu. I'm trying to run Ubuntu from a CD before I attempt a full install. When I try to log onto Firefox it fails, then after a minute or two, my wireless router asks for authentication which I already given before my attempt to log onto Firefox. Ubuntu is "online" or appears to be because I can log off my router and Ubuntu shows I've logged off. Can you help? Thank you

---

### Post by mastablasta on 2011-06-30
> **zeke1312 said:**
> When I try to log onto Firefox it fails, 
there is no logging in to Firefox. you just start it and use it.
 
> 
then after a minute or two, my wireless router asks for authentication which I already given before my attempt to log onto Firefox. Ubuntu is "online" or appears to be because I can log off my router and Ubuntu shows I've logged off. Can you help? Thank you
 
in network manager you need to click on it and find your network. then give it your authentication for the network. it might also ask you for additional password. i think this second one is to lock your network password on computer so you dont' have to type it in every time.
 
oh make sure you have propper type of access selected (WEP or more likely WEP2). and you should be good to go.
 
especially if your wi-fi card is working.

---

### Post by zeke1312 on 2011-06-30
Yes, I have done all that. I currently have a desktop,notebook and an android communicating to my router OK for many months. I'm trying the CD version (11.04) on the notebook. I had the full version running (10) on my desktop and communicating OK.

---

### Post by mörgæs on 2011-06-30
How does it run if you use wired internet connection?

---

### Post by varunendra on 2011-07-02
Can you post outputs of:
```
lshw -C network
``````
ifconfig -a
```while it appears connected to the wifi.. (do not use wired connection while running ifconfig)
and..
```
dmesg | tail -20
```
when it gets disconnected (asks for passkey)

---

### Post by zeke1312 on 2011-07-02
Thank you. I used a password which included alpha and I am now connected. Hummm...but it does work now!

---

