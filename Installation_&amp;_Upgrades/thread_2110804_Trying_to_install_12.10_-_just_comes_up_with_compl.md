---
title: "Trying to install 12.10 - just comes up with completely blank splash screen"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by scrumpypaul on 2013-01-31
Hi Folks,

I have a very old Dell Dimension 1100 (aka B110) PC, originally shipped with XP.

The only modification is increased RAM to 2GB.

Reading the spec sheet, it supposedly has Integrated Intel Extreme Graphics 2.

I recently had an older version of Ubuntu on it, but decided I wanted to put Windows 8 on it.

So I reinstalled Windows XP and then went through the upgrade process for Win8. 

It wouldn't work - resulting in just a blank screen.

Decided to reinstall Ubuntu, downloaded 12.10 and installed with a USB stick.

Installation seems to go fine but the result is just atht it sits on the colourful splash screen with no toolbar, nothing.

I can open up a terminal with Ctrl-Alt-T.

That's about it.

I had, in the course of trying to sort the Win8 upgrade, downloaded a whole bunch of drivers from Dells website and installed them

Is this the cause of my problem?

In which case, could somebody kindly give me a real step-by-step guide to solving this before I throw the whole thing out of a window?

TIA

SP

---

### Post by Mark Phelps on 2013-01-31
I would go for 12.04 at this point.

I've been running Ubuntu for years and 12.10 is the first version the presented serious problems in installing it and getting it working.  It still has crashes every day I use it.

Try booting from a 12.04 CD and seeing how well it works.

---

### Post by scrumpypaul on 2013-01-31
Thanks,

I've reinstalled 12.04 and it works - sort of - but is painfully slow in opening windows and web use, even though I have a strong net connection. Any ideas why?

Should I try reinstalling drivers? If so, how?

SP

---

### Post by Mark Phelps on 2013-01-31
Is this the Dell that uses the Celeron processor? 

Recent Ubuntu versions expect fairly modern hardware to run well; something this old would do better using a lighter weight version such as Lubuntu.

---

### Post by scrumpypaul on 2013-01-31
It's about a thousand years old Mark. But, it was running Ubuntu until just a few days ago, maybe build 11.**? And it did so fine, only now it seems so slow.

May be worth my while trying something less intensive, so thanks for your advice.

---

### Post by Mark Phelps on 2013-02-01
> **scrumpypaul said:**
> It's about a thousand years old Mark. But, it was running Ubuntu until just a few days ago, maybe build 11.**? And it did so fine, only now it seems so slow.

May be worth my while trying something less intensive, so thanks for your advice.

The newer versions use the Unity desktop by default -- which places significantly more graphics load on the PC than did the older versions.  Thus, it's common that an 11.x version ran just fine and 12.x versions do not. Lubuntu doesn't use the Unity desktop, so that is less of a load.

---

### Post by scrumpypaul on 2013-02-01
Thanks for that Mark. Even before your suggestion I decided to have a try putting Lubuntu on. It works a lot better - still not great - but okay. Youtube won't play fullscreen video without it being unusably choppy, but if it isn't fullscreen it copes reasonably well.

So, I've also decided to stick it on an extremely old laptop which was running (well, crawling really) XP. Lubuntu works superbly straight from the gate, even rekindling the long-lost wifi..........

Thanks for your help.


SP

---

### Post by ac5jw on 2013-02-01
Hello, I am a new forum member because of this same problem with 12.10 and blank (but colorful) splash screen.  It boots up OK to a good desktop login screen with menu items at the top.  But, everything disappears after I log in to 12.10 and I get a blank screen and nothing to click on.  I get some action with a right click for folders and document creation, but that is about it.

I saw your reference to Lubuntu and I will look into that.  In the meantime, I ordered some CDs for 12.04 which should arrive in a few days.

I was using Lucid, I think, and always upgraded online with new versions.  I only got this 12.10 DVD because I got click-happy on my Ubuntu and removed too many things at once, freezing my OS.  Because I could not recover it, I used my backup computer to order the 12.10 on DVD to repair the primary Ubuntu.  I had tried to upgrade online to 12.10 using the Update Manager, but it froze up upon reboot.

I am not a terminal CLI user, I am more comfortable with GUI environments.  I have been on Linux and Ubuntu for a couple or three years now.

Thanks for the good ideas and discussion!  As it stands now, I may try the Lubuntu idea.

---

### Post by scrumpypaul on 2013-02-03
ac5jw

Yes, give Lubuntu a try, I'm really happy with it. The laptop that I put it on would absolutely craaawwlll to open pages but this has made it really quite snappy, plus I've configured Chromium just the way I want it. In essence, I will only use that laptop to surf the web and I'm very happy with it now, whereas beforehand it was just gathering dust.

Best of luck.


SP

---

### Post by scrumpypaul on 2013-02-04
Even better still Mark - when I used WinXP on my laptop it said my battery was goosed, meaning I had to use mains power, which effectively consigned it to obscurity.

However, here I am, typing on battery power using Lubuntu - and it says I have over an hour and a half battery left!!!

Absolutely marvellous!!

---

### Post by ac5jw on 2013-03-01
Hello SP and other readers,

I did obtain Lubuntu and I was not satisfied with it.  I don't remember exactly why, but I did install it on top of another Linux OS while evaluating multiple Linux OS's and I quickly realized it was not for me.  I tend to favor a familiar GUI with a desktop and Mozilla FireFox web browser, so Lubuntu may have been too different for my taste or possibly offered Google Chrome web browser instead.  I ordered Ubuntu 12.04 LTS installation CDs from Canonical and my backup PC is humming with it so I am happy.  But, my primary computer for some reason cannot read the Ubuntu 12.04 LTS installation CD at all, and only reads one CD out of about 20 that I have.  It does, however, have more success with DVDs.

ac5jw

---

