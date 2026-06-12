---
title: "Harddrives shows up as single drives instead of RAID drives on NVidia 590 SLI chipset"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by treierts on 2007-08-29
Hi,

I have tried to install Ubuntu v7.04 on my Dell system (XPS700) based on the NVidia 590 SLI chipset. I have two raid sets, both RAID0 with two drives in each set.

When I boot the Ubuntu Install DVD, I get to the part where I can partition my drive(s). The problem is that Ubuntu display my drives as 4 single drives and not my two raid volumes.

How can I work around this problem? Is there a startup parameter or setting I can change?

Any help in getting past this problem would be very much appreciated.

Best Regards,

Tom Reiertsen

---

### Post by PilotJLR on 2007-08-29
Afraid not. Your computer, like most non-servers, uses software RAID... the RAID functionality was derived from a Windows driver.

You can still use RAID, but it would be linux software RAID instead. Google "fake RAID" for lots of information on what I'm talking about.

---

### Post by treierts on 2007-08-29
Ok, thanks for the info. Seems like I won't be able to install Linux this time either without a bunch of hassle (which equals no install at all). Too bad, I was looking forward to trying Ubuntu. 

Ah well :)

Best Regards,

Tom Reiertsen

---

### Post by confused57 on 2007-08-29
> **treierts said:**
> Ok, thanks for the info. Seems like I won't be able to install Linux this time either without a bunch of hassle (which equals no install at all). Too bad, I was looking forward to trying Ubuntu. 

Ah well :)

Best Regards,

Tom Reiertsen

If you still want to try, here's the Ubuntu Documentation guide:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by highlanderc on 2007-09-09
I registered just to rant on this topic...

You know why windows is so good and popular??? because it has solutions and answers...

I have been looking and I am having the same problem.. pointing someone to read the manual is, in all honesty... not good at all... 

Its safe to say then that... Windows is so much better than linux because I don't usually run into this kind of problems... 

If you can help out.. Do so.. I am in the same boat...

---

### Post by Evanlec on 2007-09-09
> **confused57 said:**
> If you still want to try, here's the Ubuntu Documentation guide:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I was in the same boat, and this guide seemed to be the only solution, but unfortunately i had so much difficulty trying to get it to work that i eventually gave up and just went back to no RAID.

you win some you lose some i guess.

---

### Post by confused57 on 2007-09-09
Here are some Ubuntu/Linux Raid links provided by Herman:
[http://ubuntuforums.org/showpost.php?p=3327821&postcount=32](http://ubuntuforums.org/showpost.php?p=3327821&postcount=32)

If someone(me) doesn't have any experience with Ubuntu & Raid, the next best thing is providing a link.
Raid does work well with Windows, maybe because every hardware & software manufacturer provides support...makes sense, since that's where the $$ are.

---

### Post by PilotJLR on 2007-09-09
Software raid works just as well in Linux... it's a power user tool, and can require that level of knowledge to make it work well.

I strongly disagree that posting links to howtos is not helpful; these wiki howto's are the result of collaboration from many skilled people, all of whom are writing these pages on their own time. NOT using them is a waste of everyone's time and effort.

---

