---
title: "ubuntu 7.04 upgrade ?"
date: 2013-12-11
forum: Installation &amp; Upgrades
---

### Post by jnorthr on 2013-12-11
my trusty old circa 2000 laptop with 256mb and dvd reader just lost it's hard disk. Luckily i had an old 20gb hard disk that i had installed 7.04 on and my lap works well. But i do not have an internet connection just a dvd reader so how can i bring my 7.04 install up to date ? or is this even possible without a full re-install ?? am guessing i'd need synaptic package manager and change the sources to look at a dvd - which one do i use for an i386 system ? :confused:

---

### Post by protoss96 on 2013-12-11
Hi **jnorthr**,

Why you just don't install newest Xubuntu or Lubuntu they are very lightweight btw? I think you can upgrade to 7.10 then from 7.10 to 8.04 and so on... You can download image from here:
```
http://old-releases.ubuntu.com/releases/7.10/
```

And btw you should move repositories if you want upgrades.

---

### Post by Kirboosy on 2013-12-11
As protoss96 stated you will have to go from 7.04 to 7.10 to 8.04. 

Once you hit 8.04 you would be able to jump from 8.04 LTS to 10.04 LTS to 12.04 LTS...14.04 LTS is coming out in April so at that point you could jump to the next LTS if you wish.

If you do update from 7.04 to where you want to be you will need to burn CDs/DVDs for the computer to upgrade to each new revision. So lets say it will take you, 4 CDs at a minimum if you decide to stick with 12.04 LTS. 

I would recommend fresh installing Lubuntu on your computer. Just back it up and reinstall it from scratch. You will be much happier with the process. It will be extremely slow and tedious to upgrade each release. 

Hope that helps!
~Caboose

---

### Post by Elfy on 2013-12-11
I would just bite the bullet and wish that I'd done something about upgrading over the last 7 years.

Reinstall to a newer version, back up things you need to keep.

---

### Post by jnorthr on 2014-01-12
old laptop just rebuilt though hard drive had a nice install of ubuntu 7.04. as i now have wireless again, tried 'updates' option from the menu but said 'cannot find network or cannot locate ubuntu 8.04 for upgrade. any anyone point me to a repo for 8.04 or alternatively how to manually fast-forward my version ? i have a dvd reader so could theoretically put a ubuntu 13.10 dvd and rebuild from there but don't want to blitz all my work and setups. any ideas ?
thx :confused:

---

### Post by ahmad7jafari on 2014-01-12
Hi
maybe useful;
[https://help.ubuntu.com/community/EOLUpgrades/Feisty](https://help.ubuntu.com/community/EOLUpgrades/Feisty)
[https://help.ubuntu.com/community/UpgradeNotes#Ubuntu_7.04_.28Feisty_Fawn.29](https://help.ubuntu.com/community/UpgradeNotes#Ubuntu_7.04_.28Feisty_Fawn.29)

---

### Post by QIII on 2014-01-12
Hello!

The answer to the question is yes -- technically.  But the old versions have been moved and that is why you can't find an upgrade.

The ***practical ***answer to the question is no.  The way you would have to upgrade would probably lead to compounded problems -- you have to do a series of upgrades that might introduce errors at each step and leave a mess at the end.

Could you give us the hardware specifications of your machine and we'll see if using a more recent version has a reasonable chance of success.

---

### Post by Bucky Ball on 2014-01-12
The config files will probably not work on a 13.10 install as the apps you are using have changed so much since 7.04 (wow! First release I ever tried). 

You would be much better to do a clean install of 13.10 and reconfigure, upgrade to the long-term support release directly from there in April (five years support which sounds like it might suit you). 

The other issue is ... Unity. Some love it, some hate it, but be aware, that is the default desktop environment Ubuntu uses now and it is radically different from the gnome DE in 7.04. You might want to try Xubuntu or Lubuntu which are both much more like what you are used to. Or take the plunge and try the latest Ubuntu with Unity DE (you can always change the DE to gnome-fallback or any number of others if you don't like the default Unity DE).

---

### Post by mörgæs on 2014-01-12
Threads merged. Please don't create multiple threads regarding the same problem.

---

### Post by kostkon on 2014-01-12
With that amount of RAM, and the hardware being pretty old overall, puppy linux or some other super lightweight distro would be a more logical choice, I don't think it can run Lubuntu.

---

### Post by QIII on 2014-01-12
Bodhi Linux would do just fine on that, I think.

---

### Post by Bucky Ball on 2014-01-12
> **jnorthr said:**
> ... 256mb 

Oops. My bad. Missed that. Puppy is a good choice I played with Porteus recently and that would also run.

---

### Post by jnorthr on 2014-01-12
Thank you all for the advice. Have noticed that my disk has several partitions one of which is /home ! ( Now i remember why i went thru the agro to partition my drive! ).
  
My old war horse laptop has been maxed out at 256MB ram 800MZ Pentium III - s-l-o-w yes, but absolutely brill keyboard & 15.5" screen which was great in 2001 :)

So me thinks i might as well go for lubuntu 13.10 ( as i hate unity - that's mostly why i stopped using ubuntu and went to an apple). 

Ergo a fresh install plus avoid blitzing the /home partition might just save me the setup grief, well that's the plan really ;)

more news soon
thx
jim

---

### Post by Elfy on 2014-01-12
> Ergo a fresh install plus avoid blitzing the /home partition might just save me the setup grief, well that's the plan reallyGiven the changes between versions from 2007 and now - I'd be wary.

Perhaps if you have diskspace go for an install WITHOUT a seperate /home and keep the partition of 7.04's /home there - then just move things across as you find a need for them.

Just a thought

---

