---
title: "Ubuntu installation problem on MSI M670X"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by DanceHatx on 2008-02-03
Hi

Somehow  I cannt install the new ubuntu on my MSI M670X notebook...
I tried to boot from the burned ubuntu live dvd
got into the choice menu
but after I chose the 1. possibility (dont remember exactly, but it was to install the OS)
came a totally black screen...
i had to restart the system!
the second time, the screen was totally white...

what the hell is happening???
and what should I do???

I really wanna use some open source linux, but if its so much trubble, when I even havent installed it...
I cannt even imagine, what is gonna be later...
:S

thanx for the help!!!

---

### Post by overdrank on 2008-02-03
> **DanceHatx said:**
> Hi

Somehow  I cannt install the new ubuntu on my MSI M670X notebook...
I tried to boot from the burned ubuntu live dvd
got into the choice menu
but after I chose the 1. possibility (dont remember exactly, but it was to install the OS)
came a totally black screen...
i had to restart the system!
the second time, the screen was totally white...

what the hell is happening???
and what should I do???

I really wanna use some open source linux, but if its so much trubble, when I even havent installed it...
I cannt even imagine, what is gonna be later...
:S

thanx for the help!!!

HI and welcome, could you tell us some specs on the system and did you check the cd for errors?

---

### Post by DanceHatx on 2008-02-03
thanx!

I guess, I will be a frequent questioner in the future...:)
if Im gonna be able to install the OS...

the notebook specification is here:
[http://www.techbiz.com.ar/catalog/product_info.php?cPath=29_46&products_id=1741](http://www.techbiz.com.ar/catalog/product_info.php?cPath=29_46&products_id=1741)

I havent made a cd check...:S
and I dont have the dvd here with me right now (Im at work)
but then I will do that first, when I got home tomorrow!

---

### Post by overdrank on 2008-02-03
> **DanceHatx said:**
> thanx!

I guess, I will be a frequent questioner in the future...:)
if Im gonna be able to install the OS...

the notebook specification is here:
[http://www.techbiz.com.ar/catalog/product_info.php?cPath=29_46&products_id=1741](http://www.techbiz.com.ar/catalog/product_info.php?cPath=29_46&products_id=1741)

I havent made a cd check...:S
and I dont have the dvd here with me right now (Im at work)
but then I will do that first, when I got home tomorrow!

Ok and if you burned the dvd then you may also want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
The laptop has the nvidia 6100 graphics so you may also try the safe graphics mode. I have read that some user have had issues with using the live cd and installation.

---

### Post by DanceHatx on 2008-02-03
yeah
I was reading around as well!
and have found nicely a lot of problems with this ntb
"lucky me"
:S

do you suggest, i should NOT use the live cd, but the other text based one???

I guess I will download a new iso tonight!

on the forum, was written something about typing in something like noacpi
or something similar
but unfortunately dont even know, where to type this request in, when the system boots...:S
(Im really beginner with everything in IT area:S)

thank you!

---

### Post by overdrank on 2008-02-03
> **DanceHatx said:**
> yeah
I was reading around as well!
and have found nicely a lot of problems with this ntb
"lucky me"
:S

do you suggest, i should NOT use the live cd, but the other text based one???

I guess I will download a new iso tonight!

on the forum, was written something about typing in something like noacpi
or something similar
but unfortunately dont even know, where to type this request in, when the system boots...:S
(Im really beginner with everything in IT area:S)

thank you!

Hi and if you want to install then the alternate cd ( text installer) is a option. But if you are wanting to try before installing then the live cd is the way to go. 
When you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add noapic before the -- then press enter then b for boot and hopefully this will run the livecd.

---

### Post by DanceHatx on 2008-02-03
thanks a lot!
ill try!
and ill be back, if anything...
bye

---

