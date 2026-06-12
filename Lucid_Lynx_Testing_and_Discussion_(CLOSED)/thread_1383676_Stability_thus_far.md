---
title: "Stability thus far?"
date: 2010-01-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2010-01-17
How stable is it this far?  I have intel graphics so i'm wondering if this would be an issue.  Just havent had time to reinstall since it last broke..Advice?

---

### Post by buzzmandt on 2010-01-17
have laptop with intel graphics, no probs at all.  running very good for me both gnome and kde

---

### Post by shwallace on 2010-01-17
I have installed it on a Toshiba laptop with ati mobile radeon graphics. Seems pretty stable so far. No problems with wifi or video, except the brightness applet doesn't seem to work.

---

### Post by dFlyer on 2010-01-17
Ubuntu 9.10 very stable on my laptop with intel graphics since it was released back in October 2009.

Gary

---

### Post by mick222 on 2010-01-17
very stable never even noticed when alpha2 came out got a partial upgrade today libavcodec-extra-52 cant upgrade should i remove it.

---

### Post by buzzmandt on 2010-01-17
> **mick222 said:**
> very stable never even noticed when alpha2 came out got a partial upgrade today libavcodec-extra-52 cant upgrade should i remove it.

nah, just wait a couple days

---

### Post by Ibidem on 2010-01-17
Intel graphics--which ones?
i9xx are working fine, and *some* i8xx; i865 chips work, but it looks like i845 may not be working.  
I'm using 945 graphics, and it works (barring bad builds of X, and some oddball stuff)

Ibidem

---

### Post by sports fan Matt on 2010-01-17
my model: Lenovo IdeaCenter K Series K2.3  Pentium dual-core E2180(2.00GHz) 3GB DDR2 500GB Intel GMA 3100 Desktop

---

### Post by buzzmandt on 2010-01-17
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by sports fan Matt on 2010-01-17
So is this good or bad?

---

### Post by mick222 on 2010-01-17
very good i gave up with karmic alphas as i kept breaking them. Looks like it will be good from the start.

---

### Post by Ibidem on 2010-01-17
Haven't seen any reports of trouble with a 3100 chipset...I'd say try it out.
Of course, I haven't noticed any mention of that chipset at all here, but I think no news is good news, this far along.
Ibidem

---

### Post by sports fan Matt on 2010-01-17
Gonna re upgrade now.

---

### Post by mamamia88 on 2010-01-17
firefox crashes constantly for me.  also, i had the screen go completely black once when saving a jpg to apply as desktop background and had to hard reset it.  have only been running it since this afternoon.

---

### Post by sports fan Matt on 2010-01-18
Firefox will not even open here..crashes upon opening.

---

### Post by Ibidem on 2010-01-18
Working fine for me...
I saw that problem one time: when I had run Firefox as root.
Solution:
Rename/delete/change owner for ~/.Mozilla
This will get rid of any customization/history you have.
Ibidem

---

### Post by sports fan Matt on 2010-01-18
And lose all my customizations?  I really don't understand why i'd have to start fresh when I just upgraded to lucid.

---

### Post by running_rabbit07 on 2010-01-18
I am not using Intel, but I can say the rest of the system is running awesomely. I think the Lynx is going to really be a hit.

---

### Post by running_rabbit07 on 2010-01-18
> **Ibidem said:**
> Working fine for me...
I saw that problem one time: when I had run Firefox as root.
Solution:
Rename/delete/change owner for ~/.Mozilla
This will get rid of any customization/history you have.
Ibidem

Have you been able to try Google Chrome or Epiphany?

---

### Post by sports fan Matt on 2010-01-18
apparently mania and i have the same issue...anyone else have this occur?

---

### Post by Ibidem on 2010-01-18
> **sox fan Matt said:**
> And lose all my customizations?  I really don't understand why i'd have to start fresh when I just upgraded to lucid.
I mean Firefox settings only (not GNOME or anything else), but I would suggest that you check the properties of ~/.Mozilla for the "owner";
(Goto Home, show hidden, right click, Properties)
if you are listed as the owner, it's not what I'm referring to; otherwise, run "gksu Nautilus", goto your home folder, repeat the steps above, and change the owner.
If it asks if you want to apply recursively, make sure it does.
Ibidem

---

### Post by Ibidem on 2010-01-18
@running_rabbit07:Never wanted Chrome, and Epiphany wasn't showing up in Aptitude when I installed.
Besides, I like Firefox, have almost never had issues, and several sites I have to use (school) refuse anything other than Firefox (or *the other browsers*, IE and Safari).
I know about setting the user agent, but why when you've got the real thing?
Ibidem

---

### Post by woodmaster on 2010-01-18
no issues yet with Alpha 2 running off a live CD.  I am not brave enough to do an install yet.  I think I'll wait for stable on that.  Firefox works great.  Forgot it loaded that fast without addons!

---

### Post by sliketymo on 2010-01-18
Running Lucy,with intel 31/33Graphics chipset.Rock solid so far.Epiphany is listed in Software center.Chromium is stable so far(using chromium  daily ppa).I have had no problems with Firefox,also using the daily's.

---

### Post by benny.kallstrom on 2010-01-18
Lucid alpha 2 is running better and faster than Karmic on my HP 6830s laptop.

---

### Post by NCLI on 2010-01-18
I'm still in "Low Graphics Mode" with my Intel 945GME GPU. Hope that stops soon, it's very annoying to use 4:3 on a 16:9 monitor.

---

