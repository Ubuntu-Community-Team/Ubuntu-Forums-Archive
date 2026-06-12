---
title: "safe to upgrade?"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2010-01-17
I have tried to read some of the thing under the sticky thread about ubuntu not working after update to 9.10, mainly connected with nvidia etc.

This all seems rather complex for someone with only small experience.

The Q is : is it safe today (bugs fixed?) to update from 9.04 to 9.10 simply via the update manager? Or will I have definitely no running system then and will need lot of special work to be done on drivers etc?

My system is a dell dimension 4550, nvidia GeForce4 Ti4200.

Or is the upgrade to 9.10 to dangerous still?

---

### Post by John Bean on 2010-01-17
I would strongly recommend you use a liveCD of Karmic to establish that it works as expected on your PC before contemplating an "upgrade" to your existing system.

And even if it does work I'd still recommend a new installation every time... but that's just me.

---

### Post by ottosykora on 2010-01-31
OK, today, I downloaded the current iso of the 9.10 ubuntu.
Produced a CD and booted from it.
Nothing, it just comes up with white ubuntu logo and after abt 10 minutes flashing cursor on the screen, thats all.

Strange, I hoped that after so long time after release, all the bugs might have been cleared, but it looks like the 9.10 version simply wont work on my dell dimension 4550.

Or is there any version where all those problems are corrected? 
(lucky I did not click update to next distro in the update manager)

---

### Post by dzon65 on 2010-01-31
Did you burn it as image?Did you burn it at low speed?

---

### Post by dzon65 on 2010-01-31
"Or is there any version where all those problems are corrected? 
(lucky I did not click update to next distro in the update manager)".
You can always get a cd from ubuntu shipit.
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by ottosykora on 2010-01-31
I burned it as usual, did compare after, the CD seems to be ok. Did second copy on other computer, same. 

It seems to be not the problem of the CD or so, but rather the version 9.10 still has all the bugs with display drivers etc in it as so many people run into.

I downloaded it just from the main download. Therefore was the Q if the is possibly some meanwhile corrected version avaiable from some ftp place or so.

The current 9.10 definitely ends up in showing the white ubuntu logo and later only flashing underscore prompt.

Have tried to set all acpi off and noapic etc, safe graphics, still no go.

---

### Post by dzon65 on 2010-01-31
Could be due to kernel.Sometimes bios has to be updated.
Might wanna read some threads like this one:[http://ubuntuforums.org/showthread.php?p=8743175](http://ubuntuforums.org/showthread.php?p=8743175)

---

### Post by ottosykora on 2010-01-31
@dzon65

hmmm, yes, but this computer has the most recent bios avaiable for it, nothing more can be done in this direction.

I have tried to read many of the suggestions in the sticky thread with the kernel and nvidia, it looks I am one of those many victims of this problem, simply 9.10 seems to run only on some very recent and very advanced hardware. And yes, there is nvidia in my computer, this seems to make it even worse.

I only had the impression, that after those bugs are known for so long time, that there will be some corrected iso files for download somewhere available to solve this graphic problem. 
It seems that this is so far the end of ubuntu updates so far, even my office computers are some which came with XP originaly and have nvidia graphics in it, this seems the end of using ubuntu probably. :-(

---

### Post by dzon65 on 2010-01-31
I've been doing ubuntu (minimal)installs on pentium 3 without a glitch.The last one was an old compq presario with hardly 300mb (this was even upgraded ram,since I started with 128mb ram).
Hey,that you might just try that.Why not?Try a minimal install,you can add whatever window,file or whatever manager.The advantage with it is that you can keep it as light as you want.I'll give you some links in a sec.

---

### Post by dzon65 on 2010-01-31
Posted some links here:[http://ubuntuforums.org/showthread.php?p=8752268#post8752268](http://ubuntuforums.org/showthread.php?p=8752268#post8752268)
Let me know if the minimal DOES boot.Cause if you want a minimal gnome environment I'll tell you how to do it.PS:That psychocat-link installs a leightweight.But if you want a minimal ubuntu,there's some things to be changed.

---

### Post by gradinaruvasile on 2010-01-31
If you have an expendable partition you might try to install it with the text mode installer (alternate cd). I had startup problems on nvidia a8200 igp because of the nv driver.

PS. Well nvidia is the best supported graphics chipset around... By their proprietary drivers - the opensource one still has problems with some models.

---

### Post by ottosykora on 2010-01-31
I was in fact not heading for new installation or so.
There is 9.04 running on that machine, various software installed, configured etc.

However I wanted update to 9.10.

The advise was to first try with the life CD, but this is the first which does not work any more. CD with 9.04 work fine, from there I did install the previous versions after all.

Now inserting 9.10 and booting provides this famous flashing white ubuntu logo for abt 10 minutes and then nothing. There is no way to install something, since I have not even a cmd prompt.
Probably could install with the alternate and then while trying to restart ubuntu I will get same experience as so many other, it simply will also show flashing ubuntu logo and nothing else, black screen after.

The point is to keep running system uptodate and if updates are such that they will simply destroy the system, then this is somehow disappointing and makes one reluctant to use ubuntu any more.

In fact I thought I will wait few week or moths , they will solve the problems of the initial release, but bad luck, it still has all the graphic problems as on the beginning. So the current installations can not be maintained any more. :-(

---

### Post by gradinaruvasile on 2010-01-31
And why exactly you need to upgrade? I can tell you there is nothing groundbreaking in 9.10. 
Personally i "upgraded" Ubuntu 9.04 (Gnome) to Xubuntu 9.10 on all 3 of my computers. Works like a charm, fast and stable, no default PulseAudio.
Maybe try the Xubuntu livecd - it just might work...

Also, if you have a USB stick, you can use that for booting, no need to burn cds.

---

### Post by ottosykora on 2010-01-31
usb sticks, well non of my PC at home or at work is able to boot from usb media, so this is why I still keep going with CD.

The problem with the older distros is, that also all possible apps are in rather old versions in the depository and an update of single apps is beyond my knowledge, since it will often need recompiling it from source etc. I can see already now , that many things are simply not updated in the 9.04 version and the only laptop I have with 9.10 all seems to be updated to the current status.

With xubuntu I have not best experience. I have it on an older laptop which did never accept any ubuntu installations. But the GUI part of it is somehow unstable, I have often mixed up characters in the apps like browser, the start menu can be edited only by writing some xml files, nothing very done for everyday use as a win alternative.

I have 2 Dell dimension 4550 with ubuntu 9.04 and one with kubuntu 8.10 and some compaq with 9.04 and some laptops. So far only one older toshiba laptop managed to have 9.10 on it, it simply will not even start any kind of installation or even command line on any other of my computers.

---

### Post by Alexandre Putt on 2010-01-31
I think it may be a better idea to wait till the official release of 10.04 in April/May. I updated from 9.04 to 9.10 flawlessly, but I have a number of side issues like e.g. noticeably slower booting time. Overall, I'd prefer to have stayed a little longer with 9.04.

---

### Post by theozzlives on 2010-01-31
I had problems with a white screen off the CD, but did an upgrade several months later and it worked. If they updated the .iso, it would be 9.10.1.

---

### Post by ottosykora on 2010-02-03
>If they updated the .iso, it would be 9.10.1.<

hmmm, yes makes sense.

But there is no -1 version released I think?

So will wait until the 10, will sure try with life system first then.

It is just problematic, since for the 9.04 software is mostly also old and not updated any more, for the 9.10 one gets the recent versions. This is the major issue why I was up to an update.

---

