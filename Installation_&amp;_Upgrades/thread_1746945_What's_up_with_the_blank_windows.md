---
title: "What's up with the blank windows?"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by bkline on 2011-05-02
Just upgraded to 11.04 and now I frequently get windows with nothing in them.  Happens randomly when I launch a new app, or switch between apps, or maximize the window for an app.  Is this a known bug?

---

### Post by haydemon on 2011-05-02
I have the same problem. :confused: The only way I've been able to get around this problem is to activate a new window, then minimize it; the original content shows up in the original window after that. It's quite ANNOYING!!! But, first I changed the boot options to the Classic look, versus the new one, because I was having a heck of a time navigating between open windows, which didn't give me the option of trying the so-called solution above. I hope somebody addresses this issue QUICK!

---

### Post by bkline on 2011-05-02
Don't know yet if this is a real solution, but after switching to "Classic - no effects" I haven't experienced the problem.  I guess the maintainers thought that randomly blanked windows would be an attractive "effect"!

---

### Post by XenomeX on 2011-05-02
Hey my problem's even worse.  The other day I upgraded from 10.10 only to find !all! windows open blank except for the System Monitor and maybe one other that doesn't really ad any functionality.  They all have the very top bar with the close, re-size, minimize buttons.  Re-size and even that disappears.

I changed to the Classic look, same thing.  I'm not real impressed with the new layout anyway.  Sorry, a little off subject but I don't see it as easier, more intuitive or less cluttering. 

I sure hope there's a fix for this and soon, I'm back to using XP.  Anybody?

I've been running Ubuntu since at least Intrepid Ibex.  Have never had any real problems with upgrades and updates until now.  Always did them as soon as available.  Maybe I was just lucky.  Maybe I should go back to my old Windows strategy of always staying a full upgrade behind the curve.

Anyway, if anyone has any suggestions, I'm open.

Thanks.

---

### Post by bkline on 2011-05-02
> **XenomeX said:**
> I changed to the Classic look, same thing.

Did you try "classic - no effects"?  That worked for me.

---

### Post by XenomeX on 2011-05-03
> Did you try "classic - no effects"?Thanks! I hadn't yet thought to try that.

At least Ubuntu is functional now.  Still has plenty of problems though.  And I'm guessing I'll find even more related to this issue.

Most problematic: Open applications don't show up on the panel.  If I minimize them I can't get them back.

Most irritating: My Cairo-Clock no longer displays properly.  It's background, window? which is supposed to be clear is now an ugly black square and smoothing doesn't work properly.  The result of effects being turned off?  I know, it's just a clock but I put a lot of effort into getting it just right.

And then attempting to resize certain windows causes large blocks of the desktop to turn black.  Clicking on those areas cause them to revert but in an oddly patchwork way.

I'm guessing all this is related to the graphics driver. My current version is noted as Recommended.  The NVIDIA version 173 is not activated but required to run Unity and perhaps Classic with effects?  

I'm not going to try that driver until I learn more as I've read of problems caused by activating it.  For now I can live with what I got and will not risk making things worse.

So thanks for getting me back up and running.  Much appreciated.

---

### Post by bkline on 2011-05-03
> **XenomeX said:**
> I'm guessing all this is related to the graphics driver.

Seems like a plausible theory.  This affects my laptop but not my workstation.

> **XenomeX said:**
> So thanks for getting me back up and running.  Much appreciated.

Glad to help!

---

### Post by bkline on 2011-05-03
> **bkline said:**
> Is this a known bug?

[Answering my own question:] Looks like it is: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/753144](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/753144)

---

### Post by biodiesel-bri on 2011-05-07
I'm experiencing the same issue in 100% of the time Kubuntu 11.04 with the proprietary Nvidia drivers, so this has nothing to do with Unity. I also experienced this issue in Kubuntu 10.10 but only when I had a lot of windows opened - reducing the number of open windows 'solved' the issue when it happened.

A temporary workaround in Kubuntu is System Settings -> Desktop Effects -> Advanced -> uncheck Enable Direct Rendering.

---

### Post by MAFoElffen on 2011-05-07
> **bkline said:**
> Seems like a plausible theory.  This affects my laptop but not my workstation.

Glad to help!
I'm thinking one of two things:

