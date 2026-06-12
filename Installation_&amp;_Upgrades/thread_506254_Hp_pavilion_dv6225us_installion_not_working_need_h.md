---
title: "Hp pavilion dv6225us installion not working need help"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by nal on 2007-07-21
I have an HP Pavilion dv6225us laptop with 1gig mem and 512 meg gforce go 6150 graphics card.  I love this laptop cus it screams in windows xp.  I want to switch it to linux really really bad.  But I have nothing but troubles from the get go.  I get a black screen when i try to boot from live cd, which I fixed by option f4 and going to 1020 by 800 for resolution before booting.  Then after I install it will black screen again and thats where I get stumped.  I get a bc43xx error and the laptop will randomly freeze while in terminal.  I can't finish envy to see if that will give me graphics cus of the lockups all the time.  If you can help me I would be really greatfull cus I really really want linux on this beast.  here are my specs.  I cant mod probe or anything atm cus I had to switch back to xp to talk on the forums.

AMD turion64 x2 tl50
richo 5-in-1 built in card reader
sata 120 gig hd
nvidia gforce go 6150 graphics card
nvidia nforce 430/410 serial ata controller
HDAUDIO soft data fax modem with smartcp
nvidia nforce network controller (network card)
broadcom 802.11 b/g  wlan
nvidia network bus enumerator 
Conexant HD audio


hope all that helps.

---

### Post by Pumalite on 2007-07-21
Try the Alternate CD.

---

### Post by nal on 2007-07-21
just finished the alternate and same thing.

---

### Post by Pumalite on 2007-07-21
Can't you enter to a command line at all?

---

### Post by nal on 2007-07-21
yea I got to command line, thats where it locks up alot.  I try to use envy, apt-get anything, after a few mins it locks up. oh by terminal i ment command line

---

### Post by Pumalite on 2007-07-21
Try this:

dpkg-reconfigure xserver-xorg

Most defaults will be ok. Coose 'vesa' as the driver. Then 'startx'

---

### Post by rksingh54 on 2008-05-26
I hope you succeeded in installing UBUNTU 8.04 Hardy Heron. I have the same model and I was successful in installing UBUNTU with the aid of a live CD. One thing that is still I am working on is WLAN. That has been a true challenge

RKS

---

