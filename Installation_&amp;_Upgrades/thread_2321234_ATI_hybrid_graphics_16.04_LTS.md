---
title: "ATI hybrid graphics 16.04 LTS"
date: 2016-04-21
forum: Installation &amp; Upgrades
---

### Post by redguy41 on 2016-04-21
Hi, 
has anyone done a clean install of 16.04 LTS using hybrid graphics? Or at least ATI graphics card?

I'm using ATI/Intel, and listening to advice whether to install 16.04 or not, I was wondering if someone has taken that step, and if there are any problems with the AMDGPU open source driver in basic tasks (tear, lag, and so on)?

Planning to do a clean install on Ubuntu 16.04 LTS.

04:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M / R9 M275X/M375X] (rev ff)

---

### Post by grahammechanical on 2016-04-21
AMD will not be providing any proprietary video drivers for Ubuntu 16.04 because 16.04 uses a new version of the X server and the AMD proprietary video drivers do not work well with it.

So, if your work flow depends on using an AMD proprietary video driver do not upgrade to 16.04. The proprietary video driver will be removed during the upgrade and radeon or amdgpu will be used instead. It is all in the 16.04 release notes.

As for your specific situation, the answer would be to try a live session.

See know issues

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Regards

---

### Post by QIII on 2016-04-21
... and:  AMD has been working very had with the open source community (well, Canonical specifically -- which means that Ubuntu will have all the benefits before anyone else) to do what we have been asking for for years -- create a truly good open source driver.

AMD doesn't want to spend the time updating fglrx for the new X Server and Canonical doesn't want to wait to use it until the work with AMD is done, so we will have a rough Summer.  But we are told by both AMD and Canonical that by the end of Summer the wait will have been worth it.

If you absolutely must use the fglrx driver, don't upgrade until we see what happens by August or so.  But I have read that 16.04, at least, will not get any newer fglrx that may be available later.  In other words, 16.04 just won't ever have fglrx, even if the fglrx driver is available later.

If you want to use the current open source Radeon driver, it IS available.  In fact, if you don't have a Volcanic Islands chipset, you will default to the Radeon driver when you install 16.04.  This is what happened with a fresh install with an R9 290X, which has a member of the Sea Islands chipsets.

I will be doing some detailed and thorough testing of 16.04 on an R9 380X (which has a Volcanic Islands chipset) with AMDGPU and the experimental AMDGPU Pro this weekend and next.  I'll try to have some info on my blog by next weekend.

As for hybrid graphics, I can't say at all what will happen with that.

---

### Post by Bashing-om on 2016-04-21
redguy41; Hello;

May I add:
> 
As for hybrid graphics, I can't say at all what will happen with that.

See the release notes, known issues with hybrid graphics are noted and a work-a-round for install.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by sgian on 2016-04-21
I tried out the beta version of 16.04 on two different computers with AMD graphics, HD 8370D and a R5450.  They were adequate for common tasks like web browsing.  It was just gaming (specifically minecraft) that it was noticeably slower for the R5450 and completely inadequate for the HD 8370D.  So if you are just browsing the internet and checking email, 16.04 should be fine.

---

### Post by Bashing-om on 2016-04-24
Addendum :
Maybe with the release of 16.04.1 the FGLRX driver will be available ???
[http://news.softpedia.com/news/canonical-recommends-open-source-amdgpu-and-radeon-drivers-for-ubuntu-16-04-lts-501556.shtml](http://news.softpedia.com/news/canonical-recommends-open-source-amdgpu-and-radeon-drivers-for-ubuntu-16-04-lts-501556.shtml)

The last parafraph :
> 
Update: We've been informed by Oliver Grawert from Canonical that the proprietary AMD Catalyst (fglrx) driver has been temporarily removed the Ubuntu 16.04 LTS repositories, as it is not yet ported to X.Org Server 1.8. It will be added again as part of the first point release, Ubuntu 16.04.1 LTS.


Whether having effort put into a proprietary driver will be fruitful, time will tell .

 [INDENT][INDENT]me, I vote open source
[/INDENT][/INDENT]

---

