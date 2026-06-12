---
title: "Confirm or Deny: Conflict with Highpoint Rocket 133 &amp; Feisty?"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by HoldSteady on 2007-08-04
When I finally decided to switch from Windows to Ubuntu, I first tried to install Feisty.  I tried three times, actually - confirming the MD5 checksums of the 4X burned discs.  Each time the install would fail with busybox / job control errors.

I then tried to install Edgy instead - and it worked.  I used it for about a week (installing various programs, running the Updates as needed), then I tried the Upgrade to Feisty from within Software Updates.  Rebooting resulted in the same failure as my initial Feisty install attempts, forcing a reinstall of Edgy again.

I now wonder if the Feisty install cannot handle my Highpoint RocketRAID 133 PATA controller card.  I don't have a RAID (my two hard drives are listed as hdg and hdh), I just added the card to allow my newer drives to work at ATA 133 instead of the slower motherboard controller on my older system.

I do have to admit, I went to the dark side and installed Automatix (for the multimedia codecs), so that may have been a factor in the upgrade failure, but I'm not convinced, given the inability to clean install Feisty in the first place.  I have since uninstalled Automatix and gone back to the original sources.list.

So my original question: is Feisty incompatible with my Highpoint RocketRAID 133 PATA controller card?  And more importantly: will Gutsy be compatible with this card, or should I just be content with Edgy?

I did read the suggested similar threads such as [http://ubuntuforums.org/showthread.php?t=45426]("http://ubuntuforums.org/showthread.php?t=45426"), but again, I don't have a RAID setup (even in the windows 2000 partition on my dual boot Grub setup).

In case it matters:
 uname -a
Linux Nostromo 2.6.17-12-generic #2 SMP Mon Jul 16 19:37:58 UTC 2007 i686 GNU/Linux

---

### Post by tgm4883 on 2007-08-04
I can confirm that Feisty does work with Highpoint Rocket 133.  It is currently installed in my file server running Feisty (Desktop Edition).  

However, it is not hosting a drive with the OS on it, simply extra storage drives, and it will not allow you to run software RAID on it either.  Your problem may stem from using it as the OS drive, or other Feisty hardware related issues.

---

### Post by orpobanana on 2007-11-16
> **tgm4883 said:**
> However, it is not hosting a drive with the OS on it, simply extra storage drives, and it will not allow you to run software RAID on it either.  Your problem may stem from using it as the OS drive, or other Feisty hardware related issues.

Do you mean, that you can't use hard drives connected with HPR 133 with EVMS? I was planning to buy this card, but if it doesn't support soft-RAID it's good to know about it.

Thanks

---

### Post by HoldSteady on 2007-11-16
I gave up on the card and yanked it out; I was then able to install Feisty.  Since that success, I was considering upgrading to Gutsy, but not after reading the massive upgrade thread where a significant chunk of users had problems.  I think I'll wait for the next LTS in six months - unless I'm not allowed to upgrade direct from Feisty to Heron (again, that really should have been named Hungry Hungry Hippo).

---

### Post by tgm4883 on 2007-11-17
> **HoldSteady said:**
> I gave up on the card and yanked it out; I was then able to install Feisty.  Since that success, I was considering upgrading to Gutsy, but not after reading the massive upgrade thread where a significant chunk of users had problems.  I think I'll wait for the next LTS in six months - unless I'm not allowed to upgrade direct from Feisty to Heron (again, that really should have been named Hungry Hungry Hippo).

The card doesn't support software RAID and I couldn't find a way to do it (kept giving me various errors)

About the LTS, unless they change something, it has always been that you have to upgrade from the previous version.  So you will not be able to upgrade from anything except Gutsy

---

