---
title: "Ubuntu 13.10:   Installation nvidia driver on card NVIDIA geoforce GT740M"
date: 2013-12-27
forum: Installation &amp; Upgrades
---

### Post by sgxnew54 on 2013-12-27
Hi everybody,
I installed Ubuntu 13.10 (dual boot windows 8) on my PC/Toshiba satellite i5 with a card video Geoforce GT740M and everyting was perfectly working.

After I tried to install manualy the nvidia-331 driver (last driver) driver as follows: 

[COLOR=#008080][B]sudo add-apt-repository ppa:mad:org-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331.[/B][/COLOR][COLOR=#008080]

[/COLOR]But after reboot I had the screen user&password and after the **black screen**.

So then I Tried to install another driver "**nvidia-current**" from a terminal  
 #  s**udo apt-get install nvidia-current ** 
  and rebbot but I had the same result as above, i.e. the black screen.


Please can you help me to correct the error, if possible, or restore the original video settings ??.

thank you in advance.
Sandro

---

### Post by Accidus on 2014-01-02
I have the same problem: when I install either nvidia-current or primus, and restart the notebook, when I log in I get a black screen with a mouse pointer. Purging everything and restarting fixes the problem. 

I am happy to provide other information if necessary or run further analysis if told what it is, it's just that I don't know what to do.

I'm using 13.10 on a  Toshiba Satellite P855-335, the graphics card is GeForce 640M

---

