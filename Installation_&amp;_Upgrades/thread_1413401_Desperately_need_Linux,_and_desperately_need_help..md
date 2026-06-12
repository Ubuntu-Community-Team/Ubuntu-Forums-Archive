---
title: "Desperately need Linux, and desperately need help..."
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by Veteropinguis on 2010-02-22
I'm on vacation with my family for 3 weeks in France. I brought my netbook so I could continue to keep up with my homework, which amounts to a lot of typing and editing some TIF files.

Problem: Windows 7 isn't compatible with the router/modem I have access to, so I have no internet access in the apartment we've rented. I know that it works, because I'm using the apartment owner's ancient anemic desktop. Can't do homework on this though.

Problem 2: I have Windows 7 Starter, so I can't use compatibility mode, so I can't use Wubi.

Problem 3: I don't have an optical drive and have just a 512mb flash drive which may not work, so I'm not sure how to fix this.

Problem 4: I don't have a Windows 7 backup disc; never received one.

Problem 5: My dad works with copyright and intellectual property so he'd notice if I pirated Windows and would be extremely not okay with it.

I could probably buy a bigger flash drive if I really had to, hopefully they're not too expensive. I am most comfortqble with Ubuntu but I will use whatever will run the Gimp (or some TIF editor) and Firefox. I cannot afford to get 3 weeks behind on my homework.

I've only been off the plane for a few hours and am trying to get used to the French keyboard, so I apologize for any typos that slipped through.

Am I as completely screwed as I think I am, or can something be done?

---

### Post by theozzlives on 2010-02-22
you're in a predicament. I'd say if your computer will boot USB, get a bigger flash drive and use unetbootin to copy the Ubuntu install to the flash. Install from there.

---

### Post by solar george on 2010-02-22
fun, fun, fun, anyway maybe you'll have some luck with [slax]("http://www.slax.org").
gimp 2.6.8 is available as an addon

---

### Post by darkod on 2010-02-22
One option: Get a 4GB stick (they should be cheap these days). Create bootable usb startup disc of ubuntu on it. It will take approx 700MB of it. You can use the rest of the stick as long as you don't rename or delete/move the install files/folders.
You can work on ubuntu booted from the stick, and save your work on the remaining unused space on the stick.
That should do the job for you without need to even install on your hdd. Of course, you can install ubuntu on your hdd if you want to, even better solution.

---

### Post by theozzlives on 2010-02-22
> **darkod said:**
> One option: Get a 4GB stick (they should be cheap these days). Create bootable usb startup disc of ubuntu on it. It will take approx 700MB of it. You can use the rest of the stick as long as you don't rename or delete/move the install files/folders.
You can work on ubuntu booted from the stick, and save your work on the remaining unused space on the stick.
That should do the job for you without need to even install on your hdd. Of course, you can install ubuntu on your hdd if you want to, even better solution.

The only way I could make that work is with 2 partitions. I have an 8 GB (4.1 GB FAT32) as sdb1 to be seen by Windows. and the remainder (sdb2) contains a full install of Ubuntu (ext4). That way I can save my data to sdb1 and Windows will still see it.

---

### Post by TusharG on 2010-02-22
Well get 4 GB USB disk and how to install Ubuntu on it???????????
None of he above mentioned option will work.

dude... just get mandriva USB stick and boot it from it. Its available in stores.

---

### Post by darkod on 2010-02-22
> **TusharG said:**
> Well get 4 GB USB disk and how to install Ubuntu on it???????????
None of he above mentioned option will work.

dude... just get mandriva USB stick and boot it from it. Its available in stores.

I never said INSTALL ubuntu on it. I said CREATE usb startup disc of ubuntu. Basically the same like the mandriva you mentioned.

> The only way I could make that work is with 2 partitions.

If you have more than one partition windows can see only the first.

But if you format the whole stick as single FAT32 partition, create it as usb bootable ubuntu stick, there are no problems using the free space remaining as long as you don't delete any of the ubuntu install files.

---

### Post by solar george on 2010-02-22
Well the slax option should work off of his(/her) existing usb disk and can be installed from windows (the anaemic pc mentioned) so should maybe be the first method tried, but other than that i'd agree with TusharG and say that a mandriva key would be the least hassle (as its pre-installed) assuming its available nearby.

---

### Post by AlanR8 on 2010-02-22
> Problem: Windows 7 isn't compatible with the router/modem I have access to

This needs more explaining. Is it a router or is it a modem.

I've never had any problems with any Windows or Linux machines recognising any router and believe me, due to a long undetected power surge, I got through 7 routers in 18 months!

---

### Post by pirateghost on 2010-02-22
> **AlanR8 said:**
> This needs more explaining. Is it a router or is it a modem.


agreed.

it wouldnt matter if it was a modem or a router or both.  network devices like modems and routers are unaware of an OS on the client.  it simply doesnt care.  

i think the problem here is a lack of understanding the modem/router at hand and how to configure the network in windows 7

---

### Post by TusharG on 2010-02-25
> **darkod said:**
> I never said INSTALL ubuntu on it. I said CREATE usb startup disc of ubuntu. Basically the same like the mandriva you mentioned.



That wont work cause for that he needs a internet connection to download Ubuntu and he is unable to connect to internet!

---

### Post by steev182 on 2010-02-25
But how is he able to post on here?

---

### Post by Veteropinguis on 2010-02-27
Okay, I (a she, by the way) ended up spending about 16 hours figuring out how to make Windows 7 play nice with the WEP encryption on the Wanadoo router here. Apparently MS has decided that WEP isn't cool any more so it's a major pain to get any information on how to set it up- most of the advice was to switch to WPA.

However, I have now resolved to get and make a bootable Ubuntu flash drive, for a netbook backup...and to remember to *always* take a LiveCD with me.

Thanks for the advice, though. I will definitely be more prepared in the future.

---

### Post by penguinv on 2010-03-01
> **pirateghost said:**
> agreed.

it wouldnt matter if it was a modem or a router or both.  network devices like modems and routers are unaware of an OS on the client.  it simply doesnt care.  

i think the problem here is a lack of understanding the modem/router at hand and how to configure the network in windows 7

Ah so... (stroking beard)

In EU the internet cafe is really popular and others can help you find and create that stick.

    "Don't be afraid to ask for directions." 

Your ISP can as well. Do not panic. 

jjjay bayz-whaan duh   --- means I have need of ---

aid-eh mwa - SVP  (sill-vue-play)
     help me please

Bon Chance!  
Quelle adventure!

---

### Post by Veteropinguis on 2010-04-12
After a lot of pain and suffering, I got the router working. I had to do a lot of router-resetting and manually screw around with security settings in Windows. But, it worked.

In future, I'm keeping a Live USB around. Just thought I'd let posterity know how this was resolved.

---

