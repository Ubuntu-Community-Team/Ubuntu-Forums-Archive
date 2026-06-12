---
title: "Sad noob install problem - both 8.04 and 8.10 fail on 740G MB"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by mattthemuppet on 2008-11-04
Hi everyone and thanks in advance for the help!

I've been wanting to try Linux for some time and all the articles I read indicated that it was relatively straight forward (:)), so I thought I'd try it on a new build:

Gigabyte GA-MA74G-S2H mobo (740G chip/ SB700 southbridge)
AMD X2 5000
WD6400AACS
Pioneer DVR-216 (SATA)

HDD is currently partitioned 100GB(WinXP SP3)/400GB(NTFS, data)/100GB(unformatted, intended for Linux)

I've downloaded both 8.04 and 8.10 32bit images, burnt both twice to CD using Nero (2nd attempts for both at x4 speed, following some tips on here). My old DVD drive seems to be kaput so I can't test that as an alternative. Both CDs were checked by the Ubuntu CD check on the Ubuntu boot/ install menu and came up fine.

I've tried both as Install from the Ubuntu boot/ install menu and from within Windows using Wubi. From the boot/ install menu I get the Cylon style orange bar, then a corrupted image, followed by "Cannot detect graphics card and display, in low graphics mode". If I try and select my display and resolution, the monitor (Dell 19in LCD) is picked up fine, but my max resolution is 800x600. If I click continue, I get:

*starting deferred execution scheduler atd [ok]
*starting periodic command scheduler crond [ok]
*checking battery state...                 [ok]
*running local boot scripts (/etc/rc.local)[ok]
_

and nothing - no disk activity (DVD or HDD), even if I leave it for hours.

If I try using Wubi, I get the chose partition/ username/ password screen fine, it unpacks stuff, then prepares disk image. As soon as it's got up to the full 700MB or so, an error pops up saying (off the top of my head):

"Cannot access CD drive. Another program may be accessing it. Stop all other programs and try again"

This is with everything (firewall, windows explorer etc) shut down.

Exactly the same with both 8.04 and 8.10, which makes me think its a hardware issue. The corrupted screen after doing an install from the boot menu plus some posts on here about problems with ATI graphics and/ or SB700 southbridges makes me think it might be something with the motherboard (though I know of another person on SPCR that's installed the server version of 8.04 on a system with this board). But, the Wubi install within Windows makes me think it might be the SATA DVD drive. Either way, I have no idea about how to fix it. Help, please?!

I really want to give Ubuntu a go, I'm so tired of fighting with Windows and all of its vices, but I'm properly stuck (other than trying another distro :()

thanks!
matt

oh, forgot to say - if there are any command line solutions, can you be explicit (to the point of patronising if need be) about how I do it, as I haven't a clue!

---

### Post by spawn. on 2008-11-04
It may be a bad copy or you may need to update your driver.

My experiences:

I had a similar pop-up error message when installing Ubuntu 8.04 awhile ago. I kept trying to install until the darn thing worked. I should mention, it required 4 attempts to re-burn another copy of Ubuntu 8.04 to get one that would run (e.g. 1 CD did not load at all, 2 would be 99% installed before BAM! "error pop-up," and 1 would actually work). A week afterwards, I decided to request a LiveCD from Ubuntu that arrived last week. By the time the LiveCD arrived, I solved all my problems and configured the entire OS to be productive. The LiveCD is definitely worth ordering for those times when you have issues. Go on and request a CD of 8.04 ... in the meantime... ***keep trying

Most images that I burn are hit and miss. I think my Mandriva 2009 LiveCD that I burnt worked, as well as the Gentoo one. However, the SUSE 11 and the Ubuntu 8.10 copy did not. I re-burnt those images until it worked, some three attempts at various speeds. 

As far as the error message about your graphics card, I received that error when trying to install compiz on my other laptop (for 8.04). It is running a Nvidia 64MB card. I could not use advanced graphics or anything. My resolution was okay though. After installing a different driver for the card, I was able to add some features. I have not tested it on the 8.10 version yet.

---

### Post by mattthemuppet on 2008-11-04
> **spawn. said:**
> It may be a bad copy or you may need to update your driver.

do you mean update the Windows chipset driver? I only used the one on the MB CD, so I'm sure there'll be a newer one.

> **spawn. said:**
> My experiences:

I had a similar pop-up error message when installing Ubuntu 8.04 awhile ago. I kept trying to install until the darn thing worked. I should mention, it required 4 attempts to re-burn another copy of Ubuntu 8.04 to get one that would run (e.g. 1 CD did not load at all, 2 would be 99% installed before BAM! "error pop-up," and 1 would actually work). A week afterwards, I decided to request a LiveCD from Ubuntu that arrived last week. By the time the LiveCD arrived, I solved all my problems and configured the entire OS to be productive. The LiveCD is definitely worth ordering for those times when you have issues. Go on and request a CD of 8.04 ... in the meantime... ***keep trying

Most images that I burn are hit and miss. I think my Mandriva 2009 LiveCD that I burnt worked, as well as the Gentoo one. However, the SUSE 11 and the Ubuntu 8.10 copy did not. I re-burnt those images until it worked, some three attempts at various speeds. 

As far as the error message about your graphics card, I received that error when trying to install compiz on my other laptop (for 8.04). It is running a Nvidia 64MB card. I could not use advanced graphics or anything. My resolution was okay though. After installing a different driver for the card, I was able to add some features. I have not tested it on the 8.10 version yet.

Okay, thanks for the tips! I'll try a few more burns and order a LiveCD in the meantime. It's a bit frustrating as I only have ~1 1/2h every night after putting the kids to bed to rest/ do jobs and this has taken up 4 nights so far :(

---

### Post by spawn. on 2008-11-04
I know what you mean about not having time. I have to work 60% of the time, and go to class the other 40% so I can keep going! Every now and then, I can set aside some time to mess around with the OS.

---

### Post by mattthemuppet on 2008-11-06
Spawn - it worked! Burnt 8.10 ISO with my work computer, tested it on that (Wubi install) then went home and it worked perfectly on my home PC. Tried in Windows, which worked fine, then rejigged some of the partitions to create a / and /home partition, then installed on the HDD. Now I just have to figure out why it's not connecting to the internet (I'm guessing an ISP setting), but I'm sure that'll be easy to fix. Really like it already though, feels very snappy!

Thanks again, I owe you a coffee:)

matt

---

### Post by spawn. on 2008-11-07
Thats some good news to hear! I'm glad u got it up and running. Speaking of coffee, I just spent $6 USD at Starbucks for a mocha frappuccino. Delish!

---

