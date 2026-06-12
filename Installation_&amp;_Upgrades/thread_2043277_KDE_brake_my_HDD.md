---
title: "KDE brake my HDD"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by filip007 on 2012-08-16
Well i was formating using auto-install than it's stopped at 33% and damage my hard drive, i have created custom install, but the damage has been done!
 
I know this is not a new problem, but todays HDD are getting pretty sensitive, you better check on that. 

...and no i can't repair it, if official Hitachi tools says error, it's error, can't do much more i guess. 

And what was the problem, massive bad sectors fallout, i have also check logs from HDD it self and it shows, time logs when i was trying to install KDE so before was OK.:mad:

---

### Post by cortman on 2012-08-16
> **filip007 said:**
> Well i was formating using auto-install than it's stopped at 33% and damage my hard drive, i have created custom install, but the damage has been done!
 
I know this is not a new problem, but todays HDD are getting pretty sensitive, you better check on that. 

...and no i can't repair it, if official Hitachi tools says error, it's error, can't do much more i guess. 

And what was the problem, massive bad sectors fallout, i have also check logs from HDD it self and it shows, time logs when i was trying to install KDE so before was OK.:mad:

So your point is... ?

In the first sentence you're formatting the drive. In the last you're installing KDE and saying that that was the problem. ??

All hard drives will die. Bad sectors are a physical anomaly, not software related.

Likely your problem isn't bad sectors but an incomplete or corrupted partition table, which you can fix by booting to a LiveCD and repartitioning with GParted.

---

### Post by filip007 on 2012-08-16
Just ranting on KDE that's all and no it can't be formated, that's the problem it's kaput. Ok my board is to blame, GA 770T UD3, all stuff practically new or unused.:confused: 

If you agree that KDE formating is a bit different than others.

---

### Post by mastablasta on 2012-08-16
> **filip007 said:**
> Just ranting on KDE that's all and no it can't be formated, that's the problem it's kaput. Ok my board is to blame, GA 770T UD3, all stuff practically new or unused.:confused: 
 
If you agree that KDE formating is a bit different than others.
 
KDE is a desktop environment. it's way of formating is exactly the same as in others. 
 
 
As it was mentioned only the partition table likely got corrupted. this can be fixed with tools such as gparted or kde partition manager (parted anyway...). 
 
additionally i have a disk thta refused to work in windows and to boot widnows form it. it keep getting "corrupted". i formated it as ext4 and added it to linux maschine. so far, so good. no errors noted.

---

### Post by filip007 on 2012-08-17
No it's no, KDE use a bit different install as auto-install goes if compared to Ubuntu. Well custom install did finish the job like i said before.

Windows install worked but showing bad sectors, if checked with Smart tool, formating did not solve it so that's that. 

I'm getting another drive, but now i am afraid what will happen if i try the same.:confused:

What i see KDE done wrong calculation on formating and destroy my HDD. 

I used 500GB Hitachi on Ga 770T UD3 board, if someone else will dig out what went wrong here.

---

### Post by Codify on 2012-08-17
So the HDD is new? Why don't you download DBan and nuke the drive, then try to install whichever OS you want. DBan will completely erase the drive including your bad sectors. If they are really bad sectors they will show up again when you format the drive but this is one way of giving your drive a second chance.

---

### Post by filip007 on 2012-08-17
It was 155 days and 77 hours old, that all.

I doubt it...or it was wrong partition calculation or Hitachi is not compatible with KDE auto-install, Smart output don't lie.

I have another Hitachi at home, but i don't want to experiment, it works just fine for 5 years in another machine.

---

### Post by tartalo on 2012-08-17
> **filip007 said:**
> It was 155 days and 77 hours old

It's still under guarantee, ask for a replacement.

---

### Post by cortman on 2012-08-17
> **filip007 said:**
> No it's no, KDE use a bit different install as auto-install goes if compared to Ubuntu. Well custom install did finish the job like i said before.

Windows install worked but showing bad sectors, if checked with Smart tool, formating did not solve it so that's that. 

I'm getting another drive, but now i am afraid what will happen if i try the same.:confused:

What i see KDE done wrong calculation on formating and destroy my HDD. 

I used 500GB Hitachi on Ga 770T UD3 board, if someone else will dig out what went wrong here.

If it's bad sectors, it's in no possible way related to software.

Plus, if you had Windows on it before and it showed bad sectors, why are you blaming it on Ubuntu? 

I'd drop the KDE bone and do a little research on what programs actually do the formatting, if for no other reason so that your posts look a little better informed.

---

### Post by filip007 on 2012-08-18
1.) No, i had Kubuntu first thing on, then Windows later to check more in depth with Smart output.

2.) I guess nobody is using KDE with Hitachi drive that's too bad. 

3.) KDE formating process is not equal to Ubuntu.

4.) Ubuntu is cool, just a bit ugly.

---

