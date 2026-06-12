---
title: "upgraded from 10.04 to 12.10 and is very slow"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by Nathan883 on 2012-11-27
Hi everyone,
This may have been asked before and it it has I would be happy to read any thread someone can direct me to. 

I have an older Pentium 4 dual core 3.3Ghz with 1 gig Ram.  I was running Ubuntu 10.04 and the machine was very fast.  I loved it.  I then upgraded to 12.04, now 12.10 and the machine runs very slow.  I don't know much about linux but i did run a top command and things looked pretty good.  Swap was low, memory was 890K out of the one gig but I think this is normal as once you load something it stays in memory until something new is loaded??

Processor load was down about 6%, so by all accords the machine seems to have plenty of resource and should run fast but if I click on safari, I wait a full 8 seconds for the window to open and this is when I log in using 2D.  If I use 3D it takes up to 20 seconds.  

It seems everything I try to do lags at least 6 to 10 seconds more before it opens/closes/moves.  

2 questions, 
1- do you think a fresh install would help?
2- what is the harm in moving back to 10.04?  My concern is I won't have any support becuase it is not LTS anymore?  Is this an issue?

Any guidance you can provide is GREATLY appreciated.

---

### Post by snowpine on 2012-11-27
Welcome to the forums!

0. Ubuntu provides a "Live DVD" so you can evaluate a new release *before* you upgrade/install, to see how it will run on your hardware. Each release has higher system requirements than the previous releases, and your pentium 4 is rapidly aging.
1. Doubt it.
2. 10.04 is fully supported through April 2013.
3. You might try the lightweight Xfce desktop as described here: [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by snowpine on 2012-11-27
4. Safari is **not provided or supported** by Ubuntu developers; maybe try a supported browser (like Firefox) to see if you have the same problem.
5. What is your graphics card and have you installed the correct drivers?

---

### Post by Nathan883 on 2012-11-27
Sorry, I use firefox, not sure why I typed safari, I don't even own a mac.  Anyway, I am going to try snowpine's suggestion of a different desktop and if that does not work, revert back to 10.04.

---

### Post by mörgæs on 2012-11-27
My experience with upgrades is not good, and I guess that a reinstall would be worth trying. Best of all is a reinstall of (for example) Xubuntu, giving you the Xcfe desktop as Snowpine suggested.

---

### Post by Nathan883 on 2012-11-27
Hi Morgaes,
I did not pick my buntu, I read 10.04 was the most supported and most stable one somewhere so I went with that and it actually worked out really well so I stuck with it. Several months ago the upgrade manager started saying 12.04 was available so I clicked it and the upgrade went through.  

I guess my issue with the other buntus like xfce is a lack of education.  Do the lighter weight desktops limit you in what you can run?  Is all the software available in the software center for 10.04 also available for xubuntu?  My assumption was that if it was considered lightweight it would not handle firefox, flash, Gimp, Fstop etc. 

Thanks
Nate

---

### Post by ZippyUbu on 2012-11-27
Hi,

So you can keep an eye on support for the release that you are using, check out the Ubuntu wiki, Oodles of info here:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

--Zu

---

### Post by ajgreeny on 2012-11-27
> **Nathan883 said:**
> Hi Morgaes,
I did not pick my buntu, I read 10.04 was the most supported and most stable one somewhere so I went with that and it actually worked out really well so I stuck with it. Several months ago the upgrade manager started saying 12.04 was available so I clicked it and the upgrade went through.  

I guess my issue with the other buntus like xfce is a lack of education.  Do the lighter weight desktops limit you in what you can run?  Is all the software available in the software center for 10.04 also available for xubuntu?  My assumption was that if it was considered lightweight it would not handle firefox, flash, Gimp, Fstop etc. 

Thanks
Nate
No, you can use any and all of the applications available in the repos with any of the DEs that are possible.  You can even run the heavyweight apps like firefox etc, with no DE at all, just a window manager like openbox, if you want to.

There are many users who have very powerful machines but still use a low resource DE or WM so as not to waste hardware resources on the part of the OS that does not really do any work, ie the DE/WM.

---

### Post by ugm6hr on 2012-11-27
In the long term, it may be worthwhile sticking to LTS versions, which are now supported 5 years from release.

The last was 12.04, and the next anticipated is 14.04.

Though if you've already upgraded to 12.10, might be worth sticking with that (+XFCE) until 14.04.

---

### Post by Nathan883 on 2012-11-28
Hi Everyone, thank you for all your input.  I installed Gnome manager lastnight and first reverted to Gnome classic then Gnome advanced.  The Gnome advanced seemed to improve performance by at least 60% if not more.  I am going to stick with this for a while. 

Thanks again.

---

### Post by crbmky on 2012-11-28
I've been having the same problems with fresh installs of Ubuntu 12.04 and 12.10.  Both ran painfully slow (in terms of the desktop environment)  immediately after a standard install on a old Intel P4 2,66 GHz w. 512 RAM.  I figured everything should have run smooth based on [Meeting Minimum Hardware Requirements]("https://help.ubuntu.com/12.04/installation-guide/i386/minimum-hardware-reqts.html"), but smooth was not the case.

Assuming the slow performance is normal for my system, maybe the ***recommended*** hardware requirements for desktop installs should be updated?  I would think these recommendations are based on what users can expect with a base install of the O/S. 

I ended up installing Ubuntu 10.04 in the end and this seems to run just fine (also had no issues with the latest Debian 6.0 desktop on another partition).
[B]
[/B]

---

