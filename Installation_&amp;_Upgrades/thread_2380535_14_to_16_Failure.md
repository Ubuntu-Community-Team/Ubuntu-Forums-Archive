---
title: "14 to 16 Failure"
date: 2017-12-18
forum: Installation &amp; Upgrades
---

### Post by glenn15 on 2017-12-18
I started of this problem while running a dual boot Ubuntu 17 and Windows 7 on my Dell Laptop. While not paying attention to the boot process, my laptop started booting into Ubuntu, I wanted Win7, so not having a cancel operation I turned off the power, bad move on my part.
Turned power on and boot went to grub rescue. No commands would work in grub rescue and I did not have a boot/repair disk for Win7 and this is a refurbished laptop and did not come with a Win7 disk. This laptop is strictly a toy for the grand kid and me and contains no data that needed to be save so I was lax in any recovery or back up and this is not a problem.

The problem is:
I can run Ubuntu from disk (14,04), load 14.04, but when I try to upgrade to 16.10 (via GUI Icon or pop up requestioning to Upgrade. The upgrade will not always work and when it does 16.10 will fail to load within 24 hours. I have reloaded 14.04 and have been running error free for several days.
Thinking, which can be dangerious, I had a hard drive or memory problem I ran memory test and reformated the hard drive (to Ubuntu format). I still got the same response.
Reading the forum there appears to be a problem when trying to Upgrade to 16.10, saw one mention of it.

The question is:
Iwill be getting a Win7 dvd in the next couple of day and I will, again, reformat the disk, create two particians, one for windows and one for Ubuntu. Then I will load windows 7.
Now do I star again with Ubuntu 14.04 ... to 17.?, or jump the shark and go directly to 17. What is the best/most reliable process.

Thank you in advance for all help.

---

### Post by DuckHook on 2017-12-18
Welcome to the forums, glenn15.

If you are intent on going to 17.10, then you can just install 17.10 outright. No need to go 14.04&#8594;16.04&#8594;16.10 etc.

You are unable to upgrade from 14.04 to 16.10 because of multiple reasons:

[LIST=1]
[*]the repositories for 16.10 no longer exist (well, they do exist but have been moved to archives—which is pretty much the same thing). 16.10 is out of support, as 17.04 will also soon be. That's the problem with standard releases: they last all of 9 months and then, kaput. On the other hand, it should be easy to upgrade to 16.04. Why do you need to upgrade past 16.04? It's LTS and therefore stable, secure, reliable and trouble-free. Also, supported until 2021.
[*]Even if the repos were still available, you can't jump multiple versions at once. The only exception to this is LTS to LTS, so you can go from 14.04 to 16.04.
[/LIST]
If you like 16.04, you can also install that one off the bat. No need at all to start at 14.04 .

I recommend that you stick with 16.04 until the next LTS which will be 18.04. Even then, wait until the first point release—let others work out the bugs first.

---

### Post by glenn15 on 2017-12-19
The only reason going to 17.10 is that is what I (tought) i had before the crash and every thing worked, On my laptop 16.04 crashes after about a days use, When I try to boot I get a  a prompt "int???", cannot remember the rest as it has been several days ago and I did not write it down, senior moment, I have been running 14.04 for a couple of days with no crashes, because I have the DVD, but there are several apps that are out of date, such as Firefox and rather than try to upgrqade a bunch of app I would sooner go with a more recent version of Ubuntu. As soon as I get my windows7 disk I will also load 17.10
Thank you for the information.

---

