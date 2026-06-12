---
title: "is it safe tu update 10.10?"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by silentrock on 2010-10-07
Im running lucid (dual boot),i heard that Maverick is going to come with freaking great new features,im kidna curious about this.

But is it recommended to upgrade? 

How much time (aprox) should it take?

What problems could i face ?

---

### Post by sikander3786 on 2010-10-07
> But is it recommended to upgrade?

Recommended in the sense if you yourself want to upgrade. Not necessary until support for your current release expires.

> How much time (aprox) should it take?

Depends on your internet connection speed. With my 8 MBPs, it took about an hour or so to complete.

> What problems could i face ?

If successful, there should be no problems at all.

If unsuccessful for any reason, you might have broken packages, unmet dependencies, blank screen, system freezes etc etc. I am not freaking you. Just relax. There is no apparent reason for it to be unsuccessful.

And this time upgrade from 10.04.1 > 10.10 RC has been the smoothest upgrade of my Ubuntu history. I'm quite pleased, so you will also be...

---

### Post by 0N3 on 2010-10-07
It's always best to do a fresh install you will encounter less problems if your lucky you may encounter no problems but my advice is a fresh install

---

### Post by QIII on 2010-10-07
Not necessary.  You have an LTS.  If it is running well, you can leave it as it is.  If you really want the new stuff, give Maverick a few weeks and watch the forums for comments.  Don't bust your gut in anticipation.  There is no need to buy the new 2011 Belchfire 5000 automobile just because of the advertising hype.

Personally, I haven't had any problems with Maverick since the Beta and I put the RC on my daily driver when the ATI driver was available in the repo.

If you are going to upgrade, make sure you are fully updated/upgraded for Lucid first.  Then, *completely *remove your video driver.  Install it again after you upgrade.  This has caused many a headache and post on the forum.

ON3's comment is my preferred route.  But you need not do it that way.  

If you have separate /home, it might be just as easy to reinstall,  leaving your /home alone when you get to the partitioning section.   Upgrading works in the vast majority of cases.  Your chances of having  problems are pretty small.  But this is an option.  

Before you go this route, uninstall your video driver.  Why?  Because  you'll probably want to reinstall your apps (see following).  If the  driver is there, it will be caught up in this and may cause you some  grief.

 ```
dpkg --get-selections > selections.txt
``` This makes a list of your apps to use later.
 
 If your video driver is installed, you will get it in that list and you  may have trouble when you reinstall your apps.  If you get rid of it beforehand, you can just reinstall the video  driver when you get done.

 Note:  I like to save a copy of files like /etc/hosts to my /home so I  can copy them back or pick through them to remember what I had added.

Then, make a backup copy of *all *of the contents of /home by using CTRL+H to make the hidden files visible.  Copy it *all *to some place you can get back to if disaster strikes.  

After you reinstall, get your apps back:
  
  ```
dpkg --set-selections < selections.txt
```  and then
 
 ```
apt-get update
``` then
  
  ```
apt-get dselect-upgrade
```

---

### Post by sanderd17 on 2010-10-07
> **silentrock said:**
> Im running lucid (dual boot),i heard that Maverick is going to come with freaking great new features,im kidna curious about this.

But is it recommended to upgrade? 

How much time (aprox) should it take?

What problems could i face ?

First of all, the features are not that freaking great new, they were really big from 9.10 to 10.04. From 10.04 to 10.10, there is little changed, a bit more software availiable in the software center is the only big deal.

Since you use a LTS, it's not recommended to upgrade for 3 years. If you can't stand from curiosity, you should upgrade.

Did you have a lot of problems with the prevous ubuntu? If you did, you can be sure those problems will come back if you upgrade via the update manager. In that case, it's best to install ubuntu 10.10 like you installed 10.04, once it works, you can delete 10.04 (or keep that partition until 11.04 if you don't need that much space).

If you install at the first day of release, you need to count a server downtime. If that happens, you can be downloading for a few hours. Nothing bad, you can still use your computer while downloading but you can't travel with it. If you wait a few days, the download will go faster.

