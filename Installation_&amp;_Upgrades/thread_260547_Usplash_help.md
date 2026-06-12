---
title: "Usplash help"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by fokuslee on 2006-09-18
i just followed the guide from tseliot and compiled my own kernel 
now to use Usplash the guide did not work for me 100% 
but thx to jrib at #ubuntu i was able to figure this out 

type: sudo nano -w /etc/mkinitramfs/module
then type
capability 
vesafb 
fbcon 
unix
then save and exit 
now 
sudo dpkg-reconfigure kernel-image-`uname -r` did not work for me 
so i had to
sudo -s -H 
then type  
dpkg-reconfigure kernel-image-`uname -r` 

dono why this worked but it worked for me hope this helps someone.

ps. oh and MOD if u find this to be complete jibberish just delete my post cuz im a total linux nub 
:D

---

