---
title: "Ubuntu 6.06 'Select and Install Software' Failing"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by PQLResearch.Com on 2006-07-17
Hi there. I'm attempting to install Ubuntu 6.06 and I'm having some problems. I am by no means a linux expert, but I did manage to install SuSE 10.1 on the same box I'm installing Ubuntu, so I am not completely a novice (but I may be missing something easy/obvious so please help if you can!).

Test system I'm installing this on:

Athlon 1200 on MSI Board, With 384MB PC133 ram.
30GB Western Digital Drive.
Low-End GeForce4 Graphics
Anything else you need?


Here's what I've run into.

- The "LiveCD" download would essentially boot into a magenta/red colored background with a cursor and stall there. The machine wasn't locked, it would just stall. No options, nothing to click. No hard drive activity. 

- I took the advice of many here and downloaded the 'alternate' CD. I used Md5 summer to make sure the checksum was good, and burned it at 24X. I used the 'Verify CD' test and Ubuntu reported it was good.

- I proceeded to install in Text Mode.

- It gets about 20 minutes in .. past the time zone.. the clock.. and a bunch of files being retrieved from the CD. I then get a red screen with the header 'Configuring libpango1.0-common'. The screen says the setup component of 'Select and Install Software' failed. If I hit okay, it will try again and
essentially loop and reproduce the problem.

Can anyone offer a solution?

Thanks!

Tim
[www.pqlresearch.com](www.pqlresearch.com)

---

### Post by az on 2006-07-17
Maybe your optical drive is failling?

I have had the same problem on older systems.  Your's is not too old, but maybe it is in a dusty or smokey environment.

Maybe try to change the DMA mode in the bios (to use a slower mode).  That still may not help.  Can you use another optical drive?

---

### Post by PQLResearch.Com on 2006-07-17
Thanks for responding.

I have another I can use and I'll swap it shortly. The one I'm using is a 36X .. pretty old considering CD speeds have been topped at 48-52x for years now. =)

I'm trying the 'OEM Mode' install just for kicks. I'll report back if that seems to be successful. If it fails, I'll swap the drive and pull a 52X cdrom from another linux system.

I really appreciate your time and help.

Tim
[www.pqlresearch.com](www.pqlresearch.com)

---

