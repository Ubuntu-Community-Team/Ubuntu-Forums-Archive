---
title: "INSTALLING 10.04 on HP DV6-2155dx"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by fremantle on 2010-06-26
Tomorrow morning im going to my cousin's house to install ubuntu lucid lynx on his hp  DV6-2155dx. right now he has windows 7 which is heavily infected with malwares and viruses, he cant even access the internet. all i need to know is, will wireless work after a clean installation of 10.04 on hp  DV6-2155dx?

---

### Post by hansdown on 2010-06-26
Hi fremantle.

Try ubuntu with no changes to your computer with the live CD.

You can test everything to be sure it works, before installing.

---

### Post by Hman242 on 2010-06-26
> **hansdown said:**
> Hi fremantle.

Try ubuntu with no changes to your computer with the live CD.

You can test everything to be sure it works, before installing.
+1

Also, if it helps, I have an HP dv7 that had it's wireless work out of the box.

---

### Post by fremantle on 2010-06-26
yes, but i HAVE to install it and just wanted to know if the wifi didnt work out of the box what tools i needed to make it work (like fwcutter) oz he doesnt have another computer, ethernet conn, and windows is dead.

---

### Post by fremantle on 2010-06-26
> **Hman242 said:**
> +1

Also, if it helps, I have an HP dv7 that had it's wireless work out of the box.
 
cool! than i guess his one will work too ):P

---

### Post by CodigoVision on 2011-01-05
I am running Ubuntu 10.10 (first installed 10.04 before upgrading to 10.10) on my HP DV6-2155dx, here are my results:

Sound: Speakers do not turn off when you plug in headphones.
Solution...
in terminal:
gksudo gedit /etc/modprobe.d/alsa-base.conf
 add this line to the very bottom:
options snd-hda-intel model=hp-dv5
 save and restart :)
 Everything else is working great, wireless works out of the box.
 
Got the remote working
basically you need to install lirc and configure 3 files see the link below for detailed instructions. [http://www.codigovision.com/ubuntu-1004-hp-dv6-2155dx](http://www.codigovision.com/ubuntu-1004-hp-dv6-2155dx)

---

