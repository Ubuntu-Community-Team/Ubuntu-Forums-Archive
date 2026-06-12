---
title: "What are pros/cons upgrading from 14.04.2 to 15.04?"
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2015-04-26
No one seems to mention upgrading from 14.04.2 to 15.04.  Is this an allowed upgrade?  What are advantages and disadvantages?

John

---

### Post by ajgreeny on 2015-04-26
You can not do that in one jump using the standard online upgrade system; you can only move by one version at a time so you would need to first upgrade to 14.10 then to 15.04, so it is not worth the effort in my opinion.

What you could try is the dirty version of a clean installation which is the same as a normal installation but you choose not to format any of the partitions but simply overwrite them.  In order to do this you need to choose "Something Else" at the partitioning stage then make sure that the format tick-box is deselected for all the partitions.

I have never tried it but always made a clean installation; I have a separate /home partition so it is quick and easy for me.

---

### Post by impliedconsent2 on 2015-04-26
PROs:  latest supported DE and kernel. Cool new looks. Kinda cool to install new distribution from scratch (see con)
CONs:  bricking your solid 14.10 install (which I did)

---

### Post by grahammechanical on 2015-04-26
Ubuntu 15.04 only has 9 months support. So, if we move from 14.04.2 to 15.04 (whichever way we do it) we will have to upgrade to 15.10 and then 16.04 before we get back on to a 5 years Long Term Support (LTS) release. It is not a problem for me.

---

### Post by cigtoxdoc on 2015-04-26
Thank you for your help.  Upgrade from ISO went very smoothly as one option was from 14.04 to 15.04.  No data appeared to have been lost as when I reinstalled evolution, my mail was still there.  Moreover, e-mail that had caused evolution (3.10.4) to9 crash, now were displayed correctly with evolution 3.12.11 that came with 15.04.  This upgrade was done on my test pc (hp-compaq dc5800).

Will it work as well with my production PCs (DELL Vostro 3500 with nVidia graphics, and two desktops based on Intel i7-4770K processors)?

John

---

### Post by fr33z0n3r on 2015-04-27
I feel like I may have made a bad choice when I wiped my 14.04.02 install and went with 14.10.  I have had more bugs then in 14.04.02 by far. I had gedit crash with minimal usage!  That has me quite concerned over going to 15.04.

So my con would be abandoning the stability (and attention of) an LTS version.  I feel like the effort placed in newer versions, especially of late, is lacking compared to LTS.  I will probably have to go to 15.04 but I plan to hold out for a bit longer until enough feedback has flushed out any major issues.  The switch to systemd has me worried.

@cigtoxdoc - I'm just a noob, but I think that your direct upgrade method sounds like a bad idea.  Good luck!

---

### Post by craig10x on 2015-04-28
I have done upgrades both by using the iso and the upgrade using the software updater and came to the conclusion that using the software updater upgrade method generally works the best...

When i did it with the iso, because you are not actually on the hard drive, often certain items won't make it over and there can be other problems...when you upgrade using the software updater method, in my case, i have always had 100% perfect results...and i think a lot has to do with the fact that it is being done "in place" in other words, right on the drive...so things tends not to get lost or messed up....
Although i do always uncheck my ppas in the software sources first before upgrading (and re-checking after upgrade is finished and you re-boot to the new version...

And i have done upgrades on upgrades, again with superb success...i upgraded from 14.04.2 to 14.10 and now that 15.04 is out, i upgraded again to that...
As was mentioned, you can't go directly from 14.04 to 15.04 with the "in place" upgrade but you can do it in 2 steps...that would have been the better way to go...
Although i would have done that over two days time (if i was in your position)...just to sort of give the system a little extra time to stabilize, get the latest updates, before going on to the next upgrade... ;)

---

### Post by ubfan1 on 2015-04-28
@cigtoxdoc - Be careful on the desktops if they have multiple disks -- see bug 1265192.  The Ubuntu 14.04.2 with the updated kernel (Hardware Enablement Stack (HES))  really needs new HESes added as the old one expires, unlike the original 14.04 which just keeps the original kernel and keeps updating, so once you are on the .2, .3,... 14.04 series, you have the 9 month update requirements too.

---

### Post by mattharris4 on 2015-04-28
> **fr33z0n3r said:**
> I feel like I may have made a bad choice when I wiped my 14.04.02 install and went with 14.10.  I have had more bugs then in 14.04.02 by far. I had gedit crash with minimal usage!  That has me quite concerned over going to 15.04.

So my con would be abandoning the stability (and attention of) an LTS version.  I feel like the effort placed in newer versions, especially of late, is lacking compared to LTS.  I will probably have to go to 15.04 but I plan to hold out for a bit longer until enough feedback has flushed out any major issues.  The switch to systemd has me worried.

@cigtoxdoc - I'm just a noob, but I think that your direct upgrade method sounds like a bad idea.  Good luck!

I wish more people would warn others thinking of upgrading to a non-LTS version that those versions are mainly for development and testing, not for the average user to "upgrade" to.  Granted that is my opinion but LTS is around for a reason and that is to provide the normal user devoid of any programming skill to be able to install and use Ubuntu et. al. easily and reliably (at least in most cases, the HP "only will run Windows 8.1" bug still will require reprogramming, sorry).  If someone buys a bleeding-edge new computer with all of the new toys maybe that person needs a non-LTS version, especially if buying this late in the development cycle.  Otherwise unless you know what you are doing and intend the install mainly to test and report problems in order to assist in the development of Ubuntu et. al. 16.04 do not install any version but the current LTS which is 14.04.  You can have those new and great features when 16.04 comes out and they will actually work correctly and save you a boatload of grief!

---

### Post by Cliff Bentley on 2015-07-20
Thanks for the advice mattharris4. I had been debating, now I'm glad I looked at this thread. I intend to install a MEAN Stack (MongoDB, Express, Angular, Node.js) to develop a few thing for myself and to stretch my skills. Knowing that a lot of new versions would be coming down from npm, I was afraid of using Ubuntu 14.04. But you spoke sense. I'll worry about a complete upgrade next Spring using the next LTS.

---