### Post by jerrylamos on 2010-01-18
> **sox fan Matt said:**
> How stable is it this far?  I have intel graphics so i'm wondering if this would be an issue.  Just havent had time to reinstall since it last broke..Advice?

intel graphics i845G lucid:

Alpha 2 CD live hit enter on the boot choices screen Lucid freezes.  Nothing can be done.

Alpha 1 updated as in sudo apt-get update, apt-get dist-upgrade runs at most briefly then desktop freezes.  Adding "nomodeset" to the linux boot line and keying in an /etc/X11/xorg.conf with "vesa" will run for a few hours anyway.

Alpha 2 alternate CD installed and runs fine, for an Alpha.  Froze up when trying to open a CD.  This is a multi boot karmic, lucid, debian, slax, ... All the rest are released levels and run fine, lucid is still in development and shaky.

Some problems reported with ati video graphics; mine running O.K.

Jerry

---

### Post by sports fan Matt on 2010-01-18
I am the owner..I do know that.  Well, I am just gonna delete my firefox folders and start again.  Not the most ideal solution, but I cant seem to get used to chrome.

---

### Post by philinux on 2010-01-18
> **sox fan Matt said:**
> I am the owner..I do know that.  Well, I am just gonna delete my firefox folders and start again.  Not the most ideal solution, but I cant seem to get used to chrome.

Just back up your bookmarks.

---

### Post by Nickedynick on 2010-01-18
If you're checking out Alpha 2 I'd recommend doing a clean install rather than upgrading from Karmic. As far as I know the upgrade path isn't complete, so issues will crop up - hence your Firefox problems.

I've tried both upgrading and a fresh install, and the freshness works a hell of a lot better.

---

### Post by VMC on 2010-01-18
> **Nickedynick said:**
> If you're checking out Alpha 2 I'd recommend doing a clean install rather than upgrading from Karmic. As far as I know the upgrade path isn't complete, so issues will crop up - hence your Firefox problems.

I've tried both upgrading and a fresh install, and the freshness works a hell of a lot better.

I never go the upgrade route. I just save needed files/programs and do a fresh install. No cruft live here.

---

### Post by Nickedynick on 2010-01-18
Yeah exactly. I've gotten into a habit of manually partitioning to make/keep a separate /home partition now. I really wish there was a simple option to do the same for a standard install - it'd make things a lot easier for newer users.

---

### Post by Arlanthir on 2010-01-18
> **Nickedynick said:**
> Yeah exactly. I've gotten into a habit of manually partitioning to make/keep a separate /home partition now. I really wish there was a simple option to do the same for a standard install - it'd make things a lot easier for newer users.

Don't you have problems with configuration files that live hidden on /home when you upgrade?
Since we're discussing stability, I'm taking the chance to ask how stable is that. I've always wanted to have a separate /home partition, but I'm afraid of the configuration mess that some applications may cause once they're fed files from previous versions.

Ideally, applications should always overwrite the configuration files on install, so, does that happen? :P

---

### Post by nanog on 2010-01-18
> 
I've tried both upgrading and a fresh install, and the freshness works a hell of a lot better.

I disagree. 

Two of my stable boxes are running karmic upgraded all the way from 6.06 and all of my lucid upgrades are running fine (with the exception of a stray kernel bug or two). I also have no problems with cruft.

---

### Post by ranch hand on 2010-01-19
> **sox fan Matt said:**
> And lose all my customizations?  I really don't understand why i'd have to start fresh when I just upgraded to lucid.
Gee Whiz, I would hate to  think that a pre-release OS in Alpha development would have problems that you would not get in a stable release.

Sounds like a darned simple cure to me.  I would put them back one at a time and see which one or two are causing this to happen to you.  File a bug and maybe you will actually help some poor sucker from having this problem AFTER release.  That is what we are here for.

---

### Post by Nickedynick on 2010-01-19
> **nanog said:**
> I disagree. 

Two of my stable boxes are running karmic upgraded all the way from 6.06 and all of my lucid upgrades are running fine (with the exception of a stray kernel bug or two). I also have no problems with cruft.

Did you upgrade recently, or when the toolchain was available? Because it seems that recent upgrades are screwing up.

[QUOTE=Arlanthir]Don't you have problems with configuration files that live hidden on /home when you upgrade?[/QUOTE]

Good point. As long as you use a separate profile while it's in development it's fine. Problems happen using the same profile on 2 different versions, where old config files get written over by newer ones, and consequently things mess up. I tend to have a testing partition and a stable one, when the next release comes out I wipe the testing one and do a fresh install on the stable one so this doesn't happen.

---

### Post by sports fan Matt on 2010-01-19
So far so good.  Whenever I try to clean install though I always have either an issue with the disc at the lowest speed or brasero doing something crazy so I always upgrade.  I try to not do a clean install until once I have the disc.  (I know not fun, but it works)

---

### Post by Jordanwb on 2010-01-19
[IMG]http://img11.imageshack.us/img11/1825/yosemite20winter.jpg[/IMG]

Rock solid.

---

### Post by nanog on 2010-01-21
> Did you upgrade recently, or when the toolchain was available? Because it seems that recent upgrades are screwing up.

I upgraded during alpha1 and pre-alpha1.  I plan on trying alpha2 this weekend. There should be a sticky that describes how to recover from upgrade problems (e.g. chroot and basic dpkg). 



> Don't you have problems with configuration files that live hidden on /home when you upgrade?

One of the most annoying things about dpkg is that it no longer removes usr config files when purging. I understand why but there should be an option or flag!
*shakes fist in air* 
I delete the many annoying ~/.* folders deposited by miscellaneous applications.

---

