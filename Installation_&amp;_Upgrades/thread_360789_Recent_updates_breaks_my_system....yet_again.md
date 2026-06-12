---
title: "Recent updates breaks my system....yet again"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by ghidorah on 2007-02-13
My Ubuntu was nice enough to install some kernel updates for me, without asking, and now I can't log in. GDM just restarts after I try to log in. I get no errors in the logs as to why GDM is restarting. Another day of work lost because of Ubuntu. 

I've tried Ubuntu for about a year now and it's been a profoundly negitive experience. Updates constantly break things. It's the 3rd time in less than 2 months that updates have messed up my system and left me having to boot into Windows to figure out why my Ubuntu is broken, again. Last month one of the updates broke xine and Google Earth, both worked fine before, Ubuntu updated itself and now both xine (and anything that depends on libxine) and Google Earth coredumps with floating point exceptions. Then another round of updates and new problems. This time it was the new ati driver. It was causing my system to freeze after running for about 10min. Once I figured out it was the ati driver, I switch to the fglrx driver included with Ubuntu. This stopped the random lockups I got within minutes of logging in, but now 3D apps would lock the system up randomly. Fine, recompiled the kernel, installed the drivers from ATI manually and got everything working again. Finally (most) everything was working. This lasted about a week. Last night Ubuntu was nice enough to automatically update itself and now I can't even log in. I ran Debian as my primary desktop OS for about 8 years and never had issues like this. Granted, Debian is a little rough around the edges compared to Ubuntu, but Debian worked, which meant I could work. With Ubuntu, it's been so unreliable I have to keep my system dual booted with Windows as a backup so I can get work done, which is just sad at so many levels. I lost half a days time trying to troubleshoot my latest major problem with Ubuntu and finally had to reboot into Windows so I can try and get some work done today. Ubuntu has so much potential but so far it's been one of the the most unstable (and therefore unusable) Linux distros I've worked with in my 10 years as an IT professional. Sorry about the extended rant, but it's just been an extremely frustrating experience. ](*,)

---

### Post by IgnorantGuru on 2007-02-13
I'm fairly new to (K)ubuntu...  I switched from SUSE awhile back.  In general I like Ubuntu a lot more - easier to maintain and just glued together better.  As for updates, most of them have gone smoothly, although I did recently lose the X-server when I updated the kernel, due to a missing dependency.  I do think they need to test the updates a bit better before offering them.

When things do break, usually you can find a fix by checking the forums.

It sounds like a lot of your problems are related to the proprietary video drivers.  I agree there needs to be a little more glue in that area.  But learning how to (re)install them correctly helps.

Also, learn how to backup your partition.  I just wrote a howto on this here...
[http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017](http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017)

There is no need to go through hell when things break - just roll it back and then when you have some time, do the upgrade again and figure it out.

Second, turn off automatic updates.  I have Adept Notifier in the tray so it tells me when there are updates available, but it doesn't update anything until I do so.  I click on it and select what to upgrade.  If it's something like a kernel or video driver update, I save that for when I have some time, and I first make sure my partition backup is up-to-date.

For example, when the recent update took the X-server down, I rolled it back (5 minutes work).  Then I searched around and learned that the linux-restricted-modules-2.6.17-11-386 needed to be manually installed to correct it.  So then I did the upgrade again and did the fix.  No big deal.

---

### Post by ghidorah on 2007-02-13
I can go sifting through forums to find an answer to a problem or just troubleshoot the problems myself. That's not an issue. Having an OS that's doesn't work more often than it does is the issue. I rely on Linux for my job as an IT consultant, it's an essential tool. The issue isn't whether I can solve a prolem I'm having with Ubuntu, I can...I'm a consultant, I do it all the time. The issue is time, something I'm in short supply of, and the amount of work (i.e. money) I lose because Ubuntu decided not to work again. Time I have to spend fixing my own system's problems is time I lose on paid projects. Like I said, I like Ubuntu, it has alot of potential, but I use Linux for my job, I depend on it. Linux isn't a hobby for me anymore, it's a career. And answers like "just turn off automatic updates" (advice I see given out all the time by Ubuntu users) because updates will randomly break your system is unacceptable in business situations, especially at the cost of timely security updates. It's like taking your car to a mechcanic because your brakes don't work and being told "Your brakes don't work? Well then just don't use the brakes."

---

### Post by IgnorantGuru on 2007-02-13
I didn't say don't use updates, I said don't use automatic updates.  Controlling when an update occurs is important if you want stability.

I agree that it would be better to have more stability in the updates - it would be nice to have a lot of things.  If you're that experienced, maybe you should lend your energies to the efforts to develop Ubuntu.  Complaining about a free product because you can't make enough money off it isn't exactly helpful.

I don't know of any version of linux that can replace Windows for thick-headed stability.  Microsoft has a lot of resources to hammer it flat.  But I also wouldn't go back to using Windows if they paid me.  Ubuntu is well worth the tweaking required.  Personally, I've had very few problems, and those I did have, the solutions just required a little research.  Call it 'doing your part', and say "thank you, Ubuntu developers".  It's not perfect, but it's excellent.

---

### Post by IgnorantGuru on 2007-02-13
Also, you can thank the closed-source drivers from ATI and NVidia for a lot of the problems.  The open-source parts work much more reliably.  Integration with the proprietary drivers is sketchy, but that is not entirely an Ubuntu dev issue.

Unless your business customers need great 3D graphics, consider using the open drivers.

---

