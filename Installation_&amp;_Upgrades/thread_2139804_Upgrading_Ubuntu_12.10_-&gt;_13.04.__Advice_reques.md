---
title: "Upgrading Ubuntu 12.10 -&gt; 13.04.  Advice request."
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by felkar on 2013-04-27
I note the info posted on my "upgrader" :

 [COLOR=#ff0000]Welcome to Ubuntu 13.04 'Raring Ringtail'[/COLOR][COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]The Ubuntu team is proud to announce Ubuntu 13.04 'Raring Ringtail'.[/COLOR]
 
and would welcome "belt and braces" advice on how to undertake the upgrade.

Since I am new to Ubuntu and my network-access is temperamental, I would prefer to burn a DVD and then use it for the upgarde.

I am especially keen to hold on to the installed Ubuntu 12.10 (which works perfectly and does all that I need) until I am reasonably certain that the "upgrade" has worked.

If relevant documentation exists, please point me to it.

Thank you

felkar

---

### Post by BlinkinCat on 2013-04-27
Hi,

Is this what you are after?

[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

Cheers - :)

---

### Post by gordintoronto on 2013-04-28
Unless there is a specific reason you want to use 13.04, you don't actually need to upgrade. If you do upgrade, you will also need to upgrade when 13.10 and 14.04 come out. (14.04 will be a long-term support release, so you can stick with it for up to five years.)

I never upgrade, I always do a fresh install. I have separate root and home partitions, so my data is undisturbed. Even so, I always have two backups; all it takes is one wrong answer, and "poof," it's all gone.

Here's some interesting reading: [http://askubuntu.com/questions/202945/how-to-upgrade-from-12-04-to-12-10-using-cd](http://askubuntu.com/questions/202945/how-to-upgrade-from-12-04-to-12-10-using-cd)

---

### Post by Mark Phelps on 2013-04-28
I wouldn't upgrade just yet, if I were you.  Due to limited testing, it takes a month or so for new bugs to be identified and fixed with each new release.  You do better waiting a while and monitoring the forums to see what gets identified.

And, when you are ready to upgrade, before you do that, install Clonezilla and image off your current setup to an external drive. Why? Because there is no roll-back capability that will allow you to restore what you have now.  So, if the upgrade goes badly, you are stuck having to fix it.

---

### Post by felkar on 2013-04-29
[QUOTE=gordintoronto;12623199]

I **never **upgrade, I always do a fresh install. I have separate root and home partitions, so my data is undisturbed. Even so, I always have two backups; all it takes is one wrong answer, and "poof," it's all gone./QUOTE]

I would like to thank [COLOR=#000000]Mark Phelps,[/COLOR] [COLOR=#000000]gordintoront and [/COLOR][COLOR=#000000]BlinkinCat for their prompt and helpful replies.
[/COLOR]
I believe that the advice (quoted above) addresses all my worries.  While I am very new to Ubuntu, I have burned my fingers badly with "Debian Upgrades".  

Based on my experience with installing Ubunto 12.10 on a newly-purchased desktop, a "fresh install" with Ubuntu was a dream-ride.  And, given that I now use the services offered by "Ubuntu 1" to store a "continually updated" personal Documents and Downloads, a fresh install of the "long term release" (on an empty partition) is likely to do all that I need.

Again, sincere thanks!

felkar

---

### Post by grahammechanical on 2013-04-29
> [COLOR=#000000] am especially keen to hold on to the installed Ubuntu 12.10[/COLOR]

The only way you can do that is to burn an ISO of 13.04 and install it in another partition and dual or triple boot. Once we have upgraded to a newer version we cannot revert back should we not like it. If things go wrong we (that is you) will have to fix the problems. So, watch the forums. See what issues others are having and try to figure out what needs to be done to fix those problems. Just in case you have them.

I am running 13.04 but I recommend that you hold on to 12.10. It has enough support to get you to 14.04. Ubuntu 13.04 does not have enough support to get you to 14.04, the next LTS. You would have to upgrade to 13.10 and then to 14.04.

You should use the intervening months to learn to fresh install. I would recommend a fresh install of 14.04. I expect the underlying OS to be very different by the time we get to 14.04. 

From now on we should consider a basic principle for using Ubuntu. If you want stability install an LTS release. Just for the record so that no one thinks I am putting down Ubuntu. I will be moving on to 13.10 and then 14.04. But I am also running the development branch at the same time.

Regards.

---

### Post by BazBear on 2013-04-29
I did the upgrade from Lubuntu 12.10 to 13.04 yesterday and it went flawlessly (Asus Eee PC 1005HA dual boot with Win7). I did, however, back everything up, and made sure I had a copy of 12.10 to install just in case. I know a clean install is more ideal, but I didn't want to go through the hassle of installing all the software I prefer and getting everything configured the way I had it. The upgrade, of course, installed all of the Lubuntu default apps I previously replaced and removed from 12.10, so I just needed to spend a few minutes removing them.

---

### Post by felkar on 2013-04-30
> **BazBear said:**
>  I know a clean install is more ideal, but I didn't want to go through the hassle of installing all the software I prefer and getting everything configured the way I had it. 

Avoiding that hassle is the attraction of the "upgrade" route.

And I will not know just how big the hassle is before I have installed a new release of Ubuntu.  Are there likely to be any "booting problems" if I install a new version of Ubuntu on a different partition of my HD? 

 I may need to become more familiar with Ubuntu's "boot" program (GRUB 2?) to handle a "multi-boot" set-up. At present, my previous (Debian) OS has been copied to a different partition on my new HD and can be mounted and accessed from the loaded Ubuntu 12.10.

Given that Ubuntu 12.10 has all the features that I use, I favour the previously-posted advice to stick with it until the next long-term release becomes available.

Thank you for the advice.

felkar

---

### Post by darkod on 2013-05-01
> **grahammechanical said:**
> 

I am running 13.04 but I recommend that you hold on to 12.10. It has enough support to get you to 14.04. Ubuntu 13.04 does not have enough support to get you to 14.04, the next LTS. You would have to upgrade to 13.10 and then to 14.04.



You made a bug here. :)

Both 12.10 and 13.04 are non-LTS releases, and if the older one can get you to the next 14.04 LTS then the newer one can certainly get you there. 12.10 has 18 months of support, so yes, it can get you to 14.04 just barely. 13.04 is only a year from 14.04 and can definitely cover the period until the next LTS comes out. It can even cover the period until the first point release 14.04.1 which is the best moment to install a new LTS (main problems noticed in the release hopefully solved).

As for upgrading to the next LTS, it depends what we are talking about. From both 12.10 and 13.04 you can't upgrade online directly to the next LTS. You will have to go release by release, and from 13.04 there is one upgrade less to do.
But with the upgrade option the cd/dvd gives you in the latest releases, I guess you could use this to upgrade directly to 14.04 from both 12.10 and 13.04. That seems to be the only way to upgrade directly.

---

### Post by felkar on 2013-05-02
> **darkod said:**
>  with the upgrade option the cd/dvd gives you in the latest releases, I guess you could use this to **upgrade directly to 14.04 **from both 12.10 and 13.04. That seems to be the only way to upgrade directly.

Currently, I do not understand how this option would work.  I was envisaging  that I had to do a "new install" of Ubuntu 14.04 on a different partition of my HD, followed by reconfiguring with the help of the info in my Ubuntu 12.10 partition.

However, I have 12 months in which to come to grips with alternative routines.

Once again, my thanks to all who have been good enough to share their "update experiences".

felkar

---

### Post by BazBear on 2013-05-03
> **felkar said:**
> Avoiding that hassle is the attraction of the "upgrade" route.

And I will not know just how big the hassle is before I have installed a new release of Ubuntu.  Are there likely to be any "booting problems" if I install a new version of Ubuntu on a different partition of my HD? 

 I may need to become more familiar with Ubuntu's "boot" program (GRUB 2?) to handle a "multi-boot" set-up. At present, my previous (Debian) OS has been copied to a different partition on my new HD and can be mounted and accessed from the loaded Ubuntu 12.10.

Given that Ubuntu 12.10 has all the features that I use, I favour the previously-posted advice to stick with it until the next long-term release becomes available.

Thank you for the advice.

felkarOh okay, you're thinking of going with a tri-boot system. I know GRUB can be set up to do it, but that's about all I know about it. Back to your regularly scheduled posters who (usually) know what they are talking about :)

---

