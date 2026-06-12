---
title: "Upgrade renamed my Wireless card"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by WoodyMahan on 2006-06-05
After upgrading to DApper 6.06 My wireless card is no longer recognized as wlan0.  It is now eth1 and cannot connect to my network.  Anyone else seen this?  How do I rename it or reconfigure?

Thanks

---

### Post by jamesrw on 2006-06-05
[QUOTE=WoodyMahan]After upgrading to DApper 6.06 My wireless card is no longer recognized as wlan0.  It is now eth1 and cannot connect to my network.  Anyone else seen this?  How do I rename it or reconfigure?

Thanks[/QUOTE]

same problem.. havent fixed it yet either. cept mine is renamed eth2.

---

### Post by mistamcgoo on 2006-06-05
i am experiencing the same problem with my wifi card, has been renamed from wlan0 to eth1 after upgrade to dapper. 
this is my earlier post about this
[http://www.ubuntuforums.org/showthread.php?t=189146](http://www.ubuntuforums.org/showthread.php?t=189146)

---

### Post by Sam Lars on 2006-06-05
It would really help if you told us what kind of cards you have like mistamcgoo did.  Reinstalling ndiswrapper and the drivers would be a good thing to try first.

---

### Post by jamesrw on 2006-06-05
fixed mine in this thread:

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

ive got broadcom chips

---

### Post by mistamcgoo on 2006-06-05
i read the thread you linked to, but this only seems to apply to broadcom chipsets, 
my us robotics 54mbps G usb stick (see link in my previous post) and my linksys 11mbps pcmcia card in my acer laptop are both installed with ndiswrapper. 
( i havent tried updating my laptop to dapper yet, keeping it on breezy as its my only pc with internet now.)

i tried several things, but i couldn't get it to work. now i downloaded an iso, 
and made a fresh install, with the usb stick out. after installing, i rebooted with the stick plugged in again, and it still gives it the eth1 name instead of wlan0
and the
 sudo iwconfig eth1 essid mynetname key xxxxxxxxxx 
command still gives the same error as before. 
Plus now i found a second problem, there seems to be no ndiswrapper? 
In breezy, i just installed a package called ndiswrapper-tools from the cdrom repo, and it worked. i had both my cards working in no time. 
 
I cant find it anywhere now , and the sudo ndiswrapper -i drivername.inf returns
"command not found". Is ndiswrapper no longer in ubuntu? 
it was still working after i did the upgrade. (or still seemed to be working at least) 

i really hope my only solution won't be going back to breezy :confused:

---

### Post by jamesrw on 2006-06-05
i believe it is ndiswrapper-utils.. try that instead.. you might have to have universe enabled in your repositories.

---

### Post by Sam Lars on 2006-06-05
Just FYI, mistamcgoo, the Linksys should work with that thread, since they're Broadcom chipsets.

---

### Post by mistamcgoo on 2006-06-06
@sam lars, thank yo for the info, but are you sure? i am rather noobish at this myself. 
when, on my laptop(still breezy) i type 
lspci | grep command in your guide, the prompt returns nothing
when i just do lspci, this is the last line : 
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
so i  supposed these were realtek chipsets? will this still work with your guide?
( i really want to be sure, if i lose the wifi connection on this laptop, i'm out of an internet connection :( )

edit : @ jamesrw, i doublechecked, but i cant find anything about ndis, i enabled the universe repo
         but nothing comes up through search.  strangely enough, i just edited the sources list on my laptop(change references from breezy to dapper)
        and when i clicked reload in adept (i run kubuntu on my laptop forgot to mention earlier) and  searched or ndis it does give me ndiswrapper source, utils and even a graphic front end for it. How come this is not in ubuntu's synaptic? are the ndiswrapper packages only available trough download? 
(my laptop does still have an internet connection, havent actually upgraded it, just changed the sources list. My desktop has no internet connection at all atm)

---

### Post by jamesrw on 2006-06-06
strange.. as I have ndiswrapper utils/source coming up in synaptic(Dapper)... here is my sources.list:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricteddeb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

---

### Post by mistamcgoo on 2006-06-09
My wifi connection is up :). 
I simply coplied the ndiswrapper deb file from the cdrom and installed it from desktop. 

in my first thread (the on i linked to in my first reply here) about 
ranf told me to blacklist islsm, and i got it to work now :)
it seems like dapper tried to use a native driver for my card.

---