---

### Post by sikander3786 on 2010-10-07
@QIII

> Not necessary. You have an LTS. If it is running well, you can leave it as it is. 

@sanderd17

> Since you use a LTS, it's not recommended to upgrade for 3 years.

Come on guys, if that is the case, the developers should put their efforts in the LTS releases, follow a debian release cycle and forget about the short term releases.

Who says it is not recommended to upgrade from an LTS release? The purpose itself dies if everyone is going to stick to LTS for 2-3 years. I'll say, for lazy and inexperienced users, LTS is the way to go. For enthusiasts, well they fall for alpha/beta/rc whatever they see. And who'll do the testing and report bugs if they were not there?

---

### Post by QIII on 2010-10-08
Notice that I said "not necessary" and not "not recommended".  Notice that I said he *can *leave it as is, not that he *should *leave it as is.  Also notice that I said wait a bit.

Then I said how to do it.  I, and many others, use the latest as soon as it is available (or before the Final, if it seems to be in good order.)

I would have to ask a couple of questions back:  Why even do an LTS?  Why *not *continue development of new releases even though you know people stick with an LTS to LTS cycle?  If you are a newcomer, why *not *use an LTS while you work at getting your skills developed?

I did not say the OP *shouldn't *upgrade.  He simply doesn't *have *to buy the latest model just because they added more chrome.

---

### Post by msmx5s on 2010-10-08
I upgraded to 10.10 no problems. I did have probs with 10.4 for ethernet and video drivers, but the upgrade didn't do anything to the old work around. 

I do have a couple of questions though... Now I have 10.10 RC installed, what happens when 10.10 comes out properly? Does it upgrade again, or does it stay the same with maybe a few updates?

---

### Post by ezsit on 2010-10-08
> Im running lucid (dual boot),i heard that Maverick is going to come with freaking great new features,im kidna curious about this.

If Lucid is running fine, I would not bother upgrading. The differences betweeen Lucid and Maverick are almost imperceptible. There is a different default font and wallpaper, Nautilus CD Burner is gone, and F-Spot has been replaced with Shotwell for photo management. Other than that, you will probably never notice a difference. There are a lot of kernel changes and new drivers, so if your hardware needs newer drivers, go for it. If you have an Item Atom processor, there have been regressions in the kernel, so avoid upgrading.

> But is it recommended to upgrade?

Only if you want to upgrade. LTS releases like 10.04 have support for three years, so there is no need to upgrade unless you want to.

> How much time (aprox) should it take?

If you try on release day, several hours. If you wait at least a couple of days, much less time as the servers will not be overloaded.

> What problems could i face ?

Normally none. However, you could wipe part or all of your system via software bug or your own fault. So the possibilities are endless. Unless you want to possibly spend hours or days fixing problems, and know how to fix problems, best to wait a few weeks and see what others experience. 

Check the forums and look for similar hardware setups and disk partition layouts to yours and note the problems others are seeing before upgrading your own system. 

And most important, BACKUP your stuff before you do anything!

---

### Post by Dustin2128 on 2010-10-08
no reason not to, but depending on your connection speed, I'd start it just before you go to bed.

---

### Post by QIII on 2010-10-08
> **msmx5s said:**
> Now I have 10.10 RC installed, what happens when 10.10 comes out properly? Does it upgrade again, or does it stay the same with maybe a few updates?

It does not do a "version upgrade".  You are running 10.10.

As you do your normal periodic update/upgrade process, you will have the Release version of Maverick.  No need to reinstall or go through a version upgrade process.  Just keep updating/upgrading as usual.

You will end up with a little bit of dust in the corners when doing this, since packages will be updated and they can leave behind some candy wrappers.  A clean install would not leave behind those remnants.  But the volume is small and it can be cleaned up.

---

### Post by msmx5s on 2010-10-11
TY QIII

I did a clean install... and all is OK :-)

---