First as suspect is compiz.  That has been the number one thing that has been comming up with these problems.  Search this forum, as there is many threads that have resolved this here already, but "one" that comes to mind is here in this post and the refrered tutorial:[  http://ubuntuforums.org/showpost.php...10&postcount=2]("http://ubuntuforums.org/showpost.php?p=10779010&postcount=2") 

...and the tutorial it refers to on diagnosing compiz problems, reconfiguring and customising it:[  http://ubuntu4beginners.blogspot.com...-in-unity.html]("http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html")

May be... that you might need to allocate more allocated vmap memory via " vmalloc=192MB " (or whatever amount) in the kernel boot line.  Meaning that the problem may be that the addresable memory allocated is not enough... Meaning that even though your video card has lots of video memory, the kernel is not allocating the space to address it... There is an open bug on this, but the above is the workaround for it.  A good, easy thing to try.  Instructions here in 1st post:  [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Please let me know how it goes and if that information helped.

---

### Post by biodiesel-bri on 2011-05-07
It can't be with Compiz because I've got the same problem and I'm not even using Compiz.

According to the bug report, the problem lies with the Nvidia drivers.  Follow the link to the bug report and in the comments there is a way to submit the bug to Nvidia.  The only way this is going to be fixed is if a bunch of us email Nvidia with proper bug reports including the information they need to fix the issue.

---

### Post by phydeaux98038 on 2011-06-01
> **bkline said:**
> Did you try "classic - no effects"?  That worked for me.

Is there any way I can set up "Classic - no effects" via the CLI, since the Systems Settings window is one that shows as blank 100% of the time?  For that matter, Chrome comes up blank about 75% of the time, Firefox about 60%...  generally speaking, I'm really wishing I hadn't made the change to 11.04.  10.10 seemed to work just fine for me.

---

### Post by bkline on 2011-06-01
> **phydeaux98038 said:**
> Is there any way I can set up "Classic - no effects" via the CLI, since the Systems Settings window is one that shows as blank 100% of the time?  For that matter, Chrome comes up blank about 75% of the time, Firefox about 60%...  generally speaking, I'm really wishing I hadn't made the change to 11.04.  10.10 seemed to work just fine for me.

You get the option to choose when you're on the login screen, after you've selected the username, but before you enter your password.  Look down at the bottom of the screen and you'll find the picklist.

---

### Post by phydeaux98038 on 2011-06-01
> **bkline said:**
> You get the option to choose when you're on the login screen, after you've selected the username, but before you enter your password.  Look down at the bottom of the screen and you'll find the picklist.

Ah ha!  Never looked down there at login time.  Of course it was that easy.

Now, continuing on with the issue with this Broadcom wireless chipset.  Grrrr.

---

### Post by Gstrazds on 2011-06-06
Hi there.. This problem has a workaround until the Nvidia drivers are fixed.. 

There is a bug report on this.. Short answer - change the Video aperture in Bios from 64 meg to 128meg.. problem went away for me.. although if a very large number of windows are open it might come back.. 

rebroadcasting the solution posted elsewhere..

Take care 

Glenn

:)

---

### Post by bkline on 2011-06-06
Thanks, Glenn!

---

### Post by wildmanne39 on 2011-06-07
> **bkline said:**
> Thanks, Glenn!

Hi, if you are running a nvidia card the driver is the problem in unity, I had to change from the current driver to the 173 and everything is great.

---

### Post by brel on 2011-06-24
Downgraded to driver 173 and that worked for me as well. I've got an nvidia geforce 7025.

---

### Post by bkline on 2011-06-24
I tried Glenn's solution (see above) and it worked on my laptop.  Hurrah!  Now if we could just get nVidia to provide the real fix so we don't have to worry about how many windows we have open.

---

### Post by brel on 2011-08-21
If anyone's following this:

I've just tried the 280.13 driver and the problem is still not fixed. I've tested the 275.21 as well. Same thing. Apparently a bug has been opened at NVidia...

---

### Post by brel on 2011-08-21
I've just upped the 'Frame Buffer Size' in my bios from 64M to 256M (advice given further up) and the problem's gone away for the time being.

---

### Post by Smudge249 on 2011-10-17
I know this thread is a couple of months old but I recently upgraded to 11.10 and was experiencing the same problems with blank windows. I changed the video in BIOS from 64mb to 128mb and it seems to have fixed the problem. Funny enough I experienced the blank window problem more in 11.10 than I did in 11.04

---

### Post by bkline on 2011-10-17
> **Smudge249 said:**
> I know this thread is a couple of months old but I recently upgraded to 11.10 and was experiencing the same problems with blank windows. I changed the video in BIOS from 64mb to 128mb and it seems to have fixed the problem. Funny enough I experienced the blank window problem more in 11.10 than I did in 11.04

And to make matters worse, they've stripped the classic interface from this release.  I guess having the problems in the default interface wasn't good enough. :-)

---

