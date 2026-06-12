---
title: "Post your Lucid bootcharts or boot times!"
date: 2009-12-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-12-01
You may have remembered this topic from the Karmic dev cycle and now I'm bringing it back so that we can measure the evolution of boot time improvements.[B]

In order to participate, just install pybootchartgui and bootchart through synaptic. You may need to enable the universe repo first. The bootchart will be created in the /var/log/bootchart directory.
[/B][B] 
Don't use the attachment  function. It makes the images small and unreadable.[/B]

Let's begin.

[http://img6.imageshack.us/img6/1218/kingfisherlucid20091201.png](http://img6.imageshack.us/img6/1218/kingfisherlucid20091201.png)

---

### Post by philinux on 2009-12-02
Got bootchart version 0.90.2-5 with pybootchartgui 0+r139-2. Recently updated to crop chart when desktop achieved.

Boot time now recorded correctly at 41 seconds to usable desktop. Previous boot was 1.01.

[bootchart]("https://files.one.ubuntu.com/56b84644-024f-4824-a95b-25130c33e340")

---

### Post by Starks on 2009-12-02
The new bootchart and pybootchartgui updates didn't even shave off a second for me.

---

### Post by Gina on 2009-12-02
Lucid takes well over a minute to boot on my AMD64 desktop!!  Something like 10 times the goal of 10 secs :(  It doesn't help that it displays a command line for about a minute!

---

### Post by philinux on 2009-12-02
Just rebooted and got a bootchart time of 37.54. Wow.

---

### Post by Starks on 2009-12-02
I've heard that having multiple partitions would negate the benefits of ureadahead.

---

### Post by philinux on 2009-12-02
> **Starks said:**
> I've heard that having multiple partitions would negate the benefits of ureadahead.

Got four on the lucid disk. /, /swap, /home and /data.

---

### Post by hugmenot on 2009-12-02
Getting rid of HAL shaved off a few secs.

[[IMG]http://imgur.com/v9xaw.png[/IMG]](http://imgur.com/v9xaw.png)

---

### Post by Starks on 2009-12-02
Here's my bootchart after a ureadahead reprofiling.

48 seconds to an idle desktop doesn't sound too bad.

[http://img146.imageshack.us/img146/1676/kingfisherlucid20091202.png](http://img146.imageshack.us/img146/1676/kingfisherlucid20091202.png)

---

### Post by MacUntu on 2009-12-02
> **hugmenot said:**
> Getting rid of HAL shaved off a few secs.

Considering the CPU that's really nice, it's just not 1337. :D

---

### Post by b3n87 on 2009-12-02
> **hugmenot said:**
> Getting rid of HAL shaved off a few secs.



Do you have a SSD?

---

### Post by MacUntu on 2009-12-02
Charted my notebook: 15.98s - wish I had a SSD.

[[img]http://img.xrmb2.net/638305.jpg[/img]](http://img.xrmb2.net/images/638305.png)

---

### Post by b3n87 on 2009-12-02
I really want this one:

[http://www.phoronix.com/scan.php?page=article&item=ocz_agility_ex&num=1](http://www.phoronix.com/scan.php?page=article&item=ocz_agility_ex&num=1)

check out the results

---

### Post by hugmenot on 2009-12-02
> **b3n87 said:**
> Do you have a SSD?

Yeah, but a crappy 1st-gen Samsung one.

I got rid of a lot of cruft though. Things I will never need, why should I load all that garbage?

---

### Post by hugmenot on 2009-12-02
I was wondering about the long period of I/O only (with the long bar of ureadahead) in all your plots. Is this the spinning disks HDD mode? Because in my plot both CPU and I/O are at full tilt in the beginning.

Can anyone explain why?

---

### Post by yoasif on 2009-12-02
My chart isn't very pretty at all: [http://imgur.com/6BRLV.png](http://imgur.com/6BRLV.png)

---

### Post by MacUntu on 2009-12-02
> **hugmenot said:**
> Is this the spinning disks HDD mode?

AFAIK, yes.

> **hugmenot said:**
> Can anyone explain why?

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027726.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027726.html) 

[read: sreadahead = ureadahead SSD mode, readahead = ureadahead HDD mode]

---

### Post by hugmenot on 2009-12-02
> **MacUntu said:**
> AFAIK, yes.
[read: sreadahead = ureadahead SSD mode, readahead = ureadahead HDD mode]

Thanks. Relevant quote:

> This is because we need to minimise seek as much as possible.  If we ran
it in the background, we'd be competing for disk access with other
processes.  We'd be seeking back and forth all over the disk, and thus
have a net loss.

---

### Post by philinux on 2009-12-03
> **hugmenot said:**
> Yeah, but a crappy 1st-gen Samsung one.

I got rid of a lot of cruft though. Things I will never need, why should I load all that garbage?

What sort of cruft did you get rid of?

---

### Post by hugmenot on 2009-12-03
> **philinux said:**
> What sort of cruft did you get rid of?

Cups, HAL, Ubuntu One, Apport, Winbind, Update-notifier, apt daemon, apparmor, bluetooth, all accessibility modules,  any glockenspiel-like system sounds, etc.

You can look in the init scripts for things you may not need started. But be careful.
```
ls /etc/rc[5S].d/S* /etc/init
```

You can go into the »Startup Applications« panel and disable some unneeded daemons there.
For instance, the longest times in my boot are caused by modprobe (I blacklisted some modules there), then Tomboy, then Gnome-do. They just load a lot of resources. But I want the functionality, so they stay in.

But on the whole I&#8217;m pretty anal about cruft. That&#8217;s why the recent additions to ubuntu-desktop irritate me. But not for long &#8230;

---

### Post by Starks on 2009-12-03
46 seconds after xsplash was disabled by the devs.

[http://img514.imageshack.us/img514/5295/kingfisherlucid20091203.png](http://img514.imageshack.us/img514/5295/kingfisherlucid20091203.png)

---

### Post by MacUntu on 2009-12-04
> **hugmenot said:**
> HAL
Did that actually save you any time?

I added the xorg-edgers [0] and halsectomy [1] PPA, added the two udev-rules posted by Martin Pitt [2], and temporarily removed banshee before saying good bye to hal. Boot time didn't change, though.

[0] [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
[1] [https://launchpad.net/~pitti/+archive/halsectomy](https://launchpad.net/~pitti/+archive/halsectomy)
[2] [http://www.piware.de/2009/11/sudo-dpkg-p-hal/](http://www.piware.de/2009/11/sudo-dpkg-p-hal/)

---

### Post by hugmenot on 2009-12-04
Just to check, did you uninstall HAL, or is it still starting? 

Myself I just renamed /etc/init/hal.conf to /etc/init/hal.conf.deac. I got just under 2 seconds out of it.

I think halectomy PPA is no longer necessary. Edgers should do it.

edit: Hal also kept showing up in powertop waking up the CPU. I can&#8217;t tell if udev is visible there, and if this saves any power at all.

---

### Post by Starks on 2009-12-04
Is login screen typing counted towards the boot time?

---

### Post by MacUntu on 2009-12-04
> **hugmenot said:**
> Just to check, did you uninstall HAL, or is it still starting?

I purged it.

> **hugmenot said:**
> I think halectomy PPA is no longer necessary. Edgers should do it.

Just checked - you are right. :-)

---

### Post by hugmenot on 2009-12-04
Yes, it stops when gnome-panel is started, I think. 

see [https://bugs.edge.launchpad.net/ubuntu/+bug/438015/comments/5](https://bugs.edge.launchpad.net/ubuntu/+bug/438015/comments/5)

---

### Post by Starks on 2009-12-13
[http://img192.imageshack.us/img192/3589/kingfisherlucid20091212.png](http://img192.imageshack.us/img192/3589/kingfisherlucid20091212.png)

With Plymouth working properly.

---

### Post by phillw on 2009-12-13
What's a boot time ?    >>>>>> Runs !!!

My Laptop gets booted when a new kernel wants to load itself - even then, I believe, I don't even have to boot for that.

I like Ubuntu because of its 'up' time - running a LAMP server and shortly to add a MAIL Server aren't going to give me the fastest boot times in the world :D

We need a new thread - for 'up' time  ;)

I'm loving 10.04

Phill.

---

### Post by VMC on 2009-12-13
This, so far, is the fastest Ubuntu ever. No boot chart, but from grub to desktop under 25 seconds! 

Using single SATA hard drive, P4 - 2.65ghz, 2 gig ram, Intel i865 integrated video.

---

### Post by lean on 2009-12-13
25sec, that is really impressive. How big is, and what is the rotation speed of, the drive?
Also, a bootchart could be nice, for proof..

---

### Post by Starks on 2009-12-13
Yes, proof would be nice. Otherwise you're just misleading the developers and wasting their time.

A machine as old as yours should not be in such low territory even when on a single partition and ureadahead profiled.

I also challenge your use of desktop. A visible desktop is a far cry from a usable desktop.

---

### Post by VMC on 2009-12-13
" ...misleading the developers and wasting their time."

Your giving this topic of yours way to much credit. 

And how do you know developers are even reading it. Let alone wasting any ones time.

Be more specific next time in choosing a topic title to reflect what you want:

"Post your Lucid bootcharts **[SIZE="4"]or boot times![/SIZE]**

---

### Post by vade on 2009-12-14
12.39 seconds with 7200rpm WD Caviar Black. radeon.modeset=1, splash off.

[http://img268.imageshack.us/img268/1071/cowlucid2009121410.png]("http://img268.imageshack.us/img268/1071/cowlucid2009121410.png")

---

### Post by Merk42 on 2009-12-14
What/how do I use to make these pictures?
I tried installing what was in the second post but it gave Server Error (500)

---

### Post by MacUntu on 2009-12-14
It's just bootchart and pybootchartgui. If you get a server error, try another mirror.

---

### Post by ranch hand on 2009-12-14
You need pybootchart from the repo.  It will also install bootchart.

If you are having a problem you might try a different repo.  I have 4 installs, one uses the main and one the canadian and two the us repos.  Get different speeds all the time.  Some times one is the best and other times it is another.

---

### Post by hobo on 2009-12-14
My results: 

[https://one.ubuntu.com/files/#path=/My%20Files/hobo-laptop-lucid-20091214-2.png]("https://one.ubuntu.com/files/#path=/My%20Files/hobo-laptop-lucid-20091214-2.png")

00:30.52   **I can live with that!**

---

### Post by ranch hand on 2009-12-14
All that link does is take me to a sign in for Ubuntu1.

---

### Post by hobo on 2009-12-14
Well make a new account and sign-in. It's free and the place, I would think, most large posts will be stored. If you are a member of Launchpad I think you just use that UID and PW.

---

### Post by Merk42 on 2009-12-14
> **hobo said:**
> Well make a new account and sign-in. It's free and the place, I would think, most large posts will be stored. If you are a member of Launchpad I think you just use that UID and PW.

The point is that even when you I do log in, it just takes me to my stuff, not yours, not your picture.

---

### Post by vade on 2009-12-14
> **hobo said:**
> My results: 

[https://one.ubuntu.com/files/#path=/My%20Files/hobo-laptop-lucid-20091214-2.png]("https://one.ubuntu.com/files/#path=/My%20Files/hobo-laptop-lucid-20091214-2.png")

00:30.52   **I can live with that!**
The link doesn't work. The path is relative to your account, so it only works for you.

---

### Post by ranch hand on 2009-12-14
I have just "completely removed" bootchart and pybootchartgui and then installed them again.

There is no .png.

pybootchartgui must not work.

Anyone have an idea here, I am stuck.  It worked the last time I checked on another install on this drive.

---

### Post by spaceBARbarian on 2009-12-15
[11.67 Seconds on Seagate 7200.2 320GB HDD]("http://lh6.ggpht.com/_Gx36k4zYCQM/SybNn-2MIdI/AAAAAAAAADA/TzXZFsDxfkE/s800/shev_lynx64_nokmap.png")
Looks like were fairly close to that 10s goal :)
Originally I was getting like 15, so I did a re-"profile" and messed around in sysv-rc-conf, and now its 11-12 sec constant.

---

### Post by philinux on 2009-12-15
Mine is back to 45 seconds from 56. Improvement yes. Got Plymouth installed.

But there's a lot of time with nothing going on.

Can someone explain why?

---

### Post by hobo on 2009-12-15
> The link doesn't work. The path is relative to your account, so it only works for you.

Sorry about that. It looks like I can only SHARE by using an email address. That sucks. I will figure out another way to post.

---

### Post by Jordanwb on 2009-12-15
> **yoasif said:**
> 2 Minute Boot Time

Oh dear.

I'm gonna try Alpha 1 on my laptop this afternoon and see what I can squeeze out of it.

---

### Post by ranch hand on 2009-12-15
> **philinux said:**
> Mine is back to 45 seconds from 56. Improvement yes. Got Plymouth installed.

But there's a lot of time with nothing going on.

Can someone explain why?
It looks to me like the main things going on then are the gnome session and power management and network manager related.  Seeing that we have gotten a bunch of stuff related to those things in updates and breakage, that may well be why you are somewhat slow.

I must say though that the boot time really is nice.  I also use 9.04 a lot and when I boot in there it seems to take for ever after fooling with Lounge Lizard all day.

---

### Post by MacUntu on 2009-12-15
Bootchart doesn't work for me with -8. :(

Edit: Working again - 15 seconds.

---

### Post by Podex on 2009-12-16
I get 22.34 seconds and I'm pretty happy with it. I just installed Lucid and the first few boots I was messing with Plymouth and Nvidia drivers and got 40-50 seconds. I wonder if I'll get less than 15 seconds on Lucid with my computers eventually.

[http://img30.imageshack.us/img30/4822/koendesktoplucid2009121.png](http://img30.imageshack.us/img30/4822/koendesktoplucid2009121.png)

---

### Post by Jordanwb on 2009-12-16
38 seconds ain't bad for a laptop:

[http://img706.imageshack.us/img706/2771/jordanwblaptoplucid2009.png](http://img706.imageshack.us/img706/2771/jordanwblaptoplucid2009.png)

I can't seem to find the program that lets me disable services. :confused:

*Edit*

I found update-rc.d which will work for now. I reduced it to 28 seconds simply by disabling cpufrequtils and writing my own script to change to governor to performance.

---

### Post by lean on 2009-12-17
> **Jordanwb said:**
> 38 seconds ain't bad for a laptop:

[http://img706.imageshack.us/img706/2771/jordanwblaptoplucid2009.png](http://img706.imageshack.us/img706/2771/jordanwblaptoplucid2009.png)

I can't seem to find the program that lets me disable services. :confused:

It doesn't look like you are using ureadahead. That means their should be some real improvements in store for you.

You can use the package bum, to configure services.

---

### Post by Schrotthaufen on 2009-12-17
4.09 seconds on a Lenovo W500 with an 80GB Intel Postville.

---

### Post by MacUntu on 2009-12-17
How about a complete chart? :D

---

### Post by hugmenot on 2009-12-17
> **Schrotthaufen said:**
> 4.09 seconds on a Lenovo W500 with an 80GB Intel Postville.

Kul. Can you make a video of bootup? On my Thinkpad BIOS POST takes longest.

---

### Post by Schrotthaufen on 2009-12-18
> **MacUntu said:**
> How about a complete chart? :D


It's really not that interesting ;)
Should be at [www.sigma-server.com/sp/simon-laptop-lucid-20091217-1.png](www.sigma-server.com/sp/simon-laptop-lucid-20091217-1.png)

@hugmenot, 4.09 is only bootchart, from grub to desktop it's about 6-7 seconds, post-time has decreased by 3 seconds with the last bios update - all in all about 15 seconds from power-on to desktop... I'll try to make a video of two W500 with/without bios update and with ubuntu lucid and win 7 this weekend.

---

### Post by Jordanwb on 2009-12-18
> **lean said:**
> It doesn't look like you are using ureadahead. That means their should be some real improvements in store for you.

I do have ureadahead installed but it keeps dying on me. Even with ureadahead dying 10.04 is noticeably faster than 9.04

> **lean said:**
> You can use the package bum, to configure services.

I'll take a look at that.

*Edit*

I don't know what happened but Bootchart ain't working now.

*Edit #2*

Nevermind, it just took its time. Oh damn it shot up to 40 seconds. I rebooted and it went down to 28 seconds.

---

### Post by MacUntu on 2009-12-18
> **Schrotthaufen said:**
> It's really not that interesting ;)
Should be at [www.sigma-server.com/sp/simon-laptop-lucid-20091217-1.png](www.sigma-server.com/sp/simon-laptop-lucid-20091217-1.png)

I meant a completed boot process (which includes desktop loading, since that's what bootchart measures ;)).

---

### Post by Schrotthaufen on 2009-12-18
[www.sigma-server.com/sp/simon-laptop-lucid-20091218-2.png](www.sigma-server.com/sp/simon-laptop-lucid-20091218-2.png)

Did you mean something like that?

---

### Post by yoasif on 2009-12-20
Seeing a much improved boot time... [http://imgur.com/Axjxu.png](http://imgur.com/Axjxu.png)

---

### Post by farrell on 2009-12-20
14.43s on a stock ThinkPad X200T (C2D SL9300, 7200RPM HDD) with compiz disabled.

The boot process is still a bit verbose (even with 'quiet splash') but incredibly fast if you're used to karmic's boot time!

---

### Post by Starks on 2009-12-31
Almost under 30 seconds now.

[http://img691.imageshack.us/img691/569/kingfisherlucid20091224.png](http://img691.imageshack.us/img691/569/kingfisherlucid20091224.png)

I'm quite certain that I'd be in the 20 second range if I only had a single partition and swap.

---

### Post by celticbhoy on 2010-01-06
Just over 32secs on multi partitioned aspire one. Karmic never went below 1:11

---

### Post by Starks on 2010-01-07
25 seconds after a root reinstall

[http://img130.imageshack.us/img130/6705/kingfisherlucid20100107.png](http://img130.imageshack.us/img130/6705/kingfisherlucid20100107.png)

---

### Post by KrazyPenguin on 2010-01-07
> **Starks said:**
> 25 seconds after a root reinstall

[http://img130.imageshack.us/img130/6705/kingfisherlucid20100107.png](http://img130.imageshack.us/img130/6705/kingfisherlucid20100107.png)

I think these numbers would have more meaning if people posted both karmic vs lucid , obviously using the same hardware.

I would be truly interested to know how fast that same computer boots karmic.

Thanks.

---

### Post by xc3RnbFO8P on 2010-01-07
Here is mine Karmic 01:07.48 and Lucid 00:20.12...

---

### Post by Starks on 2010-01-07
> **KrazyPenguin said:**
> I think these numbers would have more meaning if people posted both karmic vs lucid , obviously using the same hardware.

I would be truly interested to know how fast that same computer boots karmic.

Thanks.
45 seconds to a minute

---

### Post by KrazyPenguin on 2010-01-07
> **Starks said:**
> 45 seconds to a minute

Wow makes me want to try Lucid!!!

I haven't installed it yet, but i think i will download a daily and see how it goes.

---

### Post by ceykooo on 2010-01-08
65 Seconds.  Its a 4-year old laptop, but I thought my new hard drive would have made it a bit lower.  Guess SSD would be the only option.

[http://img44.imageshack.us/img44/3552/ceykolaptoplucid2010010.png](http://img44.imageshack.us/img44/3552/ceykolaptoplucid2010010.png)

---

### Post by dagrump on 2010-01-08
My boot times are fine on my laptops, but, the desktop machines are terrible. If you have more than one drive & #%&@2 is on a different MBR the the lucid install it takes forever.
As far as I'm concerned grub2 is a bust. I don't understand why it has issues with being on a different drive than the install, grub did not display this problem. 
Making the boots faster on single drive systems is a great goal but turning systems that have more than one OS into a lumbering turnip is a crappy trade off. Breaking things is something that should be avoided like the plague. 
Now before some one pipes up with the "How often do you boot a desktop?"
I have the terrible habit of turning the damn machine off if I not using it, so I could boot the machine several times a day. Seems grub2 wasn't ready for prime time yet!
What was that curse "may you live in exciting times"?

---

### Post by KrazyPenguin on 2010-01-08
> **dagrump said:**
> My boot times are fine on my laptops, but, the desktop machines are terrible. If you have more than one drive & #%&@2 is on a different MBR the the lucid install it takes forever.
As far as I'm concerned grub2 is a bust. I don't understand why it has issues with being on a different drive than the install, grub did not display this problem. 
Making the boots faster on single drive systems is a great goal but turning systems that have more than one OS into a lumbering turnip is a crappy trade off. Breaking things is something that should be avoided like the plague. 
Now before some one pipes up with the "How often do you boot a desktop?"
I have the terrible habit of turning the damn machine off if I not using it, so I could boot the machine several times a day. Seems grub2 wasn't ready for prime time yet!
What was that curse "may you live in exciting times"?

This is a thread about boot times for Lucid which is still alpha.
If you are having problems you need to use a stable version like Karmic or file a bug at launchpad.  You might also consider using the old grub instead of grub2.

---

### Post by dagrump on 2010-01-09
Wow, from some one who isn't even running the testing version comes the standard old dodge!
As far as it goes, if the grub2 issue doesn't affect you then you won't notice this issue has been discussed since the karmic dev cycle. The are various work a rounds & a possible fix upstream. Which seems to fix the issue, of course it hasn't made it here yet.
But telling some one to use a stable release, that still displays the issue that was at hand, is not very useful.
Want to be helpful, research the issue a bit first before getting defensive.

---

### Post by taavikko on 2010-01-11
Good day to you all.

After cold boot:
Not bad when launching gnome-terminal and firefox around 33s
and even have to login before to do that (not using auto-login)

hp-dv5 1153eo

---

### Post by KrazyPenguin on 2010-01-11
> **dagrump said:**
> Wow, from some one who isn't even running the testing version comes the standard old dodge!
As far as it goes, if the grub2 issue doesn't affect you then you won't notice this issue has been discussed since the karmic dev cycle. The are various work a rounds & a possible fix upstream. Which seems to fix the issue, of course it hasn't made it here yet.
But telling some one to use a stable release, that still displays the issue that was at hand, is not very useful.
Want to be helpful, research the issue a bit first before getting defensive.

I still don't understand what the grub2 has to do with posting your boot times and charts.  If you have an issue than file a bug report.

---

### Post by Ibidem on 2010-01-12
Here are my latest, attached; not quite sure how to read them.[IMG]http://ubuntuforums.org/attachment.php?attachmentid=143441&stc=1&d=1263331970[/IMG]

---

### Post by celticbhoy on 2010-01-12
The new updates with Plymouth puts 15 - 20 secs on my boot, still early in development though.

---

### Post by Starks on 2010-01-12
> **Ibidem said:**
> Here are my latest, attached; not quite sure how to read them.
We can't read them either because you uploaded them as an attachments. Use imgur or imageshack.

---

### Post by Woody1987 on 2010-01-17
I just got an ssd and thought i would try installing alpha 2 on it to see how it runs, and wow, it boots super fast. According to bootchart it took just 6.89 seconds!

[http://tinypic.com/r/25tyhvr/6](http://tinypic.com/r/25tyhvr/6)

---

### Post by VMC on 2010-01-17
> **Woody1987 said:**
> I just got an ssd and thought i would try installing alpha 2 on it to see how it runs, and wow, it boots super fast. According to bootchart it took just 6.89 seconds!

[http://tinypic.com/r/25tyhvr/6](http://tinypic.com/r/25tyhvr/6)

There's already a thread for the [boot times]("http://ubuntuforums.org/showthread.php?t=1343305&highlight=boot+times"). Maybe you can put your results in there.

---

### Post by Woody1987 on 2010-01-17
6.89 seconds on ssd.

[http://imgur.com/PkLbg.png](http://imgur.com/PkLbg.png)

Karmic on the same drive takes about 50 seconds.

---

### Post by vishalrao on 2010-01-17
congrats on SSD, which brand/model? im assuming you dont see any dmesg errors/warnings for ATA like i do with my crucial ct128m225 ? :D

---

### Post by farrell on 2010-01-17
@Woody1987: While booting in 6.89s, ureadahead was profiling your bootup. Your second bootup may be even faster. The image below shows disk access on an aligned bootup.

With my new X25-M, the C2D SL9400 is now the bottleneck on my machine (though there is still some time wasted during bootup...)

[http://i.imgur.com/Yetef.png](http://i.imgur.com/Yetef.png)

With 9.04s, the goal for 10.04 is met :D

---

### Post by cariboo on 2010-01-17
Merged Boot time thread.

---

### Post by Woody1987 on 2010-01-17
> **vishalrao said:**
> congrats on SSD, which brand/model? im assuming you dont see any dmesg errors/warnings for ATA like i do with my crucial ct128m225 ? :D

Its a Kingston SSDNow V Series 64GB. One of the cheapest out there and despite being relatively cheap compared to others, it runs really well. And no errors or warnings in dmesg.

---

### Post by tad1073 on 2010-01-17
mine

[http://imagebin.ca/view/5g2c7mb.html](http://imagebin.ca/view/5g2c7mb.html)

---

### Post by tad1073 on 2010-01-17
> **farrell said:**
> @Woody1987: While booting in 6.89s, ureadahead was profiling your bootup. Your second bootup may be even faster. The image below shows disk access on an aligned bootup.

With my new X25-M, the C2D SL9400 is now the bottleneck on my machine (though there is still some time wasted during bootup...)

[http://i.imgur.com/Yetef.png](http://i.imgur.com/Yetef.png)

With 9.04s, the goal for 10.04 is met :D

What can I do to get my boot to 9 seconds?

---

### Post by farrell on 2010-01-17
@tad1073:

> What can I do to get my boot to 9 seconds?

ureadahead does not work correctly for you. Most of the disk access should be generated by the ureadahead process (see my bootchart above). Maybe you can solve this by forcing ureadahead to re-profile your bootup. This can be done by deleting the file /var/lib/ureadahead/pack. You may want to read the manual before deleting files:

```
$ man ureadahead
```

I've also noticed that hald is started in your bootchart. I thought hal was removed for Lucid Alpha 2... Did you upgrade from Karmic to Lucid? If yes, installing Lucid from scratch should be worth a try.

And finally... your bootchart shows a lot of processes for device init. You might want to disable devices you don't use (bluetooth?) in your BIOS, so they don't need initialization during bootup.

---

### Post by Starks on 2010-01-17
> **tad1073 said:**
> What can I do to get my boot to 9 seconds?
Do you have an SSD?

---

### Post by tad1073 on 2010-01-17
> **Starks said:**
> Do you have an SSD?
  no I do not

---

### Post by OlyPerson on 2010-01-17
> **tad1073 said:**
> no I do not

You'll need to have one to get sub ten second boots.

---

### Post by Starks on 2010-01-18
Convential hard drives are stuck in the mid 20's and above.

If you have a RAID5 Raptor setup, you might hit 15 seconds if you pray and rub cheetah blood all over it.

---

### Post by Robin Nixon on 2010-01-18
With Alpha 2, just timed by hand from the moment the first disc access message appears until the desktop wallpaper is loaded was 17 seconds - which is amazing for that PC.

---

### Post by cariboo on 2010-01-18
You'd get more accurate results, if you install bootchart, it is in the repositories.

---

### Post by gabo.cr on 2010-01-18
I have 33.41 seconds on Alpha 1.

---

### Post by Robin Nixon on 2010-01-18
> **cariboo907 said:**
> You'd get more accurate results, if you install bootchart, it is in the repositories.

I just installed it and get 22.48 seconds, but visually it *looks* like 17 seconds, which I think is an important figure too.

---

### Post by Robin Nixon on 2010-01-19
> **Robin Nixon said:**
> I just installed it and get 22.48 seconds, but visually it *looks* like 17 seconds, which I think is an important figure too.

And with today's update that's now 13.12 - fantastic!

---

### Post by Jordanwb on 2010-01-19
55 Seconds. That's pathetic. That's far slower than it should be. I got 30 seconds out of this low end laptop a few weeks ago.

Removing modemmanager or disabling plymouth trims off 7 seconds:

[[IMG]http://img696.imageshack.us/img696/1608/jordanwblaptoplucid2010.th.png[/IMG]](http://img696.imageshack.us/img696/1608/jordanwblaptoplucid2010.png)

---

### Post by woodbj on 2010-01-19
How do you set up bootchart, I have it installed via apt-get but what do i do now

---

### Post by Merk42 on 2010-01-19
> **woodbj said:**
> How do you set up bootchart, I have it installed via apt-get but what do i do now

If you installed bootchart and pybootchart there is no setup.
Just check /var/log/bootchart

---

### Post by woodbj on 2010-01-20
> **Merk42 said:**
> If you installed bootchart and pybootchart there is no setup.
Just check /var/log/bootchart

Thanks, heres my chart

---

### Post by hobo on 2010-01-20
19.01 sec. That's ~ 10 sec better than Alpha 1. Using alpha2 with kernel 2.6.32.11. This is great!

---

### Post by cecilpierce on 2010-01-20
old Hardy is faster then Lucid !

---

### Post by andrewabc on 2010-01-20
I presume they removed the 45 second delay added to bootchart in 9.10?

Or is everyone manually editing config file to removed the 45 second sleep?

---

### Post by ranch hand on 2010-01-20
I would really like someone to explain how to use bootchart.

It seems simple enough that I should be able to do this.  As a matter of fact, I can do it.  On some installations.

There are 2 of 7 installs of 10.04 and 1 of 2 installs of  9.10 that it does not work on at all.  I tried this bugger when we were testing 9.10 and never got it to work.  I tried it again when we started testing 10.04 with the tool chain and it did not work on the only installation that I had at that time.

That installation, 9.10>10.04 upgrade, is one that still will not work.  The other is an install from a daily before A1, "old" but a clean install that I have not done any big messing with.

All I get is the .tgz file, which in the case of the upgrade is an improvement as I did not get anything before when I tried this bugger.

The 9.10 that works is Zenix.

I guess my question is - WTF?

---

### Post by andrewabc on 2010-01-20
> **ranch hand said:**
> I would really like someone to explain how to use bootchart.

It seems simple enough that I should be able to do this.  As a matter of fact, I can do it.  On some installations.

There are 2 of 7 installs of 10.04 and 1 of 2 installs of  9.10 that it does not work on at all.  I tried this bugger when we were testing 9.10 and never got it to work.  I tried it again when we started testing 10.04 with the tool chain and it did not work on the only installation that I had at that time.

That installation, 9.10>10.04 upgrade, is one that still will not work.  The other is an install from a daily before A1, "old" but a clean install that I have not done any big messing with.

All I get is the .tgz file, which in the case of the upgrade is an improvement as I did not get anything before when I tried this bugger.

The 9.10 that works is Zenix.

I guess my question is - WTF?

Looking in correct folder?
filesystem->var->log->bootchart
/just checking

---

### Post by ranch hand on 2010-01-20
> **andrewabc said:**
> Looking in correct folder?
filesystem->var->log->bootchart
/just checking
Yes, as I said there are 6 of 9 installs that this works on and 3 (one 9.10 and two 10.04) that it doesn't work on.

On the three that do not work all I get is the .tgz file and no graphic file.  You can wade through a lot of pages in 3 files nad get the info but I am not doing it.

In the 9.10 Ubuntu that does not work it was installed with bootchart-java instead of pybootchartgui.  It did not work.  Installed pybootchartgui, which removed the java packages involved (3).  Still does not work.

The 2 10.04 installs that do not work look identical to the ones that do, as far as installation goes.

I have never had this bugger work right across the board and am, frankly tired of the thing.  I have a clock.  It would be nice to get it to work, though, just on general principles.

Seeing that the offending OS' generate the .tgz file, I suppose I should boot to those and file a bug from the 9.10 and one from a 10.04 against pybootchartgui.  Is that right?

---

### Post by espen77 on 2010-01-21
So i got 40 sec on a TP X200t with SSD and encrypted root.
But it dont feel so long sins it is only a few secounds between entering the passwords.

---

### Post by j_baer on 2010-01-21
* Put the pedal to the metal *

  [Lucid Fast Boot Wallpaper]("http://www.flickr.com/photos/j_baer/4293782389/")

:)

---

### Post by Jordanwb on 2010-01-21
I reinstalled A2 and ran all the updates which may not make any difference, anyways. I disabled skype - which may be an issue, and my boot time is 40 seconds, 5 seconds better than 9.04. Better, but not good enough.

Maybe replacing gdm with slim will make a difference.

---

### Post by woodbj on 2010-01-21
Now 25 Secs thats better
[http://tinypic.com/r/mjr9k8/6](http://tinypic.com/r/mjr9k8/6)

---

### Post by norm7446 on 2010-01-23
32.07 First attempt at this. Gonna Overclock the system today, and see if I can Improve.

---

### Post by philinux on 2010-01-23
This is the best I got so far. 25.81 seconds.

---

### Post by Alabamaschalk on 2010-01-24
Hi There!

I am a little bit confused. After the first install of Alpha 2 I got something around 30 sec, then after some upgrades I am ending up at around 1 min.
Does anybody have an idea how to get my 30 sec back?
Even with Alpha 1 I got 39 sec,

Please forgive me if I make something wrong with the upload. I never did that before...

[[IMG]http://img264.imageshack.us/img264/6566/ansgarnetbooklucid20100.th.png[/IMG]](http://img264.imageshack.us/my.php?image=ansgarnetbooklucid20100.png)

[[IMG]http://img691.imageshack.us/img691/6566/ansgarnetbooklucid20100.th.png[/IMG]](http://img691.imageshack.us/my.php?image=ansgarnetbooklucid20100.png)

---

### Post by ankspo71 on 2010-01-25
Hi,
This is my very first boot chart, and I don't know how to read my boot time... except maybe to say it took 51 seconds until the computer became idle. Can someone tell me if I am correct to assume that this is for a total boot time? Getting to a desktop is much faster than that though. Pentium 4 (478 socket) 3.0, 2gb ram, Lucid Alpha 2 (8.5gb used space I think). My Plymouth doesn't display either, so I am hoping that causes a delay my boot time lol.
Thanks,

Woops sorry, my original image doesn't display right.
[http://i182.photobucket.com/albums/x7/jamesb71/Lucid-lucid-20100125-1.jpg](http://i182.photobucket.com/albums/x7/jamesb71/Lucid-lucid-20100125-1.jpg)

Hmm...  both uploading here and photobucket resulted in resized images!

---

### Post by Seventh Reign on 2010-01-25
> **ankspo71 said:**
> Hi,
This is my very first boot chart, and I don't know how to read my boot time... except maybe to say it took 51 seconds until the computer became idle. Can someone tell me if I am correct to assume that this is for a total boot time? Getting to a desktop is much faster than that though. Pentium 4 (478 socket) 3.0, 2gb ram, Lucid Alpha 2 (8.5gb used space I think). My Plymouth doesn't display either, so I am hoping that causes a delay my boot time lol.
Thanks,

Woops sorry, my original image doesn't display right.
[http://i182.photobucket.com/albums/x7/jamesb71/Lucid-lucid-20100125-1.jpg](http://i182.photobucket.com/albums/x7/jamesb71/Lucid-lucid-20100125-1.jpg)

Hmm...  both uploading here and photobucket resulted in resized images!


Open your bootchart image with your image viewer (EOG most likely) and scroll near the upper left corner.  It will tell you the time there.

---

### Post by ankspo71 on 2010-01-25
Hi,
Thanks, I didn't see it all the way over there in the corner. My boot time is still 51 seconds. Ouch! I suppose it's not too bad for a single core computer though.

---

### Post by Starks on 2010-01-25
Meh.

[http://imgur.com/QnEWD.png](http://imgur.com/QnEWD.png)

---

### Post by Starks on 2010-01-25
Also, I can't stress enough that you guys learn how to use direct links for imageshack, imgur, or bayimg.

---

### Post by ankspo71 on 2010-01-25
Starks,

"For the last time...

*DO NOT POST YOUR BOOTCHARTS AS ATTACHMENTS! EVEN AFTER YOU CLICK ON THEM TWICE, THEY ARE TINY, UNREADABLE, AND WORTHLESS. USE IMAGESHACK OR IMGUR!*"

You don't have to shout. It was my first uploaded bootchart. No I did not read your first post because I was going to put this in the community cafe with the rest of the boot charts, but for the sake of lucid development I posted it here, the very first thread that mentioned bootcharts in the title. I don't know if you saw it or not, but I tried to correct the problem by uploading to photobucket, a place that until now hasn't given me trouble. 

Now on to something else. I don't see how it can say I have a boot time of 51 seconds when I have a functional desktop in a little more than half of that. What gives? Or is there another 'special requirement' that I don't know about?

---

### Post by ankspo71 on 2010-01-25
Well...
I rebooted again and now it says I have a boot time of 0:23.24 seconds. While I should be jumping up and down in excitement, I can't do anything but question the reliability of bootchart. :confused:

---

### Post by ankspo71 on 2010-01-25
Here it is.
[http://img39.imageshack.us/img39/5228/lucidlucid201001254.png](http://img39.imageshack.us/img39/5228/lucidlucid201001254.png)
I created an imageshack account just for this post.

---

### Post by farrell on 2010-01-25
> **ankspo71 said:**
> Well...
I rebooted again and now it says I have a boot time of 0:23.24 seconds. While I should be jumping up and down in excitement, I can't do anything but question the reliability of bootchart. :confused:

You do know that after certain updates, ureadahead in lucid requires one reboot to reprofile the boot and find out what files to load in advance? To clear this up, maybe you could post a link to a full-res bootchart showing your 51sec-boot. Or have a look at the manpage of ureadahead to find out if your next reboot will be profiled.

Anyway... 23sec do look really good!

> **ankspo71 said:**
> Here it is.
[http://img39.imageshack.us/img39/5228/lucidlucid201001254.png](http://img39.imageshack.us/img39/5228/lucidlucid201001254.png)
I created an imageshack account just for this post.

No need to create an account - have a look at [http://imgur.com]("http://imgur.com/") for maximum lazyness!

---

### Post by ankspo71 on 2010-01-25
Thanks, I knew ureadahead requires a system reboot to make the following reboots faster, but I didn't know that it would make that much of a difference. I also installed a few minor updates last night before installing bootchart. Maybe they had to finish installing during the reboot? I tried rebooting 2 more times, and I am staying in the 23 second range, which is better than what I was thinking (about 30 seconds).

here is the original 51 second boot chart.
[http://img686.imageshack.us/img686/3958/lucidlucid201001251orig.png](http://img686.imageshack.us/img686/3958/lucidlucid201001251orig.png)

Edit: and thanks for explaining to me about ureadahead

---

### Post by Starks on 2010-01-26
> **ankspo71 said:**
> Here it is.
[http://img39.imageshack.us/img39/5228/lucidlucid201001254.png](http://img39.imageshack.us/img39/5228/lucidlucid201001254.png)
**I created an imageshack account just for this post.**
Why? You don't need to create an imageshack account to use imageshack.

---

### Post by phenest on 2010-01-26
I've updated Jaunty to Karmic then to Lucid and my boot times have gone through the roof!
[precisionjaunty20100125.png]("http://img718.imageshack.us/img718/3000/precisionjaunty20100125.png")
[precisionlucid201001267.png]("http://img17.imageshack.us/img17/6994/precisionlucid201001267.png")

---

### Post by phillw on 2010-01-26
Yay !! - do I win ? ... 1 minute and 3 seconds :popcorn:

Bless... I guess LAMP takes a beating, along with clamav, ossec ....  

Still quicker than Vista on same laptop & that's not running WAMP !!

Phill.

---

### Post by phenest on 2010-01-26
> **phillw said:**
> Yay !! - do I win ? ... 1 minute and 3 seconds

You didn't look at mine then. 1 minute 6 seconds.

---

### Post by vade on 2010-01-26
> **phenest said:**
> You didn't look at mine then. 1 minute 6 seconds.
According to your chart the machine begins to idle at around 30 seconds. That's your actual boot time.

---

### Post by jmmL on 2010-01-26
> **phenest said:**
> You didn't look at mine then. 1 minute 6 seconds.

You've got an old version of bootchart that adds on 45 seconds to the time it takes to load the kernel, giving no indication of actual time-to-desktop. I'm not sure if a purge then reinstall of bootchart would solve this problem, but it's worth a try.

---

### Post by phenest on 2010-01-27
> **jmmL said:**
> You've got an old version of bootchart that adds on 45 seconds to the time it takes to load the kernel, giving no indication of actual time-to-desktop. I'm not sure if a purge then reinstall of bootchart would solve this problem, but it's worth a try.

I tried that. No change.

---

### Post by MacUntu on 2010-01-27
The relevant changes should be in /etc/init/bootchart.conf, so I'd remove that file, purge bootchart, and reinstall it.

---

### Post by phenest on 2010-01-27
> **MacUntu said:**
> The relevant changes should be in /etc/init/bootchart.conf, so I'd remove that file, purge bootchart, and reinstall it.

That file gets removed when I purge bootchart. This has made no difference.

---

### Post by phenest on 2010-01-27
> **jmmL said:**
> You've got an old version of bootchart

What version should I have?
bootchart: 0.90.2-5
pybootchartgui: 0+r139-2

---

### Post by Reiger on 2010-01-27
I have the same and 0:50.30 is nowhere near what I perceive as my boot times. So here's what I did: start up Dolphin ASAP via Kickoff -> Dolphin.

In order to do that, your desktop must be responsive which means that the time at which Dolphin starts up is a good replacement yardstick in your bootchart. For me, that yardstick is at around 0:27s

[http://img42.imageshack.us/img42/6161/bartixlucid201001271.png](http://img42.imageshack.us/img42/6161/bartixlucid201001271.png)

EDIT: Looking at the bootchart script the reason why we see no proper cropped chart is that we are not running Ubuntu (gnome-panel) but rather *buntu (e.g. Kubuntu, Xubuntu). 
/etc/init/bootchart*
```

# FIXME add additional processes to crop-after for Kubuntu, Xubuntu,
        # etc.
        bootchart --format=$format \
                --crop-after=gnome-panel \
                --output="/var/log/bootchart" "$TARBALL"

```

---

### Post by phillw on 2010-01-27
Curses ...

I rebooted, as ureadahead wanted another go ... Boot time 42.99 seconds - lol

So, no prize for slowest... Now, where's my Mail Server.

[http://www.phillw.net/img/piglet-lucid-20100127-1.png](http://www.phillw.net/img/piglet-lucid-20100127-1.png)

Regards,

Phill.

---

### Post by jmmL on 2010-01-27
> **phenest said:**
> What version should I have?
bootchart: 0.90.2-5
pybootchartgui: 0+r139-2

Those are the versions that I have. The only other thing I can think of is that perhaps you have an old bootchart visualisation program installed (I think it was called bootchart-java). You could check the output of ```
apt-cache policy bootchart-java
```

---

### Post by phenest on 2010-01-27
> **Reiger said:**
> EDIT: Looking at the bootchart script the reason why we see no proper cropped chart is that we are not running Ubuntu (gnome-panel) but rather *buntu (e.g. Kubuntu, Xubuntu). 
/etc/init/bootchart*
```

# FIXME add additional processes to crop-after for Kubuntu, Xubuntu,
        # etc.
        bootchart --format=$format \
                --crop-after=gnome-panel \
                --output="/var/log/bootchart" "$TARBALL"

```

I just realised that I'm using AWN without any gnome panels. I changed the bootchart.conf to show avant-window-navigator instead of gnome-panel, and now boot time is 46 seconds. Still slow though.

---

### Post by phenest on 2010-01-27
Ok. I reverted bootchart.conf back to gnome-panel. I then disabled awn and re-enabled gnome-panel for my desktop, and now my boot time is 28 seconds!

---

### Post by skymera on 2010-01-27
Restarted a few times and here's my bootchart:

16.48 seconds
[[IMG]http://img682.imageshack.us/img682/1007/scottdesktoplucid201001.th.jpg[/IMG]](http://img682.imageshack.us/i/scottdesktoplucid201001.jpg/)

Still a bit slow.

---

### Post by skymera on 2010-01-27
New chart:

14.70 seconds

[[IMG]http://img196.imageshack.us/img196/6747/scottdesktoplucid201001.th.png[/IMG]](http://img196.imageshack.us/i/scottdesktoplucid201001.png/)

---

### Post by phenest on 2010-01-27
> **skymera said:**
> New chart:

14.70 seconds

Stop showing off and tell me what's wrong with mine. It was 17 seconds under Jaunty and now over 1 minute with Lucid.

---

### Post by skymera on 2010-01-27
> **phenest said:**
> Stop showing off and tell me what's wrong with mine. It was 17 seconds under Jaunty and now over 1 minute with Lucid.

How should I know? I'm not a Guru.

I was merely posting my bootchart in the "Post your bootchart" thread.

Mine just happens to be super awesome :guitar:

---

### Post by nhasian on 2010-01-27
Hey skymera, what hard disk are you using to get such a fast boot time?

> **skymera said:**
> New chart:

14.70 seconds

[[IMG]http://img196.imageshack.us/img196/6747/scottdesktoplucid201001.th.png[/IMG]](http://img196.imageshack.us/i/scottdesktoplucid201001.png/)

---

### Post by jmmL on 2010-01-27
> **phenest said:**
> Stop showing off and tell me what's wrong with mine. It was 17 seconds under Jaunty and now over 1 minute with Lucid.

But you just said it was 28 seconds with lucid...

The 17 seconds for jaunty was almost certainly just the time to load the kernel. For comparison, jaunty took roughly 20 seconds to load the kernel on my laptop, then a further 40 seconds to load everything else to a functional desktop. Total time = 60 seconds. Lucid takes between 25 to 35 seconds depending on what I have installed, whether ureadahead is profiling or not and the phase of the moon. A huge improvement.

---

### Post by skymera on 2010-01-27
> **nhasian said:**
> Hey skymera, what hard disk are you using to get such a fast boot time?

It's a Western Digital Raptor 150GB. The old 10,000RPM drives.

I get ~80-90MB/s max data read from it.

My Windows partition is on a Samsung F2 which reads at about 104-110MB/s and is only 5,400RPM.

Technology, eh?:)

---

### Post by nhasian on 2010-01-29
Holy cow.  I've never seen or used a 10K rpm drive.  that sucker must be loud.  Makes you wonder how fast your system would boot up with one of those 128M Intel SSD drives i've been eyeing...

> **skymera said:**
> It's a Western Digital Raptor 150GB. The old 10,000RPM drives

---

### Post by Nadir on 2010-01-29
> **nhasian said:**
> Holy cow.  I've never seen or used a 10K rpm drive.  that sucker must be loud.  Makes you wonder how fast your system would boot up with one of those 128M Intel SSD drives i've been eyeing...

You should try a 15K rpm drive then: screaming hot :D

---

### Post by Reiger on 2010-01-29
I use an 80GB X25-M SSD. You can check my charts to see what that does.

---

### Post by skymera on 2010-01-30
> **nhasian said:**
> Holy cow.  I've never seen or used a 10K rpm drive.  that sucker must be loud.  Makes you wonder how fast your system would boot up with one of those 128M Intel SSD drives i've been eyeing...

Yes. It is loud. VERY loud. Especially when reading or copying lots of small files :)

I've moved my Ubuntu to a Samsung F2 drive. 5,400RPM so it's dead silent, but bootchart reports read speeds of 116MB/s and i boot in 14.1 seconds on a fresh install.

My aim is 12 seconds :)

---

### Post by phenest on 2010-01-30
I've actually had a 17.66 boot time! On that occasion I was running a gnome panel instead of gnome shell, so I least I know what I can expect.

---

### Post by hard_i on 2010-02-03
wow.. i upgraded to lucid today and got 10 sec : O

[[IMG]http://img191.imageshack.us/img191/3038/k2lucid201002034.th.png[/IMG]](http://img191.imageshack.us/i/k2lucid201002034.png/)

---

### Post by Kebabji on 2010-02-11
I'm pretty sure I screwed something up. This is me after upgrading

[[IMG]http://img683.imageshack.us/img683/945/sujukhlucid201002104.th.png[/IMG]](http://img683.imageshack.us/i/sujukhlucid201002104.png/)

---

### Post by HarshReality on 2010-02-14
I was given to believe that the boot time goal was geared using a netbook as a test bed and not a desktop at all.. if that is the case then the 10 sec goal would not apply to a desktop at all.. or am I misunderstanding

---

### Post by Merk42 on 2010-02-14
> **HarshReality said:**
> I was given to believe that the boot time goal was geared using a netbook as a test bed and not a desktop at all.. if that is the case then the 10 sec goal would not apply to a desktop at all.. or am I misunderstanding

Not just any netbook, but one with an SSD, so that'd make it 'easier' to get 10sec.

---

### Post by HarshReality on 2010-02-14
> **Merk42 said:**
> Not just any netbook, but one with an SSD, so that'd make it 'easier' to get 10sec.

Correct, the testbed I have heard is a mini 9 using its SSD drive which is what I am playing with today. So why are all these folks carrying on about desktops and trying for the 10 sec mark when it wont really apply is beyond me.

---

### Post by andrewabc on 2010-02-14
> **HarshReality said:**
> Correct, the testbed I have heard is a mini 9 using its SSD drive which is what I am playing with today. So why are all these folks carrying on about desktops and trying for the 10 sec mark when it wont really apply is beyond me.

The SSD in netbooks aren't that great. So I would think a desktop with good hard drive should get it too.

Unless throughput is the only limiting factor when it comes to boot.

I would think a quad core with good graphics card/motherboard etc, even if it only has 7200 rpm hard drive should boot similar time using same OS as netbook.

Looking at mini 9 ssd benchmarks, a new 7200 hard drive with decent dekstop config should easily boot much faster than netbook.

[http://cwhebert.files.wordpress.com/2008/10/hdtune_benchmark_stec_pata_8gb1.png](http://cwhebert.files.wordpress.com/2008/10/hdtune_benchmark_stec_pata_8gb1.png)
[http://www.activemp.com/SSD/Dell-Mini-9-PCIe-SSD-benchmarks2.htm](http://www.activemp.com/SSD/Dell-Mini-9-PCIe-SSD-benchmarks2.htm)

Those are some terrible speeds, and they are slower than my 3 year old 8mb cache 320gb hard drive.
Yes I know about better ssd access times, but I don't see how that can improve a 40mb/s read

[img]http://www.activemp.com/assets/Benchmarks/Dell-Mini-9/Atto_4G.jpg[/img]
That's a crap benchmark. If they can get 10 seconds on that SSD, good luck.

Although I think the 16gb SSD that comes with it are better
[http://www.mydellmini.com/forum/dell-mini-9-hardware-upgrades/2733-16gb-solid-state-drive-benchmarks-stec-vs-runcore.html](http://www.mydellmini.com/forum/dell-mini-9-hardware-upgrades/2733-16gb-solid-state-drive-benchmarks-stec-vs-runcore.html)
Still only a 78mb/s read. My old desktop hard drive gets 70mb/s.
My 60gb vertex gets 250mb/s, and my new 1tb is supposed to get 100mb/s

Unless most people are expecting their 5400rpm laptop hard drives to get 10 seconds...

---

### Post by kklimonda on 2010-02-14
On SSD disks, because the seek time is nonexistent you can preload data in parallel to normal boot while on "normal" disks ureadahead have to be run before all the other applications to get the most from preloading. On my laptop ureadahead have to work for 8 seconds before all files are preloaded (still I get a decent 17 to 19 seconds but nowhere close to 11 or 12 that you get on the ssd disk).

---

### Post by HarshReality on 2010-02-14
OK, so installed Lucid on the kids mini 9 (OEM).. cut off BT and a few other trivial startup applications and this is what we have.. 13.70

---

### Post by andrewabc on 2010-02-14
> **HarshReality said:**
> OK, so installed Lucid on the kids mini 9 (OEM).. cut off BT and a few other trivial startup applications and this is what we have.. 13.70

Can you host it somewhere else? The forum resizes images without warning users it has done so.

---

### Post by cariboo on 2010-02-14
> **andrewabc said:**
> Can you host it somewhere else? The forum resizes images without warning users it has done so.

If you check the Manage Attachments dialog box, it tells you the max jpg/png size is 1024x768.

---

### Post by HarshReality on 2010-02-14
> **andrewabc said:**
> Can you host it somewhere else? The forum resizes images without warning users it has done so.

Lets try...
[IMG]http://only-harshreality.com/deborah-laptop-lucid-20100214-5.png[/IMG]

---

### Post by HarshReality on 2010-02-15
OK, round 2...
Sony Vaio VGN-325J installed Lucid Alpha2 and updated to current as of 9am.
Only thing that hasnt worked with this is the multimedia keys (A/V Mode).
Turned off BT, Driver and Update Notification & Accessibility

*drumroll*

[IMG]http://only-harshreality.com/vaio-laptop-lucid-20100215-3.png[/IMG]

---

### Post by farrell on 2010-02-15
> **HarshReality said:**
> OK, round 2...
Sony Vaio VGN-325J installed Lucid Alpha2 and updated to current as of 9am.
Only thing that hasnt worked with this is the multimedia keys (A/V Mode).
Turned off BT, Driver and Update Notification & Accessibility

*drumroll*


Only 4 seconds of full CPU usage on 2GHz is really impressive!

Now, can you resist buying an SSD, knowing that your HDD causes around 70% of your boot time? (given you don't need that much storage...)

---

### Post by HarshReality on 2010-02-15
You have no idea.. however the expense I simply cannot justify.

---

### Post by DanaG on 2010-02-16
Unfortunately, Lucid presents a regression compared to, say, Jaunty... at least then, readahead worked.  Now all I get is ureadahead terminating with status 4.

It takes my system 5 seconds to start GDM... and then at least 30-45 seconds to finally show my desktop and gnome panel.

I've posted a bunch of my bootcharts here: [http://users.csc.calpoly.edu/~dgoyette/bootcharts/](http://users.csc.calpoly.edu/~dgoyette/bootcharts/)  -- note that the EliteBook is the most modern system I have.

Be aware that those bootcharts are freakishly huge.... Firefox chokes on them, so try Chromium or such, instead.

---

### Post by HarshReality on 2010-02-16
Not that this has anything to do with topic but Im curious on if you have a clean install or perhaps a botched update somewhere. I initially did an update/grade on the Vaio which went wrong under the cover however a clean redo did the trick. Of course as my home partition is seperate it wasnt that big of a deal where a person who has a single partition this wouldnt be the case.

---

### Post by ranch hand on 2010-02-16
Bootchart really grinds me.  I am having the "plymouth" problem on all my installs.  Except one.

That is my oldest, a 9.10 upgraded to the toolchain on 11-04-09.  Boots every time with plymouth.

Bootchart on the other hand rarely works on this install and this install alone.

I think the boot time is pretty good concidering that it is booting from an external enclosure (USB not eSATA) and password.  Can't prove it though.  Bummer.

---

### Post by donniezazen on 2010-02-17
My boot time is over a minute. Please help me to reduce it.

thanks

---

### Post by andrewabc on 2010-02-17
> **soham_1207 said:**
> My boot time is over a minute. Please help me to reduce it.

thanks

You have to host images somewhere else. they shrink at this forum.

Stil waiting for forum software to do a better job at warning people about squished images (if it is over a certain height which most bootcharts use reject upload altogether?).

---

### Post by Amaranth on 2010-02-18
Removed plymouth and hacked compiz up a bit but this is still not all that good considering my HD throughput. :neutral:

[http://i.imgur.com/tgbPF.png](http://i.imgur.com/tgbPF.png)

Probably due to fragmentation. Come on ext4 defrag!

---

### Post by MacUntu on 2010-02-18
AFAIK most of the boot files are too small to fragment, so the bad throughput is more likely caused by disk seeks. Having a way of putting the boot files closer together on-disk would be great.

[I did that by creating a partition large enough to hold the boot files on a second disk, copying over the boot files, enlarging the partition, and copying over the rest of the system - that halved the ureadahead time and the disk throughput looked a lot better.]

---

### Post by Amaranth on 2010-02-18
Right, I guess I didn't mean actual fragmentation but seeks, like you say. Once ext4 supports defrag though one should easily be able to write a tool to pack the boot files together again.

---

### Post by MacUntu on 2010-02-18
Yes, according to Akira Fujita it definitely should be possible once ext4 defrag works (guess I'll have a SSD before that happens :P).

---

### Post by emarkay on 2010-02-18
Here it is from today.
[B]
[COLOR=Purple] 2.8 G/1G RAM/ATI HD2600,512 VRAM/SIS AC97 OB  Audio[/COLOR][/B]

---

### Post by andrewabc on 2010-02-18
> **emarkay said:**
> Here it is from today.
[B]
[COLOR=Purple] 2.8 G/1G RAM/ATI HD2600,512 VRAM/SIS AC97 OB  Audio[/COLOR][/B]

Seriously mods do something about uploading bootcharts that just get squished. Waste of forum resources and peoples time uploading images that become unreadable. Bring it up at a meeting or something please.

---

### Post by cariboo on 2010-02-18
@andrewabc

As a moderator, there is nothing I can do about the picture upload size limit. it was set at 1024X768, because members were abusing the previous limit which was by file size.

If you would like to ask one of the admins to change the size limit, start a thread in [FF&H]("http://ubuntuforums.org/forumdisplay.php?f=48"), instead of complaining in a thread in a sub-forum that few of the admins ever look at.

---

### Post by donniezazen on 2010-02-18
This thread is so long. Have people suggested any way to reduce the boot time. I have a boot time of over a min. I have a Dell E1505/6400.

Thanks.

---

### Post by andrewabc on 2010-02-18
> **soham_1207 said:**
> This thread is so long. Have people suggested any way to reduce the boot time. I have a boot time of over a min. I have a Dell E1505/6400.

Thanks.


Looking at yours it looks like you have the 9.10 bootchart style where it adds +45 seconds.

Notice how docky/nautlius and other programs are shown in the chart near end.

Did you upgrade from 9.10?

---

### Post by donniezazen on 2010-02-18
> **andrewabc said:**
> Looking at yours it looks like you have the 9.10 bootchart style where it adds +45 seconds.

Notice how docky/nautlius and other programs are shown in the chart near end.

Did you upgrade from 9.10?

No its a clean install.

---

### Post by emarkay on 2010-02-18
> **cariboo907 said:**
> @andrewabc
As a moderator, there is nothing I can do about the picture upload size limit. it was set at 1024X768, because members were abusing the previous limit which was by file size.
If you would like to ask one of the admins to change the size limit, start a thread in [FF&H]("http://ubuntuforums.org/forumdisplay.php?f=48"), instead of complaining in a thread in a sub-forum that few of the admins ever look at.

Done:
[http://ubuntuforums.org/showthread.php?p=8848532#post8848532](http://ubuntuforums.org/showthread.php?p=8848532#post8848532)

---

### Post by andrewabc on 2010-02-18
> **soham_1207 said:**
> No its a clean install.

Ok, well you can disable the +45 seconds in a config file (forget where exactly). Or just subtract 45 seconds when comparing times with other people.

see here:
[Post your Karmic bootcharts or boot times!](http://ubuntuforums.org/showthread.php?t=1229111&page=11)

I have no idea what they are doing with Lucid. I thought they had disabled the +45 second delay.

Also wtf did cariboo907 modify your post and attach as forum image? Now it is useless image! wtf? A link to the oversized image would have worked better. This is exactly what I've been complaining about.

---

### Post by ranch hand on 2010-02-19
I was looking around in my oldest and best behaved install of 10.04 (Lounge Lizard) and discovered that I actually had a bootchart image from 2-13-10.

I only get one by accident at times.  The bugger just doesn't work right on that install.  I have "dpkg-reconfigure"d the bugger.  I have reinstalled the thing.  I have purged and reinstalled it.  Just does not work reliably.  Works in the rest of them.

They do not boot right because of the "plymouth problem".  Why this one does is kind of bugging me.

However, it does and here is what it does running on WD 320Gb 7200rpm external enclosure HDDs (root on one - home on the other).

EDIT

This is without auto login.  I do have to enter the password.

---

### Post by Starks on 2010-03-04
bump

---

### Post by farrell on 2010-03-04
recent updates (mostly between alpha 2 and today) reduced my boot time by another 2 seconds (22% sounds better), and i'm now at 7.3 seconds with intel's x25-m.

xorg could start faster (i'm using intel's gma 4500mhd).

[http://i.imgur.com/ciYnp.png](http://i.imgur.com/ciYnp.png)

---

### Post by mojo2012 on 2010-03-05
Today I installed Lucid Lynx Alpha 3 and I have to admit, that I'm really impressed. After I updated the whole system to the latest packages, the system only needs 19 secs to get from grub to desktop (auto-logon).
I think that the "original" alpha 3 booted even quicker - though I didn't measure that. Maybe bootchart itself increased the boot time by a few secs?

Btw, Karmic needs about 40 secs to get to the logon window ...

Here is my bootchart:
[http://img38.imageshack.us/img38/5865/odinlucid201003053.png](http://img38.imageshack.us/img38/5865/odinlucid201003053.png)

System:
AMD 3500+ (single core)
1GB RAM
1TB Sata drive
Radeon X800 PCI-E

---

### Post by amano on 2010-03-05
Yes, bootchart itself delays the boot a bit.

---

### Post by mojo2012 on 2010-03-05
Though I uninstalled bootchart (to get back a few secs of boottime ;-)), there is still a command line output telling me something about bootchart being terminated. Can I somehow get rid of this message?

---

### Post by ranch hand on 2010-03-05
Try;
```

sudo apt-get purge bootchart

```

---

### Post by ViperScull on 2010-03-05
A bit disappointed with the boot time once all the posts are read.
Maybe it is because of my HDD, which is 5900 RPM (Seagate 5900.12), although read speed is about 100 MB/sec

The rest of the Pc is:
Athlon II X4 620 @ 3Ghz
4GB DDR3 @ 1460Mhz

Is hald needed? Any tip to improve it? I've gotten rid of many services i don't need, but a lot of them i don't know what they are for.

[[IMG]http://img42.imageshack.us/img42/5916/barydesktoplucid2010030.png[/IMG]](http://img42.imageshack.us/i/barydesktoplucid2010030.png/)

---

### Post by darundal on 2010-03-05
Here is my chart

[img]http://xs.to/image-E7ED_4B925CFD.jpg[/img]

Just a note, the chart lies. It says the boot time is a bit over 7 minutes, but it is actually over 20 (from grub to the boot screen disappearing). I have a forum post, which sadly isn't getting much attention, [here]("http://ubuntuforums.org/showthread.php?t=1421307"). No, the iPod is not usually connected. If anyone has any ideas about how to solve this, please post there. Thank you.

---

### Post by andrewabc on 2010-03-05
> **ViperScull said:**
> A bit disappointed with the boot time once all the posts are read.
Maybe it is because of my HDD, which is 5900 RPM (Seagate 5900.12), although read speed is about 100 MB/sec

The rest of the Pc is:
Athlon II X4 620 @ 3Ghz
4GB DDR3 @ 1460Mhz

Is hald needed? Any tip to improve it? I've gotten rid of many services i don't need, but a lot of them i don't know what they are for.


Only way to really make it any faster is with SSD. I'd be happy with 22 seconds.

---

### Post by Starks on 2010-03-05
For me, Plymouth, installed or purge, seems to leave me with crappy boot times and error messages. Plus, autologin doesn't work properly anymore.

---

### Post by ViperScull on 2010-03-06
> **Starks said:**
> For me, Plymouth, installed or purge, seems to leave me with crappy boot times and error messages. Plus, autologin doesn't work properly anymore.

For me, autologin sometimes works sometimes doesn't.

Sometimes i have to press enter on a black screen, then gdm appears and i have to login normal way. Sometimes works just fine.

What i can't do is to suspend. It goes directly to resume screen where i have to type my pass, but when i do it, systems freezes and i have to reset it.

[QUOTE="andrewabc"]Only way to really make it any faster is with SSD[/QUOTE]
I know, and i considered about getting one. But it's still very expensive, and TRIM support in 2.6.33 isn't as mature as i'd like.

---

### Post by Jay_Bee on 2010-03-06
> **darundal said:**
> Here is my chart
Just a note, the chart lies. It says the boot time is a bit over 7 minutes, but it is actually over 20 (from grub to the boot screen disappearing). I have a forum post, which sadly isn't getting much attention, [here]("http://ubuntuforums.org/showthread.php?t=1421307"). No, the iPod is not usually connected. If anyone has any ideas about how to solve this, please post there. Thank you.
Did you file a bug about this? Somethings seriously wrong.
Did older versions of Ubuntu boot fine? Could it be a hardware error?

---

### Post by andrewabc on 2010-03-06
> **ViperScull said:**
> 
I know, and i considered about getting one. But it's still very expensive, and TRIM support in 2.6.33 isn't as mature as i'd like.

Yep, from linux standpoint, best time to get one would be this upcoming fall as ubuntu 10.10 should better support SSD (especially if the use newest kernel and not just .33), and prices should fall by then, along with much better firmware.
ocz firmware has garbage collection so even if OS doesn't support TRIM garbage collections still keeps SSD maintain fast speed. although I havn't even upgraded my firmware as my computer doesn't support IDE mode which is needed to upgrade firmware. :P

---

### Post by Herman on 2010-03-09
[IMG]http://members.iinet.net/%7Eherman546/p1/ocz-lynx-lucid-20100310-2.png[/IMG]I have my OZC Vertex TRIMMED with DiskTRIM and wiper.sh,  see the following thread if you're interested,                           [ext4 without journaling]("http://ubuntuforums.org/showthread.php?t=1404664"). :D


EDITED: I have now removed this chart again because it has now been superceded with two better ones. 
The first chart I posted showed a boot time of 6.09, but that was replaced with one showing 5.35 seconds.
Further along in this thread it booted in 4.46   			#[**204**]("http://ubuntuforums.org/showpost.php?p=8963358&postcount=204"),  and now  4.27 seconds,   			#[**226**]("http://ubuntuforums.org/showpost.php?p=8994639&postcount=226").


[IMG]http://members.iinet.net/%7Eherman546/p1/ocz-lynx-lucid-20100309-1.png[/IMG]

---

### Post by andrewabc on 2010-03-09
> **Herman said:**
> I have my OZC Vertex TRIMMED with DiskTRIM and wiper.sh,  see the following thread if you're interested,  			 			[ext4 without journaling]("http://ubuntuforums.org/showthread.php?t=1404664"). :D


[IMG]http://members.iinet.net/%7Eherman546/p1/ocz-lynx-lucid-20100309-1.png[/IMG]

thanks for the info.
I don't see you're bootchart though. You link to the thread, and in other thread you link back to this thread to see the bootchart.

---

### Post by ranch hand on 2010-03-09
> **andrewabc said:**
> thanks for the info.
I don't see you're bootchart though. You link to the thread, and in other thread you link back to this thread to see the bootchart.
This is strange, the chart was here last night.  About 9 seconds if I remember right.  I was going to look at it in more detail today and it has up and left.

---

### Post by darundal on 2010-03-09
> **Jay_Bee said:**
> Did you file a bug about this? Somethings seriously wrong.
Did older versions of Ubuntu boot fine? Could it be a hardware error?

Every other version of Ubuntu worked fine. I doubt it is a hardware error, as Karmic worked just fine on that drive before I upgraded (and it was a straight up upgrade install from a perfectly working Karmic install). Actually, just did a fresh reinstall, and while it still has the same issue, the boot time is not nearly as long, although it is still unreasonably long and still causes the hard-drive clicking. I am going to get a chart of my new install up soon. Oh, and insofar as a bug report, no, I haven't, because I am not exactly sure what to put in it.

Edit: Here is a chart from my current install, yet again the chart lies, I timed it during boot (from grub to GDM) and it was 7 minutes and 52 seconds

---

### Post by Herman on 2010-03-09
Sorry about the technical hiccup, it's back, 6.09 seconds.

My bad. 
 I thought that once it uploaded to Ubuntu web forums server it would stay there and I could remove it from my web location and have a good night's sleep. (LOL). But apparently I need to leave it in place, Ubuntu's server only reads the URL I guess. Sorry, my mistake, now I know. :oops:

I have a better one this morning anyway, 5.35 seconds, so I have changed to the newer image file.

---

### Post by ranch hand on 2010-03-12
I just got curious and installed bootchart on my 9.04 install that I use as my main OS during the night.  This is the same respin as I use, upgraded 9.10>10.04, as my main OS in the day time.

The jak-desktop is 9.04 and the sam-desktop is 10.04.  This was the last boot of the day for 10.04 and it has not had the newest update of plymouth.

---

### Post by andrewabc on 2010-03-13
> **ranch hand said:**
> I just got curious and installed bootchart on my 9.04 install that I use as my main OS during the night.  This is the same respin as I use, upgraded 9.10>10.04, as my main OS in the day time.

The jak-desktop is 9.04 and the sam-desktop is 10.04.  This was the last boot of the day for 10.04 and it has not had the newest update of plymouth.

Looks like 9.04 is accurate, and 10.04 adds 45 second delay. Unless for some reason you boot time takes a lot longer now.

---

### Post by tekstr1der on 2010-03-13
> **andrewabc said:**
> Looks like 9.04 is accurate, and 10.04 adds 45 second delay. Unless for some reason you boot time takes a lot longer now.

Actually, it's the other way around. The old version (available for 9.04) of bootchart only measured the time to boot to GDM. Now, in 10.4, bootchart accurately measures the full bootup process from start to loaded desktop.

---

### Post by grandtoubab on 2010-03-13
21 secondes:popcorn:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.33-999-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #201003051003 SMP Fri Mar 5 11:02:11 UTC 2010
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017fd0000 (usable)
[    0.000000]  BIOS-e820: 0000000017fd0000 - 0000000017fdf000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017fdf000 - 0000000018000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x17fd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF8000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000017fd0000 (usable)
[    0.000000]  modified: 0000000017fd0000 - 0000000017fdf000 (ACPI data)
[    0.000000]  modified: 0000000017fdf000 - 0000000018000000 (ACPI NVS)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000017fd0000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0017c00000 page 2M
[    0.000000]  0017c00000 - 0017fd0000 page 4k
[    0.000000] kernel direct mapping tables up to 17fd0000 @ 15000-1a000
[    0.000000] RAMDISK: 1786f000 - 17fbfb68
[    0.000000] ACPI: RSDP 000f8500 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 17fd0000 00038 (v01 A M I  OEMRSDT  06000602 MSFT 00000097)
[    0.000000] ACPI: FACP 17fd0200 00081 (v01 A M I  OEMFACP  06000602 MSFT 00000097)
[    0.000000] ACPI: DSDT 17fd0400 04D48 (v01  410M1 410M1602 00000602 INTL 02002026)
[    0.000000] ACPI: FACS 17fdf000 00040
[    0.000000] ACPI: APIC 17fd0390 0006C (v01 A M I  OEMAPIC  06000602 MSFT 00000097)
[    0.000000] ACPI: SSDT 17fd5150 0007B (v01 OEM_ID OEMTBLID 00000001 INTL 02002026)
[    0.000000] ACPI: OEMB 17fdf040 00040 (v01 A M I  AMI_OEM  06000602 MSFT 00000097)
[    0.000000] ACPI: MCFG 17fd51d0 0003C (v01 A M I  OEMMCFG  06000602 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 383MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 17fd0000
[    0.000000]   low ram: 0 - 17fd0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00017fd0
[    0.000000]   HighMem  0x00017fd0 -> 0x00017fd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00017fd0
[    0.000000] On node 0 totalpages: 98143
[    0.000000] free_area_init_node: node 0, pgdat c07d0e00, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 736 pages used for memmap
[    0.000000]   Normal zone: 93424 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 18000000 (gap: 18000000:e6e00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1400000 s37268 r0 d24172 u1048576
[    0.000000] pcpu-alloc: s37268 r0 d24172 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 97375
[    0.000000] Kernel command line: root=UUID=ae02ece1-192f-4996-8067-144aaa760f93 ro quiet splash 
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1964800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (42 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 0000909afc]   TEXT DATA BSS
[    0.000000]   #3 [001786f000 - 0017fbfb68]         RAMDISK
[    0.000000]   #4 [000009fc00 - 0000100000]   BIOS reserved
[    0.000000]   #5 [000090a000 - 000090d189]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 0001301000]         BOOTMEM
[    0.000000]   #11 [0001301000 - 0001301004]         BOOTMEM
[    0.000000]   #12 [0001301040 - 0001301100]         BOOTMEM
[    0.000000]   #13 [0001301100 - 0001301124]         BOOTMEM
[    0.000000]   #14 [0001301140 - 0001302940]         BOOTMEM
[    0.000000]   #15 [0001302940 - 0001302967]         BOOTMEM
[    0.000000]   #16 [0001302980 - 0001302a7c]         BOOTMEM
[    0.000000]   #17 [0001302a80 - 0001302ac0]         BOOTMEM
[    0.000000]   #18 [0001302ac0 - 0001302b00]         BOOTMEM
[    0.000000]   #19 [0001302b00 - 0001302b40]         BOOTMEM
[    0.000000]   #20 [0001302b40 - 0001302b80]         BOOTMEM
[    0.000000]   #21 [0001302b80 - 0001302bc0]         BOOTMEM
[    0.000000]   #22 [0001302bc0 - 0001302c00]         BOOTMEM
[    0.000000]   #23 [0001302c00 - 0001302c40]         BOOTMEM
[    0.000000]   #24 [0001302c40 - 0001302c80]         BOOTMEM
[    0.000000]   #25 [0001302c80 - 0001302c90]         BOOTMEM
[    0.000000]   #26 [0001302cc0 - 0001302d00]         BOOTMEM
[    0.000000]   #27 [0001302d00 - 0001302d40]         BOOTMEM
[    0.000000]   #28 [0001400000 - 000140f000]         BOOTMEM
[    0.000000]   #29 [0001500000 - 000150f000]         BOOTMEM
[    0.000000]   #30 [0001600000 - 000160f000]         BOOTMEM
[    0.000000]   #31 [0001700000 - 000170f000]         BOOTMEM
[    0.000000]   #32 [0001304d40 - 0001304d44]         BOOTMEM
[    0.000000]   #33 [0001304d80 - 0001304d84]         BOOTMEM
[    0.000000]   #34 [0001304dc0 - 0001304dd0]         BOOTMEM
[    0.000000]   #35 [0001304e00 - 0001304e10]         BOOTMEM
[    0.000000]   #36 [0001304e40 - 0001304ee0]         BOOTMEM
[    0.000000]   #37 [0001304f00 - 0001304f48]         BOOTMEM
[    0.000000]   #38 [0001302d40 - 0001304d40]         BOOTMEM
[    0.000000]   #39 [0001304f80 - 0001344f80]         BOOTMEM
[    0.000000]   #40 [0001344f80 - 0001364f80]         BOOTMEM
[    0.000000]   #41 [000170f000 - 00018eeb00]         BOOTMEM
[    0.000000]  16 20 - 80 9f
[    0.000000]  90e 920 - 1000 1000
[    0.000000]  1365 1380 - 1400 1400
[    0.000000]  140f 1420 - 1500 1500
[    0.000000]  150f 1520 - 1600 1600
[    0.000000]  160f 1620 - 1700 1700
[    0.000000]  18ef 1900 - 17860 1786f
[    0.000000]  17fc0 - 17fd0
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 371172k/393024k available (4705k kernel code, 21400k reserved, 2315k data, 612k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd87d0000 - 0xff7fe000   ( 624 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xd7fd0000   ( 383 MB)
[    0.000000]       .init : 0xc07dc000 - 0xc0875000   ( 612 kB)
[    0.000000]       .data : 0xc0598620 - 0xc07db228   (2315 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0598620   (4705 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using PMTIMER reference calibration
[    0.000000] Detected 3058.464 MHz processor.
[    0.016007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6116.92 BogoMIPS (lpj=12233856)
[    0.016028] Security Framework initialized
[    0.016035] SELinux:  Disabled at boot.
[    0.016048] Mount-cache hash table entries: 512
[    0.016232] Initializing cgroup subsys ns
[    0.016238] Initializing cgroup subsys cpuacct
[    0.016245] Initializing cgroup subsys memory
[    0.016257] Initializing cgroup subsys devices
[    0.016260] Initializing cgroup subsys freezer
[    0.016263] Initializing cgroup subsys net_cls
[    0.016298] CPU: Physical Processor ID: 0
[    0.016301] CPU: Processor Core ID: 0
[    0.016306] mce: CPU supports 4 MCE banks
[    0.016320] CPU0: Thermal monitoring enabled (TM2)
[    0.016326] using mwait in idle threads.
[    0.016335] Performance Events: no PMU driver, software events only.
[    0.016343] Checking 'hlt' instruction... OK.
[    0.036287] ACPI: Core revision 20100121
[    0.050324] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.051212] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.091846] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
[    0.092000] Booting Node   0, Processors  #1
[    0.020000] Initializing CPU#1
[    0.180000] TSC synchronization [CPU#0 -> CPU#1]:
[    0.180000] Measured 1034804293 cycles TSC warp between CPUs, turning off TSC clock.
[    0.180000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.180032] Brought up 2 CPUs
[    0.180038] Total of 2 processors activated (12235.40 BogoMIPS).
[    0.181271] regulator: core version 0.5
[    0.181311] Time:  7:15:20  Date: 03/13/10
[    0.181366] NET: Registered protocol family 16
[    0.181530] EISA bus registered
[    0.181543] ACPI: bus type pci registered
[    0.181655] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.181660] PCI: not using MMCONFIG
[    0.181755] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.181758] PCI: Using configuration type 1 for base access
[    0.183186] bio: create slab <bio-0> at 0
[    0.185120] ACPI: EC: Look up EC in DSDT
[    0.189624] ACPI: Executed 1 blocks of module-level executable AML code
[    0.204648] ACPI: Interpreter enabled
[    0.204657] ACPI: (supports S0 S3 S4 S5)
[    0.204690] ACPI: Using IOAPIC for interrupt routing
[    0.205334] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.211215] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.211220] PCI: Using MMCONFIG for extended config space
[    0.230790] ACPI Warning: Incorrect checksum in table [OEMB] - 20, should be 11 (20100121/tbutils-314)
[    0.230986] ACPI: No dock devices found.
[    0.230992] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.231164] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.231496] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.231501] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.231505] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.231508] pci_root PNP0A03:00: host bridge window [mem 0x18000000-0xffffffff] (ignored)
[    0.231554] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.231801] pci 0000:00:1c.0: reg 10: [mem 0xff6ff000-0xff6fffff]
[    0.231892] pci 0000:00:1c.1: reg 10: [mem 0xff6fe000-0xff6fefff]
[    0.231983] pci 0000:00:1c.2: reg 10: [mem 0xff6fd000-0xff6fdfff]
[    0.232108] pci 0000:00:1c.3: reg 10: [mem 0xff6fcc00-0xff6fccff]
[    0.232195] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.232203] pci 0000:00:1c.3: PME# disabled
[    0.232275] pci 0000:00:1d.0: reg 10: [mem 0xff6f8000-0xff6fbfff 64bit]
[    0.232346] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.232354] pci 0000:00:1d.0: PME# disabled
[    0.232556] pci 0000:00:1e.1: quirk: [io  0x4000-0x403f] claimed by ali7101 ACPI
[    0.232657] pci 0000:00:1f.0: reg 20: [io  0xff00-0xff0f]
[    0.232754] pci 0000:00:1f.1: reg 10: [io  0xec00-0xec0f]
[    0.232765] pci 0000:00:1f.1: reg 14: [io  0xe800-0xe807]
[    0.232776] pci 0000:00:1f.1: reg 18: [io  0xe400-0xe40f]
[    0.232788] pci 0000:00:1f.1: reg 1c: [io  0xe000-0xe007]
[    0.232798] pci 0000:00:1f.1: reg 20: [io  0xdc00-0xdc1f]
[    0.232809] pci 0000:00:1f.1: reg 24: [mem 0xff6fc800-0xff6fcbff]
[    0.232849] pci 0000:00:1f.1: PME# supported from D3hot
[    0.232856] pci 0000:00:1f.1: PME# disabled
[    0.232939] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.232946] pci 0000:01:05.0: reg 14: [io  0xb800-0xb8ff]
[    0.232953] pci 0000:01:05.0: reg 18: [mem 0xff4f0000-0xff4fffff]
[    0.232972] pci 0000:01:05.0: reg 30: [mem 0xff4c0000-0xff4dffff pref]
[    0.232994] pci 0000:01:05.0: supports D1 D2
[    0.233032] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.233039] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.233045] pci 0000:00:01.0:   bridge window [mem 0xff400000-0xff4fffff]
[    0.233050] pci 0000:00:01.0:   bridge window [mem 0xbff00000-0xdfefffff pref]
[    0.233196] pci 0000:02:15.0: reg 10: [mem 0xff5fc000-0xff5fffff]
[    0.233209] pci 0000:02:15.0: reg 14: [io  0xc800-0xc8ff]
[    0.233258] pci 0000:02:15.0: reg 30: [mem 0xff5c0000-0xff5dffff pref]
[    0.233304] pci 0000:02:15.0: supports D1 D2
[    0.233308] pci 0000:02:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233315] pci 0000:02:15.0: PME# disabled
[    0.233376] pci 0000:02:16.0: reg 10: [mem 0xff5fb800-0xff5fbfff]
[    0.233389] pci 0000:02:16.0: reg 14: [io  0xcc00-0xcc7f]
[    0.233473] pci 0000:02:16.0: supports D2
[    0.233477] pci 0000:02:16.0: PME# supported from D2 D3hot D3cold
[    0.233485] pci 0000:02:16.0: PME# disabled
[    0.233519] pci 0000:00:19.0: PCI bridge to [bus 02-02]
[    0.233526] pci 0000:00:19.0:   bridge window [io  0xc000-0xcfff]
[    0.233533] pci 0000:00:19.0:   bridge window [mem 0xff500000-0xff5fffff]
[    0.233540] pci 0000:00:19.0:   bridge window [mem 0xfff00000 - 000fffff pref] reg reading
[    0.233557] pci_bus 0000:00: on NUMA node 0
[    0.233563] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.233691] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.233803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE2P._PRT]
[    0.247012] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15), disabled.
[    0.247293] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.247566] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.247839] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.248134] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.248410] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.248683] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.248957] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.249232] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.249371] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.249378] vgaarb: loaded
[    0.249559] SCSI subsystem initialized
[    0.249585] libata version 3.00 loaded.
[    0.249585] usbcore: registered new interface driver usbfs
[    0.249585] usbcore: registered new interface driver hub
[    0.249585] usbcore: registered new device driver usb
[    0.249585] ACPI: WMI: Mapper loaded
[    0.249585] PCI: Using ACPI for IRQ routing
[    0.249585] PCI: pci_cache_line_size set to 64 bytes
[    0.249585] pci 0000:00:00.0: address space collision: [mem 0xe0000000-0xffffffff 64bit] already in use
[    0.249585] pci 0000:00:00.0: can't reserve [mem 0xe0000000-0xffffffff 64bit]
[    0.249585] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.249585] reserve RAM buffer: 0000000017fd0000 - 0000000017ffffff 
[    0.249585] Bluetooth: Core ver 2.15
[    0.249585] NET: Registered protocol family 31
[    0.249585] Bluetooth: HCI device and connection manager initialized
[    0.249585] Bluetooth: HCI socket layer initialized
[    0.249585] NetLabel: Initializing
[    0.249585] NetLabel:  domain hash size = 128
[    0.249585] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.249585] NetLabel:  unlabeled traffic allowed by default
[    0.249585] Switching to clocksource jiffies
[    0.254350] pnp: PnP ACPI init
[    0.254369] ACPI: bus type pnp registered
[    0.267199] pnp 00:0f: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.267205] pnp 00:0f: disabling [mem 0x000c0000-0x000dffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.267210] pnp 00:0f: disabling [mem 0x000e0000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.267215] pnp 00:0f: disabling [mem 0x00100000-0x17ffffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.267798] pnp: PnP ACPI: found 16 devices
[    0.267802] ACPI: ACPI bus type pnp unregistered
[    0.267808] PnPBIOS: Disabled by ACPI PNP
[    0.267831] system 00:0b: [io  0x0a00-0x0a0f] has been reserved
[    0.267835] system 00:0b: [io  0x0a10-0x0a1f] has been reserved
[    0.267839] system 00:0b: [io  0x0a20-0x0a2f] has been reserved
[    0.267842] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
[    0.267851] system 00:0c: [io  0x028d-0x028e] has been reserved
[    0.267855] system 00:0c: [io  0x0480-0x048f] has been reserved
[    0.267858] system 00:0c: [io  0x04d0-0x04d1] has been reserved
[    0.267863] system 00:0c: [mem 0xff380000-0xff3fffff] has been reserved
[    0.267867] system 00:0c: [mem 0xfff80000-0xffffffff] has been reserved
[    0.267871] system 00:0c: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.267875] system 00:0c: [mem 0xfeb00000-0xfeb00fff] has been reserved
[    0.267879] system 00:0c: [mem 0xff780000-0xff7fffff] has been reserved
[    0.267887] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.267891] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.267898] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.302785] Switching to clocksource acpi_pm
[    0.302816] PCI: max bus depth: 1 pci_try_num: 2
[    0.302816] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.302816] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.302816] pci 0000:00:01.0:   bridge window [mem 0xff400000-0xff4fffff]
[    0.302816] pci 0000:00:01.0:   bridge window [mem 0xbff00000-0xdfefffff pref]
[    0.302816] pci 0000:00:19.0: PCI bridge to [bus 02-02]
[    0.302816] pci 0000:00:19.0:   bridge window [io  0xc000-0xcfff]
[    0.302816] pci 0000:00:19.0:   bridge window [mem 0xff500000-0xff5fffff]
[    0.302816] pci 0000:00:19.0:   bridge window [mem pref disabled]
[    0.302816] pci 0000:00:19.0: setting latency timer to 64
[    0.302816] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.302816] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.302816] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.302816] pci_bus 0000:01: resource 1 [mem 0xff400000-0xff4fffff]
[    0.302816] pci_bus 0000:01: resource 2 [mem 0xbff00000-0xdfefffff pref]
[    0.302816] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.302816] pci_bus 0000:02: resource 1 [mem 0xff500000-0xff5fffff]
[    0.302816] NET: Registered protocol family 2
[    0.302816] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.302816] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.302816] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.302816] TCP: Hash tables configured (established 16384 bind 16384)
[    0.302816] TCP reno registered
[    0.302816] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.302816] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.302816] NET: Registered protocol family 1
[    0.302816] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.302816] pci 0000:00:19.0: Disabling HT MSI Mapping
[    0.772608] PCI: CLS mismatch (64 != 512), using 64 bytes
[    0.772615] pci 0000:01:05.0: Boot video device
[    0.772708] Trying to unpack rootfs image as initramfs...
[    1.041721] Freeing initrd memory: 7490k freed
[    1.051233] cpufreq-nforce2: No nForce2 chipset.
[    1.051275] Scanning for low memory corruption every 60 seconds
[    1.051459] audit: initializing netlink socket (disabled)
[    1.051489] type=2000 audit(1268464521.048:1): initialized
[    1.072865] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.074766] VFS: Disk quotas dquot_6.5.2
[    1.074842] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.075662] fuse init (API version 7.13)
[    1.075772] msgmni has been set to 739
[    1.076140] alg: No test for stdrng (krng)
[    1.076159] io scheduler noop registered
[    1.076162] io scheduler deadline registered
[    1.076222] io scheduler cfq registered (default)
[    1.076363] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.076397] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.076658] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.076664] ACPI: Power Button [PWRB]
[    1.076730] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.076733] ACPI: Power Button [PWRF]
[    1.086972] isapnp: Scanning for PnP cards...
[    1.442161] isapnp: No Plug & Play device found
[    1.443711] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.443877] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.444036] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.444488] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.444714] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.446281] brd: module loaded
[    1.446967] loop: module loaded
[    1.447335] sata_uli 0000:00:1f.1: version 1.3
[    1.447363]   alloc irq_desc for 21 on node -1
[    1.447367]   alloc kstat_irqs on node -1
[    1.447379] sata_uli 0000:00:1f.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.447643] scsi0 : sata_uli
[    1.447779] scsi1 : sata_uli
[    1.447871] scsi2 : sata_uli
[    1.447961] scsi3 : sata_uli
[    1.448037] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 21
[    1.448044] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 21
[    1.448050] ata3: SATA max UDMA/133 cmd 0xec08 ctl 0xe806 bmdma 0xdc10 cmd 0xe409 ctl 0xe006 bmdma 0xdc18 irq 21
[    1.448055] ata4: SATA max UDMA/133 irq 21
[    1.448189] pata_ali 0000:00:1f.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.448400] scsi4 : pata_ali
[    1.448523] scsi5 : pata_ali
[    1.451399] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.451404] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.452578] Fixed MDIO Bus: probed
[    1.452636] PPP generic driver version 2.4.2
[    1.452781] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.452811]   alloc irq_desc for 23 on node -1
[    1.452814]   alloc kstat_irqs on node -1
[    1.452823] ehci_hcd 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.452850] ehci_hcd 0000:00:1c.3: EHCI Host Controller
[    1.452892] ehci_hcd 0000:00:1c.3: new USB bus registered, assigned bus number 1
[    1.452941] ehci_hcd 0000:00:1c.3: debug port 1
[    1.476069] ehci_hcd 0000:00:1c.3: irq 23, io mem 0xff6fcc00
[    1.488034] ehci_hcd 0000:00:1c.3: USB 2.0 started, EHCI 1.00
[    1.488173] hub 1-0:1.0: USB hub found
[    1.488181] hub 1-0:1.0: 8 ports detected
[    1.488317] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.488336]   alloc irq_desc for 17 on node -1
[    1.488339]   alloc kstat_irqs on node -1
[    1.488346] ohci_hcd 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.488361] ohci_hcd 0000:00:1c.0: OHCI Host Controller
[    1.488413] ohci_hcd 0000:00:1c.0: new USB bus registered, assigned bus number 2
[    1.488456] ohci_hcd 0000:00:1c.0: irq 17, io mem 0xff6ff000
[    1.546133] hub 2-0:1.0: USB hub found
[    1.546143] hub 2-0:1.0: 3 ports detected
[    1.546226]   alloc irq_desc for 18 on node -1
[    1.546229]   alloc kstat_irqs on node -1
[    1.546235] ohci_hcd 0000:00:1c.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.546249] ohci_hcd 0000:00:1c.1: OHCI Host Controller
[    1.546289] ohci_hcd 0000:00:1c.1: new USB bus registered, assigned bus number 3
[    1.546329] ohci_hcd 0000:00:1c.1: irq 18, io mem 0xff6fe000
[    1.602131] hub 3-0:1.0: USB hub found
[    1.602140] hub 3-0:1.0: 3 ports detected
[    1.602222]   alloc irq_desc for 19 on node -1
[    1.602225]   alloc kstat_irqs on node -1
[    1.602231] ohci_hcd 0000:00:1c.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.602246] ohci_hcd 0000:00:1c.2: OHCI Host Controller
[    1.602295] ohci_hcd 0000:00:1c.2: new USB bus registered, assigned bus number 4
[    1.602333] ohci_hcd 0000:00:1c.2: irq 19, io mem 0xff6fd000
[    1.628411] ata5.00: ATAPI: LITE-ON DVDRW SHW-160P6S, PRS2, max UDMA/66
[    1.628443] ata5.00: WARNING: ATAPI DMA disabled for reliability issues.  It can be enabled
[    1.628447] ata5.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    1.658141] hub 4-0:1.0: USB hub found
[    1.658152] hub 4-0:1.0: 3 ports detected
[    1.658240] uhci_hcd: USB Universal Host Controller Interface driver
[    1.658372] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.660399] ata5.00: configured for UDMA/66
[    1.660843] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.660855] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.661017] mice: PS/2 mouse device common for all mice
[    1.661142] rtc_cmos 00:02: RTC can wake from S4
[    1.661197] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.661245] rtc0: alarms up to one month, 114 bytes nvram
[    1.661392] device-mapper: uevent: version 1.0.3
[    1.661556] device-mapper: ioctl: 4.16.0-ioctl (2009-11-05) initialised: dm-devel@redhat.com
[    1.661690] device-mapper: multipath: version 1.1.1 loaded
[    1.661695] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.661867] EISA: Probing bus 0 at eisa.0
[    1.661896] Cannot allocate resource for EISA slot 4
[    1.661923] EISA: Detected 0 cards.
[    1.662094] cpuidle: using governor ladder
[    1.662097] cpuidle: using governor menu
[    1.662709] TCP cubic registered
[    1.662891] NET: Registered protocol family 10
[    1.663497] lo: Disabled Privacy Extensions
[    1.663898] NET: Registered protocol family 17
[    1.663924] Bluetooth: L2CAP ver 2.14
[    1.663927] Bluetooth: L2CAP socket layer initialized
[    1.663931] Bluetooth: SCO (Voice Link) ver 0.6
[    1.663933] Bluetooth: SCO socket layer initialized
[    1.663990] Bluetooth: RFCOMM TTY layer initialized
[    1.663995] Bluetooth: RFCOMM socket layer initialized
[    1.663998] Bluetooth: RFCOMM ver 1.11
[    1.664070] Using IPI No-Shortcut mode
[    1.664173] PM: Resume from disk failed.
[    1.664191] registered taskstats version 1
[    1.664453]   Magic number: 2:417:268
[    1.664602] rtc_cmos 00:02: setting system clock to 2010-03-13 07:15:21 UTC (1268464521)
[    1.664607] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.664609] EDD information not available.
[    1.686878] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.916094] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.924576] ata1.00: ATA-7: WDC WD1600JS-22NCB1, 10.02E02, max UDMA/133
[    1.924581] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.932599] ata1.00: configured for UDMA/133
[    1.932789] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JS-22N 10.0 PQ: 0 ANSI: 5
[    1.933021] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.933103] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.933204] sd 0:0:0:0: [sda] Write Protect is off
[    1.933209] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.933248] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.933470]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.972860] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.168031] usb 3-1: new full speed USB device using ohci_hcd and address 2
[    2.628031] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    2.869082] scsi 4:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-160P6S PRS2 PQ: 0 ANSI: 5
[    2.873585] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.873589] Uniform CD-ROM driver Revision: 3.20
[    2.873704] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.873767] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    3.028141] Freeing unused kernel memory: 612k freed
[    3.028895] Write protecting the kernel text: 4708k
[    3.028956] Write protecting the kernel read-only data: 1992k
[    3.283343] Initializing USB Mass Storage driver...
[    3.319946] scsi6 : usb-storage 3-1:1.2
[    3.320890] scsi7 : usb-storage 4-1:1.0
[    3.327149] usbcore: registered new interface driver usb-storage
[    3.327156] USB Mass Storage support registered.
[    3.327794]   alloc irq_desc for 20 on node -1
[    3.327801]   alloc kstat_irqs on node -1
[    3.327820] skge 0000:02:15.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.327910] skge: 1.13 addr 0xff5fc000 irq 20 chip Yukon-Lite rev 9
[    3.329367] skge 0000:02:15.0: eth0: addr 00:16:ec:9f:83:9a
[    3.336795] ohci1394 0000:02:16.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.337226] FDC 0 is a post-1991 82077
[    3.394059] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[23]  MMIO=[ff5fb800-ff5fbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.799661] kjournald starting.  Commit interval 5 seconds
[    3.799677] EXT3-fs (sda3): mounted filesystem with ordered data mode
[    4.325151] scsi 6:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
[    4.325932] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.333157] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    4.340177] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    4.347174] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    4.347190] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    4.354133] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    4.354744] sd 7:0:0:0: Attached scsi generic sg3 type 0
[    4.354955] sd 7:0:0:1: Attached scsi generic sg4 type 0
[    4.355135] sd 7:0:0:2: Attached scsi generic sg5 type 0
[    4.355302] sd 7:0:0:3: Attached scsi generic sg6 type 0
[    4.387124] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[    4.420211] sd 7:0:0:2: [sde] Attached SCSI removable disk
[    4.431131] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[    4.442117] sd 7:0:0:3: [sdf] Attached SCSI removable disk
[    4.668343] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff55c3b8]
[    7.963149] Adding 1020088k swap on /dev/sda5.  Priority:-1 extents:1 across:1020088k 
[    8.311887] udev: starting version 151
[    8.843321] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.049903] psmouse serio1: ID: 10 00 64
[    9.312633] Linux agpgart interface v0.103
[    9.325260] parport_pc 00:0a: reported by Plug and Play ACPI
[    9.325406] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    9.328634] lp: driver loaded but no devices found
[    9.420240] lp0: using parport0 (interrupt-driven).
[    9.437250] ppdev: user-space parallel port driver
[    9.597248] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[    9.704551] ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
[    9.704559] ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not inserted.
[    9.745270] ali15x3_smbus 0000:00:1e.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[    9.745362] ali15x3_smbus 0000:00:1e.1: ALI15X3 not detected, module not inserted.
[    9.900592] [drm] Initialized drm 1.1.0 20060810
[    9.942646] it87: Found IT8712F chip at 0xa10, revision 7
[    9.942670] it87: in3 is VCC (+5V)
[    9.942674] it87: in7 is VCCH (+5V Stand-By)
[   10.257359] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.623031] [drm] radeon defaulting to kernel modesetting.
[   10.623039] [drm] radeon kernel modesetting enabled.
[   10.623141] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.627679] [drm] radeon: Initializing kernel modesetting.
[   10.627932] [drm] register mmio base: 0xFF4F0000
[   10.627937] [drm] register mmio size: 65536
[   10.631029] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   10.631038] [drm] 1 Power State(s)
[   10.631043] [drm] State 0 Default (default)
[   10.631046] [drm]     1 Clock Mode(s)
[   10.631049] [drm]         0 engine: 300000
[   10.631070] [drm] radeon: power management initialized
[   10.631076] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   10.631149] [drm] Generation 2 PCI interface, using max accessible memory
[   10.631157] radeon 0000:01:05.0: VRAM: 128M 0x18000000 - 0x1FFFFFFF (128M used)
[   10.631162] radeon 0000:01:05.0: GTT: 32M 0x20000000 - 0x21FFFFFF
[   10.631203] [drm] radeon: irq initialized.
[   10.631637] [drm] Detected VRAM RAM=128M, BAR=256M
[   10.631645] [drm] RAM width 128bits DDR
[   10.631792] [TTM] Zone  kernel: Available graphics memory: 189638 kiB.
[   10.631827] [drm] radeon: 128M of VRAM memory ready
[   10.631831] [drm] radeon: 32M of GTT memory ready.
[   10.631873] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   10.634282] [drm] radeon: 4 quad pipes, 1 z pipes initialized.
[   10.634908] [drm] radeon: cp idle (0x10000C03)
[   10.635485] [drm] Loading R300 Microcode
[   10.635981] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   10.646110] nf_conntrack version 0.5.0 (5926 buckets, 23704 max)
[   10.647437] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   10.647444] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   10.647449] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   10.803465] [drm] radeon: ring at 0x0000000020000000
[   10.803496] [drm] ring test succeeded in 0 usecs
[   10.803804] [drm] radeon: ib pool ready.
[   10.803964] [drm] ib test succeeded in 0 usecs
[   10.804120] [drm] Default TV standard: NTSC
[   10.804125] [drm] 14.318180000 MHz TV ref clk
[   10.804331] [drm] Default TV standard: NTSC
[   10.804336] [drm] 14.318180000 MHz TV ref clk
[   10.804396] [drm] Radeon Display Connectors
[   10.804400] [drm] Connector 0:
[   10.804403] [drm]   VGA
[   10.804408] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   10.804412] [drm]   Encoders:
[   10.804416] [drm]     CRT1: INTERNAL_DAC2
[   10.804419] [drm] Connector 1:
[   10.804422] [drm]   S-video
[   10.804425] [drm]   Encoders:
[   10.804427] [drm]     TV1: INTERNAL_DAC2
[   10.930976] [drm] fb mappable at 0xC0040000
[   10.930981] [drm] vram apper at 0xC0000000
[   10.930984] [drm] size 5184000
[   10.930986] [drm] fb depth is 24
[   10.930988] [drm]    pitch is 5760
[   10.931110] fb0: radeondrmfb frame buffer device
[   10.931114] registered panic notifier
[   10.931127] [drm] Initialized radeon 2.1.0 20080528 for 0000:01:05.0 on minor 0
[   10.997680]   alloc irq_desc for 22 on node -1
[   10.997687]   alloc kstat_irqs on node -1
[   10.997703] HDA Intel 0000:00:1d.0: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   11.089593] hda_codec: ALC880: BIOS auto-probing.
[   11.091167] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1d.0/input/input4
[   11.277731] Console: switching to colour frame buffer device 180x56
[   11.300128] usb 3-1: reset full speed USB device using ohci_hcd and address 2
[   11.486407] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x080F
[   11.486463] usbcore: registered new interface driver usblp
[   11.493408] usblp0: removed
[   11.624047] usb 3-1: reset full speed USB device using ohci_hcd and address 2
[   11.808379] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x080F
[   11.822320] usblp0: removed
[   11.952548] usb 3-1: reset full speed USB device using ohci_hcd and address 2
[   11.962591] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   12.136379] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x080F
[   15.437119] EXT3-fs (sda3): using internal journal
[   16.220269] kjournald starting.  Commit interval 5 seconds
[   16.220558] EXT3-fs (sda6): using internal journal
[   16.220567] EXT3-fs (sda6): mounted filesystem with ordered data mode
[   19.223084] skge 0000:02:15.0: eth0: enabling interface
[   19.226968] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.155645] skge 0000:02:15.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[   21.155698] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```

/var/log/dmesg

---

### Post by Herman on 2010-03-13
I just finished tweaking it a little bit more and probably some updates helped as well. 

Now I have it down to 4.46 seconds.


[IMG]http://members.iinet.net/%7Eherman546/p1/ocz-lynx-lucid-20100314-11.png[/IMG]

---

### Post by d3v1150m471c on 2010-03-13
When I used ubuntu i could boot in 20 seconds. Kubuntu is much slower to boot but I love the environment. Hibernate is our friend.

---

### Post by Herman on 2010-03-14
:-k Hmm ... Yes, I agree that it would be better to hibernate than shut down and boot up.

Remember that not everyone will have hardware that's as well supported as yours though.

The computer I'm using right now is quite capable of hibernating and resuming, but all my fans keep running at full speed so I think it will still be consuming a lot of energy and giving off a lot of noise and heat for hours at a time for no good reason. I'd rather shut down.

However, you do make a good point. If I invest as much time into finding out how to get my motherboard's built in power saving features working, that would also be quite a satisfying achievement. I have an ASUS P5QL PRO 'Green' motherboard, advertised to feature all kinds of cool energy saving ideas. Unfortunately now that I'm the proud owner of it I find that it comes with a CD full of special software that will only work in Windows. Maybe some day if I live long enough and keep learning Linux I will be able to eventually write my own device drivers for Linux, that would be cool!  

In the meantime though, I'll be shutting down and booting. :D

---

### Post by MacUntu on 2010-03-14
> **Herman said:**
> Now I have it down to 4.46 seconds.
Nice! How much time does the system take to start GRUB2 (and doesn't that make you feel bad)? :D

I guess with a little tweaking I can get 10 seconds with my 7200rpm disc but definitely not less. It's time to SSD! ;)

---

### Post by Herman on 2010-03-14
> How much time does the system take to start GRUB2 (and doesen't that make you feel bad)?:D LOL - Yes!  You're right.
The motherboard manual that came with this motherboard points out the fact that I can display a boot logo as one of its endearing features and avoids mentioning the length of time I will have to admire my nice boot logo. 
This motherboard seems to take approximately 22 seconds to P.O.S.T. and finally arrive at the GRUB Menu, which I think seems like an eternity now that I have Ubuntu booting so quickly by comparison. 

Maybe I should take a look around in the BIOS and see if there are some settings in there that can be improved a little. :D

EDIT: Or at least I have been blaming the BIOS for the time it takes to reach the GRUB2 menu. Do you think GRUB2 takes longer to load than other boot loaders?
EDIT: I found some BIOS settings I hadn't paid attention to before and reduced the time from power on to GRUB Menu to 16 seconds, but that still seems like a very long time.

---

### Post by farrell on 2010-03-14
> **Herman said:**
> Maybe I should take a look around in the BIOS and see if there are some settings in there that can be improved a little. :D

Tweaking the BIOS did improve my POST time. Look for the boot sequence and things to check on boot. Disabling unused devices is also a good idea, as it speeds up the Ubuntu boot.

> **Herman said:**
> EDIT: Or at least I have been blaming the BIOS for the time it takes to reach the GRUB2 menu. Do you think GRUB2 takes longer to load than other boot loaders?

For me GRUB2 takes 2 seconds to instantly boot the preselected item on a SSD, compared to my 10 second POST i'm fine with it. uboot should be faster, or you could try booting without a bootloader (i think this requires a custom kernel).

Btw, congrats on your uber-fast boot!

EDIT: If you're into booting, you might enjoy this one: [http://www.linuxjournal.com/article/2239](http://www.linuxjournal.com/article/2239)

---

### Post by Herman on 2010-03-14
> Tweaking the BIOS did improve my POST time. Look for the boot sequence and things to check on boot. Disabling unused devices is also a good idea, as it speeds up the Ubuntu boot.Thanks, I'll take another look in there.
> For me GRUB2 takes 2 seconds to instantly boot the preselected item on a SSD, compared to my 10 second POST i'm fine with it. uboot should be faster, or you could try booting without a bootloader (i think this requires a custom kernel).
Btw, congrats on your uber-fast boot! 	Thank you. 
I have never thought there might be a difference in speed between different boot loaders. That's interesting to learn. I'll look into uboot. A self booting kernel you say? Wow! That's also something interesting I'll have to look up. Cool! :D

---

### Post by dbowlin17 on 2010-03-14
from the first flash of the lights on my keyboard, and going through grub (and me selecting Lucid) 24 seconds. much improved. I will say, and this is with a 2.0ghz single core P4 and 1.5gb of Rambus Ram

---

### Post by ShadowDragon on 2010-03-14
> **Herman said:**
> Thanks, I'll take another look in there.
Thank you. 
I have never thought there might be a difference in speed between different boot loaders. That's interesting to learn. I'll look into uboot. A self booting kernel you say? Wow! That's also something interesting I'll have to look up. Cool! :D
Hi Herman,

I followed your link from the OCZ-forum to this thread and if you are really performance interested you should definitely take a look at ['timechart'](http://lwn.net/Articles/352746/), it's much more fine-grained than bootchart, to allow you to tweak the most out of it.

Have fun reading. And the most important, enjoy your drive! It's why you bought it, not only to bench, but to experience the not to experience the waiting :D

Greetings,
ShadowDragon.

---

### Post by andrewabc on 2010-03-14
> **d3v1150m471c said:**
> Hibernate is our friend.

Suspend works better for me. desktop.

---

### Post by Herman on 2010-03-14
> I followed your link from the OCZ-forum to this thread and if you are really performance interested you should definitely take a look at ['timechart']("http://lwn.net/Articles/352746/"), it's much more fine-grained than bootchart, to allow you to tweak the most out of it.

Have fun reading. And the most important, enjoy your drive! It's why you bought it, not only to bench, but to experience the not to experience the waiting :grin:Thank you, ShadowDragon, yes, I am interested in learning more about getting the best performance from my SSD and also how to use benchmarking. 
My work involves a lot of GIS (computerized mapping) and I expect that to become a lot more popular since more and more mobile phones and digital cameras are starting to include GPSs now.
I'm planning on using my SSD for working with mapping software such as Quantum GIS as soon as that's available for Lucid Lynx, (I haven't been successful in installing it in Lucid as yet). It's be nice to be able to pan around on a large map without having to wait for the image to re-draw in the screen which can be slow with a hard disk drive, especially if the map includes any large rasters.
And I must say that it's a pleasure to use such as fast drive in general, everything just seems so nice and snappy!
I think that in the future hard disks will be used for storage and SSDs will take over for the operating system drive in most people's computers. :D

---

### Post by ronparent on 2010-03-14
Herman: Amen to that. I have just installed an SSD and improvement in performance exceeds any other upgrade I have made!

---

### Post by psusi on 2010-03-15
I got an OCZ Vertex 60 gig SSD on Friday and had LVM migrate the root of my running lucid install over to it on the fly, which was pretty cool, then installed grub, rebooted and WOW.  I have similar results to Herman with about a 5 second bootchart.  Very nice!

---

### Post by Owen.C93 on 2010-03-18
Hmmm, anything bottle necking in mine? I've seen faster boots with other less powerful machines.
[IMG]http://tinypic.com/r/ma80so/5[/IMG]
[http://i39.tinypic.com/ma80so.jpg](http://i39.tinypic.com/ma80so.jpg)

Any help if greatly appreciated even if it's the harsh truth lol.

---

### Post by trystan.snyder on 2010-03-18
> **Owen.C93 said:**
> 
Any help if greatly appreciated even if it's the harsh truth lol.

The harsh truth is, we need to see a higher res pic :shock:

---

### Post by andrewabc on 2010-03-18
> **Owen.C93 said:**
> Hmmm, anything bottle necking in mine? I've seen faster boots with other less powerful machines.
[IMG]http://tinypic.com/r/ma80so/5[/IMG]
[http://i39.tinypic.com/ma80so.jpg](http://i39.tinypic.com/ma80so.jpg)

Any help if greatly appreciated even if it's the harsh truth lol.

tinypic upload has been resized. Unreadable.
Don't upload to forum either (will resize).
Unless in a .zip file?

---

### Post by Fred the Penguin on 2010-03-18
Lucid has a slightly slower boot up for me than for karmic.  I booted Karmic in under 30 seconds, but Lucid took about 40. It always has a blinking beam for about 10 seconds in the beginning and then comes up with a message that I don't have time to read, but I think it is an error or warning.

---

### Post by Owen.C93 on 2010-03-19
Sorry I hadn't realised it was so small. However now boot time is alot less for some reason. Down from 40 to 25. 

Still if you want to have a qick look for any errors here's the latest chart.
[http://img202.imageshack.us/img202/4322/owenclucid201003191.png](http://img202.imageshack.us/img202/4322/owenclucid201003191.png)[URL="http://img693.imageshack.us/img693/7566/owenclucid201003181.png"]
[/URL]

---

### Post by dxxvi on 2010-03-19
Hi,

What does the option "ro" in your kernel options do? Does it affect the boot time?

Regards.

---

### Post by praveenthivari on 2010-03-19
Mine is here.
Reads around 17- 18 sec

---

### Post by Owen.C93 on 2010-03-19
> **dxxvi said:**
> Hi,

What does the option "ro" in your kernel options do? Does it affect the boot time?

Regards.
No idea, it isn't there in /boot/grub/grub.

---

### Post by hugmenot on 2010-03-19
Herman, you still have HAL installed, which does quite a bit of I/O during boot. Try to remove it. The normal Ubuntu packages should no longer depend on HAL but on libgudev instead.

---

### Post by Herman on 2010-03-19
> Herman, you still have HAL installed, which does quite a bit of I/O during boot. Try to remove it. The normal Ubuntu packages should no longer depend on HAL but on libgudev instead.:D Thank you, hugmenot, I'll try that as soon as it's convenient for me and take another look at my boot charts afterwards.


EDIT: Oh wow!
It looks like that did make a difference, 4.27 seconds now, 

Oops! Scratch that one, try 4.19 seconds instead ... 


[IMG]http://members.iinet.net/%7Eherman546/p1/ocz-lynx-lucid-20100320-8.png[/IMG]

---

### Post by HoboJ on 2010-03-20
I'm averaging 13.21 seconds. Which is amazing because I could never achieve this on any other OS. My HDD is a seagate 250gb 7200rpm. Four partitions, incl one swap. Lucid is on a middle partition as well. Mind = blown.

Here's my bootchart. [http://img52.imageshack.us/img52/862/tjdesktoplucid201003204.png](http://img52.imageshack.us/img52/862/tjdesktoplucid201003204.png)

---

### Post by eyeyoubin on 2010-03-20
39.54 seconds. pretty happy with that.
Intel Core 2 Duo 2.13GHz
2GB RAM

[[IMG]http://imgur.com/k4m4Fs.jpg[/IMG]](http://imgur.com/k4m4F.png)

---

### Post by ankspo71 on 2010-03-21
Hi,
I was getting really discouraged because I was getting mid 20's at first, then later more than a minute through Lucid Alpha2. Now that I'm using Beta 1, I'm back down to 22.53. Not bad for this computer! :p Pentium 4 3.0ghz, 2gb memory.
[http://img339.imageshack.us/img339/2741/jameslucid201003213.png](http://img339.imageshack.us/img339/2741/jameslucid201003213.png)

---

### Post by Owen.C93 on 2010-03-22
Hi I'm hoping someone can help me. For some random reson I either get a 30 second boot or a 50 second. It's either or and I can't reall tell what's up. ANyway heres the 2 bootcharts I hope someone can help.

Truth be told for a 2.0ghz dual core with 3gb of ram I am a little disappointed.

[http://img62.imageshack.us/img62/8004/owenclucid201003226.png](http://img62.imageshack.us/img62/8004/owenclucid201003226.png)
[http://img84.imageshack.us/img84/1055/owenclucid201003228.png](http://img84.imageshack.us/img84/1055/owenclucid201003228.png)

---

### Post by ShadowDragon on 2010-03-22
@Owen.C93
What's the output of:
```
sudo ureadahead --dump | head -n 2
```
I'm wondering how large the ureadahead-pack is you're trying to read while booting.

Mine's about ~175MB on a SSD with Xubuntu Karmic.
```
sudo ureadahead --dump | head -n 2
/var/lib/ureadahead/pack: created Sun, 21 Mar 2010 23:46:24 +0000 for ssd 8:1
0 inode groups, 2421 files, 2333 blocks (174668 kB)
```

---

### Post by _h_ on 2010-03-22
34.48 seconds.
<removed tinypic url>


EDIT: Stupid Tinypic. -.-


[http://img708.imageshack.us/img708/3107/daniellaptoplucid201003.png](http://img708.imageshack.us/img708/3107/daniellaptoplucid201003.png)

---

### Post by ViperScull on 2010-03-23
> **ShadowDragon said:**
> What's the output of:
```
sudo ureadahead --dump | head -n 2
```


> sudo ureadahead --dump | head -n 2
ureadahead:/var/lib/ureadahead/pack: No such file or directory

don't have that file

---

### Post by philinux on 2010-03-23
After a reprofile I get about 25 secs. Otherwise it can be 35. Still miles better then karmic at just over 1 minute.

---

### Post by andrewabc on 2010-03-23
> **Owen.C93 said:**
> Hi I'm hoping someone can help me. For some random reson I either get a 30 second boot or a 50 second. It's either or and I can't reall tell what's up. ANyway heres the 2 bootcharts I hope someone can help.

Truth be told for a 2.0ghz dual core with 3gb of ram I am a little disappointed.

[http://img62.imageshack.us/img62/8004/owenclucid201003226.png](http://img62.imageshack.us/img62/8004/owenclucid201003226.png)
[http://img84.imageshack.us/img84/1055/owenclucid201003228.png](http://img84.imageshack.us/img84/1055/owenclucid201003228.png)

There seems to be difference in bootcharts in what is being booted. Not sure what, but near end of both bootcharts (just before kthreadd) stuff is in different order.

In both bootcharts it looks like everythign is fully loaded by 25 second mark.

The reason for 30 second boot is your hard drive is bottleneck. Looking at top of bootchart graph, your CPU rarely goes 100%, and your HDD disk utilization is at max most of the time. You max out at 50mb/s and part of the time it is very low. Normal for hard drives.
What type of hard drive? 7200rpm? how much cache? (basically is it old?)

Overall your 30 second bootchart looks normal.

---

### Post by Owen.C93 on 2010-03-23
> **ShadowDragon said:**
> @Owen.C93
What's the output of:
```
sudo ureadahead --dump | head -n 2
```I'm wondering how large the ureadahead-pack is you're trying to read while booting.

Mine's about ~175MB on a SSD with Xubuntu Karmic.
```
sudo ureadahead --dump | head -n 2
/var/lib/ureadahead/pack: created Sun, 21 Mar 2010 23:46:24 +0000 for ssd 8:1
0 inode groups, 2421 files, 2333 blocks (174668 kB)
```
It's about 220mb. :L:???:
> **andrewabc said:**
> There seems to be difference in bootcharts in what is being booted. Not sure what, but near end of both bootcharts (just before kthreadd) stuff is in different order.

In both bootcharts it looks like everythign is fully loaded by 25 second mark.

The reason for 30 second boot is your hard drive is bottleneck. Looking at top of bootchart graph, your CPU rarely goes 100%, and your HDD disk utilization is at max most of the time. You max out at 50mb/s and part of the time it is very low. Normal for hard drives.
What type of hard drive? 7200rpm? how much cache? (basically is it old?)

Overall your 30 second bootchart looks normal.
It's a laptop so 2.5inch 5400rpm. Still it is only 2 years old. I wander what makes some boots longer and in a different order than another then? :???: 

Thanks for all your help guys. :)

---

### Post by ShadowDragon on 2010-03-23
> **Owen.C93 said:**
> It's about 220mb. :L:???:
That's a normal value for ureadahead-pack. I'm running a tweaked Xubuntu, so that's why I'm having a lower value ;)

> **Owen.C93 said:**
> It's a laptop so 2.5inch 5400rpm. Still it is only 2 years old.
5400rpm, means long rotational latencies... if the files needed for booting aren't places physically sequential on your disk, your head needs to do a seek-operation. Depending on what kind of drive you have it can easily take up to 10-15 milliseconds. (You can find it in the data-sheet of your drive) That means if that you can only read 100 files in 1 second (which results in a 0.4 MiB/s (!) throughput if you have a standard 4KiB-block-size filesystem). If you see that during my boot there are about 2500 files needed to be read from disk, you can do the math ;)

Now you also know why the reference-platform for ubuntu-booting (a Dell Mini with a SSD) is able to achieve 10 seconds boots. Seek-operations on SSD are easily 100 times faster (in the range of 0.1 ms) That's also one of the reasons why I'm running a SSD since June '09. :D

---

### Post by psusi on 2010-03-23
> **ShadowDragon said:**
> 
5400rpm, means long rotational latencies... if the files needed for booting aren't places physically sequential on your disk, your head needs to do a seek-operation. Depending on what kind of drive you have it can easily take up to 10-15 milliseconds. (You can find it in the data-sheet of your drive) That means if that you can only read 100 files in 1 second (which results in a 0.4 MiB/s (!) throughput if you have a standard 4KiB-block-size filesystem). If you see that during my boot there are about 2500 files needed to be read from disk, you can do the math ;)

Except that ureadahead makes sure to read the files in the order they are stored on disk, to minimize seeking.

---

### Post by Owen.C93 on 2010-03-23
Ok I guess my boot time was to be expected. I have posted a question on a decent defrager as that may help ureadahead.

Still unsure on why I get either a 30sec or a 45 (and it is either or). Thanks for all your help and I am contimplating an ssd in the near future.

---

### Post by keptang on 2010-03-23
9.73 seconds.

[http://img692.imageshack.us/img692/6894/latitude13lucid20100323.png](http://img692.imageshack.us/img692/6894/latitude13lucid20100323.png)

---

### Post by ankspo71 on 2010-03-23
> **ankspo71 said:**
> Hi,
I was getting really discouraged because I was getting mid 20's at first, then later more than a minute through Lucid Alpha2. Now that I'm using Beta 1, I'm back down to 22.53. Not bad for this computer! :p Pentium 4 3.0ghz, 2gb memory.
[http://img339.imageshack.us/img339/2741/jameslucid201003213.png](http://img339.imageshack.us/img339/2741/jameslucid201003213.png)

My original post is in the quote. I tweaked my system a bit and I just went from 22.53 to 18.24. Here's some of the things I did:
Installed boot up manager (bum), and disabled unneeded services. 
Disabled unneeded startup applications.
Disabled compiz
Enabled metacity compositing.
Reduced the number of applets in my gnome panel.
Original:
[http://img339.imageshack.us/img339/2741/jameslucid201003213.png](http://img339.imageshack.us/img339/2741/jameslucid201003213.png)
New:
[http://img180.imageshack.us/img180/8894/jameslucid201003233.png](http://img180.imageshack.us/img180/8894/jameslucid201003233.png)

---

### Post by philinux on 2010-03-23
@ankspo71

Which things did you disable with BUM?

---

### Post by _h_ on 2010-03-23
I am extrmely impressed by the new kernel update today (2.6.32-17).

My previous boot time of 34.48 seconds on 2.6.32-16 kernel:

[http://img708.imageshack.us/img708/3107/daniellaptoplucid201003.png](http://img708.imageshack.us/img708/3107/daniellaptoplucid201003.png)

And my new 18.70 second boot time on the 2.6.32-17 kernel:

[http://img717.imageshack.us/img717/3107/daniellaptoplucid201003.png](http://img717.imageshack.us/img717/3107/daniellaptoplucid201003.png)

---

### Post by ankspo71 on 2010-03-23
> **philinux said:**
> @ankspo71

Which things did you disable with BUM?

Hi, I really should have wrote them down.;) But looking in advanced mode, what I still have activated is:

(in summary and services tab)
kerneloops
rsync
pulseaudio
ppd-dns
dns-clean

(In startup and shutdown scripts )
pcmciautils

This is a basic system, so I don't need services for bluetooth, printer, scanner, etc. I forgot to say I also disabled the screensaver too.

---

### Post by Owen.C93 on 2010-03-23
> **_h_ said:**
> I am extrmely impressed by the new kernel update today (2.6.32-17).

My previous boot time of 34.48 seconds on 2.6.32-16 kernel:

[http://img708.imageshack.us/img708/3107/daniellaptoplucid201003.png](http://img708.imageshack.us/img708/3107/daniellaptoplucid201003.png)

And my new 18.70 second boot time on the 2.6.32-17 kernel:

[http://img717.imageshack.us/img717/3107/daniellaptoplucid201003.png](http://img717.imageshack.us/img717/3107/daniellaptoplucid201003.png)
I'm on it.....

---

### Post by solitaire on 2010-03-23
Drat!
I usually got 1m 25s in 9.10
Upgraded the install to 10.04
and i'm gettin a slow 25seconds :D:D lol!!

Did they change the start / stop points of bootchart again?
I know the changed it in 9.10 are those still the same start / stop points?

[http://i12.photobucket.com/albums/a233/s0litaire/europa-lucid-20100323-4.png](http://i12.photobucket.com/albums/a233/s0litaire/europa-lucid-20100323-4.png)

---

### Post by zengeos on 2010-03-23
32 seconds current beta with latest updates.

65 seconds Linux Mint 9.10

---

### Post by ElSlunko on 2010-03-23
Bootchart from today & one from 5 days ago. Time almost halved.

---

### Post by 2hot6ft2 on 2010-03-23
Sweet, compiz enabled. With NTFS partition and 3 other OSes on drive.
Bluetooth Manager, Gnome Login Sound, Gnome Remote Desktop Server, disabled in Startup Applications
Running applets in panel include Hardware sensors, System Monitor, Brightness applet, Force Quit, Pacellite and Weather w/clock
2.6.32-17 kernel @ 21.89 seconds on top
2.6.32-16 kernel @ 20.68 seconds on bottom
[[IMG]http://img256.imageshack.us/img256/9309/hot6ft2laptoplucid20100.png[/IMG]](http://img256.imageshack.us/i/hot6ft2laptoplucid20100.png/)
[[IMG]http://img688.imageshack.us/img688/9309/hot6ft2laptoplucid20100.png[/IMG]](http://img688.imageshack.us/i/hot6ft2laptoplucid20100.png/)

---

### Post by zengeos on 2010-03-23
Actually, to be more precise:

latest beta boot   29 seconds
Mint 8   1:09 seconds

I have 3 different linux partitions, plus a swap partition, and 2 Windows partitions on this hard drive, if that has any effect on boot time....

---

### Post by drfox on 2010-03-23
OK, I seriously need some help here. I have an AMD-64 Athlonx2 system, and it really should be quicker. I would appreciate suggestions of what I can do to speed boot time.
Larry
[IMG]http://img534.imageshack.us/img534/7443/bigdoglucid201003235.png[/IMG]

Thanks for the tip about ImageShack

---

### Post by _h_ on 2010-03-23
> **drfox said:**
> OK, I seriously need some help here. I have an AMD-64 Athlonx2 system, and it really should be quicker. I would appreciate suggestions of what I can do to speed boot time.
Larry

Post your bootchart to imageshack, attaching it here we can't see it in full.

---

### Post by ElSlunko on 2010-03-23
> **_h_ said:**
> Post your bootchart to imageshack, attaching it here we can't see it in full.

Oops!

Mine went from 55 to 31 seconds between 5 days ago & Today.

---

### Post by _h_ on 2010-03-23
> **ElSlunko said:**
> Oops!

Mine went from 55 to 31 seconds between 5 days ago & Today.

Nice, quite the improvement. :D What kind of hardware?

---

### Post by Arlanthir on 2010-03-23
Hm.

You guys don't have all [these flushes]("http://dl.dropbox.com/u/748218/Icarus-lucid-20100323-2.png"). Should I investigate?

Only 24 seconds is very nice, but it seems more because I'm seeing a black screen with a blinking cursor for 90% of the time, then plymouth shows up for a second there and then GDM.

---

### Post by jochem on 2010-03-23
[http://z1.zod.fr/z/jochem-laptop-lucid-20100324-2-wR0.png](http://z1.zod.fr/z/jochem-laptop-lucid-20100324-2-wR0.png)3x sec :D

In the beginning it says "wait-for-root" and "resume", arlanthir has them running for a much shorter period, why? :O

---

### Post by cariboo on 2010-03-23
The latest:

[[IMG]http://imgur.com/Cyv7is.jpg[/IMG]](http://imgur.com/Cyv7i.png)

---

### Post by andrewabc on 2010-03-23
> **Owen.C93 said:**
> It's a laptop so 2.5inch 5400rpm. Still it is only 2 years old. I wander what makes some boots longer and in a different order than another then? :???: 

Thanks for all your help guys. :)



> **Owen.C93 said:**
> Ok I guess my boot time was to be expected. I have posted a question on a decent defrager as that may help ureadahead.

Still unsure on why I get either a 30sec or a 45 (and it is either or). Thanks for all your help and I am contimplating an ssd in the near future.

With laptop, 5400rpm 2 years old. I'd be happy with the 30 second boot your getting. About as good as you'll get. My 3.5 year old 7200 rpm 8mb cache, core2duo desktop was getting ~20 second boot with ubuntu 9.04.
Now with my SSD in 9.10 I was getting 10 seconds I think. Basically real fast and I had bug with grub that made it longer to show than to load ubuntu.

Looking forward to 10.04 (and upgrade my SSD firmware).

---

### Post by _h_ on 2010-03-23
So I got to thinking, if I'm hitting 18 second boot times, I wonder what I could get if I went and did some tweaking (like disable compiz, and disable stuff via BUM).

Will have to test that soon.

---

### Post by ShadowDragon on 2010-03-23
Strange: hardware-detection time (or whatever you call the time between the start of init and the second process that starts during booting) of [Cariboo907](http://ubuntuforums.org/showpost.php?p=9017377&postcount=257) (< 0.5 sec) is significantly less then that of [Arlanthir](http://ubuntuforums.org/showpost.php?p=9017129&postcount=255) (+/- 4.5 sec)

---

### Post by samh785 on 2010-03-23
[http://img695.imageshack.us/img695/8882/system76laptoplucid2010.png](http://img695.imageshack.us/img695/8882/system76laptoplucid2010.png)

20.43 seconds

---

### Post by ranch hand on 2010-03-23
> **cariboo907 said:**
> The latest:

[[IMG]http://imgur.com/Cyv7is.jpg[/IMG]]("http://imgur.com/Cyv7i.png")
No can see.

---

### Post by Starks on 2010-03-23
All time best. 24.287 seconds.

[http://img413.imageshack.us/img413/457/kingfisherlucid20100323.png]("http://img534.imageshack.us/img534/457/kingfisherlucid20100323.png")

---

### Post by cariboo on 2010-03-23
Just click on the little picture, then click on the image that opens up. :)

Heres's a new one second boot after installing 2.6.32-17 kernel

[[IMG]http://imgur.com/R73uhs.jpg[/IMG]](http://imgur.com/R73uh.png)

---

### Post by Starks on 2010-03-23
21.30 seconds. My goodness.

[http://img202.imageshack.us/img202/457/kingfisherlucid20100323.png](http://img202.imageshack.us/img202/457/kingfisherlucid20100323.png)

---

### Post by jochem on 2010-03-23
Removing my swap file was good for 5 seconds, was there something wrong with my swap file?
Removing services/startup programs and deleting a few movies was good for another 2 seconds.

Voila:

[http://z1.zod.fr/z/jochem-laptop-lucid-20100324-13-LR0.png](http://z1.zod.fr/z/jochem-laptop-lucid-20100324-13-LR0.png)

---

### Post by _h_ on 2010-03-23
> **cariboo907 said:**
> Just click on the little picture, then click on the image that opens up. :)

Heres's a new one second boot after installing 2.6.32-17 kernel

[[IMG]http://imgur.com/R73uhs.jpg[/IMG]]("http://imgur.com/R73uh.png")

Oh my...best boot time with the new kernel so far. Beat me by ~3 seconds cariboo. :O

---

### Post by jochem on 2010-03-23
Why do my udevd and udevadm have the zombie colour?:D

[http://z1.zod.fr/z/jochem-laptop-lucid-20100324-13-LR0.png](http://z1.zod.fr/z/jochem-laptop-lucid-20100324-13-LR0.png)

---

### Post by djchandler on 2010-03-24
New 2.6.32-17 kernel boot, fastest yet for this AMD powered Toshiba Satellite. Does this include the time it takes me to select my account and type in my password?

22.63 seconds

[Here's my boot chart]("http://djchandler.files.wordpress.com/2010/03/lapbuntu-lucid-20100324-1.png").

---

### Post by trystan.snyder on 2010-03-24
15 Seconds

[http://img59.imageshack.us/img59/2033/romuluslucid201003243.png](http://img59.imageshack.us/img59/2033/romuluslucid201003243.png)

---

### Post by garvinrick4 on 2010-03-24
I  have a younger brother who is an IT for the Lottery in the unix world for 20 years and
he stated to me if I do not turn the darn thing on I will not have to worry about 
shaving a few seconds off the boot time every version of Ubuntu I test for. I think he was being a bit of a wise guy but wise in every sense of the word. Maybe we all started in msconfig in the
Windows World deleting all the Google, Adobe and other crapola out of the startup tab for so
many years we have carried it over into Linux for more speed, more speed damn it Scotty more
speed. I need Warp 9 Scotty and now. Damn it Jim the coders are sick of us, they are going to
add plymouth to the equation if you do not relax Jim, plymouth I tell you Jim is a cruel master. 
No need to tell you Star Trek and warp 9 speed were cancelled after 3 seasons. And so will go plymouth. Have a nice day and remember we are UBUNTU not the Enterprise.

---

### Post by ShadowDragon on 2010-03-24
Well, it isn't really for only more speed. Just like when we want more comfort at home, you know that soft couch in front of the tele, I want comfort with my computer. I don't want to ask myself whether it's worth to boot my laptop to check the weather to decide if I should take my bike or the car. I just want to boot my laptop, check the weather, being happy that it will be sunshine all day and I can be a green guy by taking the bike without becoming soaking wet. And all of that within a comfortable time with minimal waste to waiting. I don't want to wait 1 minute of boot-time to last-minute check my schedule, where my next class will be, then I would be late and a bad impression for coming in late... For me it's just all about comfort.


The speedy thing is for bragging in the bar :cool:

---

### Post by Laibcoms on 2010-03-25
Hi I have a question.

Does the bootchart logging add some seconds to the logging?  (Dunno how to read the chart hehe :p )

I asked because I noticed that after installing bootchart, my boot-up of Lucid takes a little longer than without it.

Without it, if I count my boot-up it takes 13 seconds (10-13 to be exact, 14 at most but rarely).

After installing bootchart, it takes me 17-18 secs.

I of course tried counting manually, and my count is the same as what bootchart reported.  If my manual count is the same as bootchart, then my 13secs count without bootchart is accurate.

And by observation as well, after installing bootchart, I get to see the boot-up logo of ubuntu.  Without bootchart, the login box just pops-up.

So that prompted me to ask this question, does bootchart affects the boot-up time?  Taking my count above, it adds or delays boot-up by 4-5 secs?

Thanks!!

---

### Post by ikt on 2010-03-25
[http://img710.imageshack.us/img710/2290/iktdesktoplucid20100325.png](http://img710.imageshack.us/img710/2290/iktdesktoplucid20100325.png)

9 seconds

---

### Post by ranch hand on 2010-03-25
> **Laibcoms said:**
> Hi I have a question.

Does the bootchart logging add some seconds to the logging?  (Dunno how to read the chart hehe :p )

I asked because I noticed that after installing bootchart, my boot-up of Lucid takes a little longer than without it.

Without it, if I count my boot-up it takes 13 seconds (10-13 to be exact, 14 at most but rarely).

After installing bootchart, it takes me 17-18 secs.

I of course tried counting manually, and my count is the same as what bootchart reported.  If my manual count is the same as bootchart, then my 13secs count without bootchart is accurate.

And by observation as well, after installing bootchart, I get to see the boot-up logo of ubuntu.  Without bootchart, the login box just pops-up.

So that prompted me to ask this question, does bootchart affects the boot-up time?  Taking my count above, it adds or delays boot-up by 4-5 secs?

Thanks!!
Yes bootchart will add a little to boot time.

The difference is that folks will believe bootchart.  There is, obviously, some advantage of having a standard way of measuring.

---

### Post by Starks on 2010-03-25
ureadahead is a miracle worker. back in the jaunty/karmic days, my boot times averaged anywhere from 40 seconds to 90 seconds.

on the very same hardware, i'm down to 20 seconds now.

---

### Post by ShadowDragon on 2010-03-25
> **Laibcoms said:**
> Does the bootchart logging add some seconds to the logging?
Like 'ranch hand' already said, tracing will always be responsible for consuming clock-cycles, and thus I can add some time.

> **Laibcoms said:**
> (Dunno how to read the chart hehe :p )
Post a link to it here and we might read it for you ;)

> **Laibcoms said:**
> I asked because I noticed that after installing bootchart, my boot-up of Lucid takes a little longer than without it. Ehm, most people don't notice the difference since it's to small... If you're able to notice it then either you have very good senses or something is wrong / different.

> **Laibcoms said:**
> Without it, if I count my boot-up it takes 13 seconds (10-13 to be exact, 14 at most but rarely).

After installing bootchart, it takes me 17-18 secs.
Take in account that installing applications, like bootchart, will make ureadahead do a profiling on the next boot, which can add time to the booting.

> **Laibcoms said:**
> I of course tried counting manually, and my count is the same as what bootchart reported.  If my manual count is the same as bootchart, then my 13secs count without bootchart is accurate.
No doubt about your counting skills then :)

> **Laibcoms said:**
> And by observation as well, after installing bootchart, I get to see the boot-up logo of ubuntu.  Without bootchart, the login box just pops-up.
Well this could be the reason why it's longer. I removed 'xsplash' from my system, it's something graphical fancy that is visualized before and after GDM on Xubuntu, and I gained multiple seconds on my booting :)
Bootchart isn't dependent on any visualization stuff, so try to find out what it is and how you can prevent is from launching.

> **Laibcoms said:**
> So that prompted me to ask this question, does bootchart affects the boot-up time?  Taking my count above, it adds or delays boot-up by 4-5 secs?
Some time, but not multiple seconds. See above.
Good luck!

---

### Post by jay817 on 2010-03-25
[ boot chart]("http://img59.imageshack.us/img59/6869/jamieubuntulucid2010032.png")

edit manged to get it down.

[boot chart ]("http://img682.imageshack.us/img682/6869/jamieubuntulucid2010032.png")

---

### Post by philinux on 2010-03-26
Wow I thought it was quick this morning.

**15.21 seconds.** Thats down from 25 the other day.

---

### Post by baizon on 2010-03-26
30 sec for me :)

[http://img169.imageshack.us/img169/2705/testsystemlucid20100326.png]("http://img169.imageshack.us/img169/2705/testsystemlucid20100326.png")

---

### Post by cecilpierce on 2010-03-26
What can I do to get the time down ? I have 4 lucid installs and they range from one minute to thirty-five secs.

---

### Post by psusi on 2010-03-26
That image is unreadable.

---

### Post by cecilpierce on 2010-03-26
> **psusi said:**
> That image is unreadable.

I know! I can't read it either, how are you people sending the .png file ?

---

### Post by solitaire on 2010-03-26
use a sites like "photobucket.com" or "Imageshack.com" and post the link in your message.

---

### Post by philinux on 2010-03-26
> **cecilpierce said:**
> I know! I can't read it either, how are you people sending the .png file ?

I view the bootchart on the desktop and take a screenshot of the window.

png's are limited to 1024x768, bootcharts are 800x3000 ish.

---

### Post by jaco223 on 2010-03-27
15 seconds here.

---

### Post by dxxvi on 2010-03-28
Mine took 42sec to boot :(

My laptop is the Lenovo SL500 Intel core2duo T6570@2.1GHz 4gig memory, kernel 2.6.32-17-generic-pae, hard disk 160gig 5400rpm. What should I do to make my machine faster (without buying an SSD)? This is what I already did:

- using noatime, nodiratime in /etc/fstab
- removing the splash option from kernel options

As far as I remember, there's a program which re-arranges the order the programs are executed when the machine boots. Do we still need that program in Lucid?

I haven't re-compiled the kernel to enable the Intel core2duo option yet. If anybody did it already, could you share your experience?

Thank you.

---

### Post by farrell on 2010-03-28
> **dxxvi said:**
> Mine took 42sec to boot :(
My laptop is the Lenovo SL500 Intel core2duo T6570@2.1GHz 4gig memory, kernel 2.6.32-17-generic-pae, hard disk 160gig 5400rpm. What should I do to make my machine faster (without buying an SSD)?

Judging by your hardware, something went wrong during your boot. To clear this up, maybe you could install bootchart and post a link to its output here.

Bootchart can be installed by typing:
```
sudo aptitude install bootchart
```After rebooting TWICE, there should be two images in /var/log/bootchart. You could then upload the latest image to [http://imgur.com]("http://imgur.com/"), post the link here and hopefully receive some good advice :)

> - using noatime, nodiratime in /etc/fstabI'm not sure if this produces significant less disk access to boot faster, it does however enlarge the time your disk can stay suspended and thus consuming less power.

> - removing the splash option from kernel optionsThis has actually increased by boot time, maybe because of the verbose output. Your mileage may of course vary...

> As far as I remember, there's a program which re-arranges the order the programs are executed when the machine boots. Do we still need that program in Lucid?I guess you're referring to upstart or ureadahead (re-arranges disk access) - both are highly needed!

> I haven't re-compiled the kernel to enable the Intel core2duo option yet. If anybody did it already, could you share your experience?I haven't done that and i'm curious if this speeds things up, but i tend to think it isn't worth the effort. Btw, how did you end up with 2.6.32-17-generic-pae on a C2D T6570, Ubuntu should have installed linux-image-generic. (PAE for 4GB RAM is on i386 only.)

Good luck with bootchart!

---

### Post by cecilpierce on 2010-03-28
> **cecilpierce said:**
> I know! I can't read it either, how are you people sending the .png file ?

hmmm!

---

### Post by yzarc on 2010-03-28
here's my boot time

[http://www.youtube.com/watch?v=eDb81JqUuHg](http://www.youtube.com/watch?v=eDb81JqUuHg)

30 seconds from grub to totally loaded desktop. nice job (or nice Shuttleworth), although it's a little bit unstable !

my computer has no ssd. it is dual core 2.4 GHz 3.6 GiB of RAM.

---

### Post by garok89 on 2010-03-28
average of 21.6 seconds post-grub....just a shame it take 16 seconds to get to grub

---

### Post by Starks on 2010-03-28
Shouldn't stuff be happening before ureadahead finishes?

[http://imgur.com/ZqZjQ.png](http://imgur.com/ZqZjQ.png)

---

### Post by psusi on 2010-03-28
No, see the sticky on ureadahead.

---

### Post by Omoronovo on 2010-03-28
Please note that this is from within a VM, as I am unable to install Lucid properly (Going to try the newest daily to see if the display issue is fixed).

10.87 seconds, I haven't modified anything.

[http://rapidshare.com/files/369174961/bootchart.png](http://rapidshare.com/files/369174961/bootchart.png)

Can any of you give me tips on how to reduce this further, so that I can really sink my teeth into it after I'm able to get it installed native?

---

### Post by dxxvi on 2010-03-28
Thank you for your willingness to help. [Here is my boot chart.]("http://imgur.com/GLMjS.png")

About the PAE: it was chosen automatically when I installed the Alpha3.

I noticed that there's a program named "sleep" running from the second 10th to the second 13th. Does anybody know what it is?

I don't know how to interpret that chart. Is there any document about the bootchart program?

Thank you.

> **farrell said:**
> Judging by your hardware, something went wrong during your boot. To clear this up, maybe you could install bootchart and post a link to its output here.

Bootchart can be installed by typing:
```
sudo aptitude install bootchart
```After rebooting TWICE, there should be two images in /var/log/bootchart. You could then upload the latest image to [http://imgur.com]("http://imgur.com/"), post the link here and hopefully receive some good advice :)

I'm not sure if this produces significant less disk access to boot faster, it does however enlarge the time your disk can stay suspended and thus consuming less power.

This has actually increased by boot time, maybe because of the verbose output. Your mileage may of course vary...

I guess you're referring to upstart or ureadahead (re-arranges disk access) - both are highly needed!

I haven't done that and i'm curious if this speeds things up, but i tend to think it isn't worth the effort. Btw, how did you end up with 2.6.32-17-generic-pae on a C2D T6570, Ubuntu should have installed linux-image-generic. (PAE for 4GB RAM is on i386 only.)

Good luck with bootchart!

---

### Post by farrell on 2010-03-28
> About the PAE: it was chosen automatically when I installed the Alpha3.So i guess you installed Ubuntu using the i386 cd, you can also use the [64-bit PC (AMD64) desktop CD]("http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-beta1-desktop-amd64.iso") (link is to beta 1) which might speed up your boot and overall performance.

> I noticed that there's a program named "sleep" running from the second 10th to the second 13th. Does anybody know what it is?sleep delays the execution of a process, so the cpu can perform other tasks. This does not work as intended in your bootchart. I recommend applying all updates or reinstalling from the beta 1 cd. Such behavior is not unusual for alpha-grade software...

Another big thing is that ureadahead seems to be absent and so the disk access time slows everything down. You can install ureadahead (which should be installed already) by typing
```
sudo aptitude install ureadahead
```and you can read what it does with this command (after installing)
```
man ureadahead
```> I don't know how to interpret that chart. Is there any document about the bootchart program?Well, blue is cpu usage, light red is disk access. In general, you would want both bars to be short in width and long in height for a quick boot.

Good luck and have fun!

---

### Post by cpmman on 2010-03-28
This is double my 9.10 time.  I do not know what the waiting times (i.e. periods of no activity) are.  Hope this is the way to post this.


[[PHP][IMG]http://imgur.com/5PIW9.png[/IMG][/PHP]]("http://imgur.com/5PIW9.png")

---

### Post by id_crisis on 2010-03-29
i need to tweak this to get boot time:) Mine is 21 sec:P



Clear pic @  [http://i.imgur.com/5lcIU.png](http://i.imgur.com/5lcIU.png)

---

### Post by Owen.C93 on 2010-03-29
> **id_crisis said:**
> i need to tweak this to get boot time:) Mine is 21 sec:P



Clear pic @  [http://i.imgur.com/5lcIU.png](http://i.imgur.com/5lcIU.png)
I think I'm right in thinking you can uninstall HAL.

---

### Post by Owen.C93 on 2010-03-29
installing -18 kernel dropped my boot by a second. Now about 26 with docky installed. About 1 sec less without it. Not bad at all.

---

### Post by id_crisis on 2010-03-29
Now its 18 sec without removing HAL.:p

---

### Post by Owen.C93 on 2010-03-29
Awesome.

---

### Post by victor9098 on 2010-03-29
With auto-login, 27 sec to my desktop! Not bad :)

[http://farm5.static.flickr.com/4038/4473630675_b2a8b47234_o.png]("http://farm5.static.flickr.com/4038/4473630675_b2a8b47234_o.png")

---

### Post by andrewabc on 2010-03-29
> **victor9098 said:**
> With auto-login, 27 sec to my desktop! Not bad :)

[http://farm5.static.flickr.com/4038/4473630675_b2a8b47234_o.png]("http://farm5.static.flickr.com/4038/4473630675_b2a8b47234_o.png")

Is that an atom? What processor?
Intel cpu 2140 @ 1.6ghz model name: same thing but with (2)
Dual core atom?

---

### Post by victor9098 on 2010-03-29
> **andrewabc said:**
> Is that an atom? What processor?
Intel cpu 2140 @ 1.6ghz model name: same thing but with (2)
Dual core atom?

From Sysinfo:
CPU Genuine Intel(R) CPU            2140  @ 1.60GHz

The bootcharts are from my Compaq Presario SR5109UK desktop

---

### Post by benderbeerman on 2010-03-29
bootchart: [http://yfrog.com/5jbenderlucid201003291p](http://yfrog.com/5jbenderlucid201003291p)
reports 200 sec, actually took almost 20 minutes

---

### Post by ShadowDragon on 2010-03-30
Nice, your disk only works for 18 seconds :) Something is wrong there... I would check the logs if I were you ;)

---

### Post by ikt on 2010-03-30
> **cecilpierce said:**
> hmmm!

guys and girls you need to upload the image to a separate image host in order for us to see the image.

[http://imageshack.us/](http://imageshack.us/)

---

### Post by Omoronovo on 2010-03-30
> **andrewabc said:**
> Is that an atom? What processor?
Intel cpu 2140 @ 1.6ghz model name: same thing but with (2)
Dual core atom?

Pentium dual core E2140 - it's a low powered Core 2 duo with half the cache.

---

### Post by ratcheer on 2010-03-30
I just did a clean install of the Mar 30 daily iso image. Then, I timed several bootups with a watch.

I am getting a consistent **18 seconds** from choosing which kernel to boot until I get the desktop login dialog. Then, after entering my password, it is a consistent **31 seconds** until the desktop is ready to use, with menus and usable controls. So, total time until I can actually use the system is **49 seconds**.

As you can see in my sig, I am not using the latest, hottest hardware.

Tim

---

### Post by petejk on 2010-03-30
I'm getting 52 seconds here. 

Any processes I can easily get rid of to speed this up? Seems like a lot

EDIT: Now 43 secs - rebooted with 2.6.32.18 and ureadahead must have kicked in

[http://i777.photobucket.com/albums/yy54/petejk/Laptop1-lucid-20100330-3-1.png](http://i777.photobucket.com/albums/yy54/petejk/Laptop1-lucid-20100330-3-1.png)

---

### Post by _h_ on 2010-03-30
Did some more tweaking, and I managed to shave off another 3 seconds from my previous 18.xx second boot time down to 15.xx seconds. :3

[http://img185.imageshack.us/img185/3107/daniellaptoplucid201003.png](http://img185.imageshack.us/img185/3107/daniellaptoplucid201003.png)

---

### Post by ShadowDragon on 2010-03-30
So what were the tweaks, ditching compiz?

Try booting with nosplash as option, but keep the quiet option, should make it a bit faster...

---

### Post by MorleyPotter on 2010-03-30
[http://imgur.com/9dJ5w.jpg](http://imgur.com/9dJ5w.jpg)

My Karmic chart for comparison

---

### Post by folgado on 2010-03-30
On my Toshiba NB 200 he boot most of the times in 60 seconds but sometimes he boot in 30 seconds.

---

### Post by Rob2687 on 2010-03-30
17.81 seconds
This machine is pretty ancient by todays standards too.
[http://i43.tinypic.com/16jew5d.png](http://i43.tinypic.com/16jew5d.png)

---

### Post by Owen.C93 on 2010-03-30
I did discover that if you take ten secodn to enter your password at the gdm login screen then that is included in your boot chart. Use auto login for consistent times.

---

### Post by andrewabc on 2010-03-30
> **ratcheer said:**
> I just did a clean install of the Mar 30 daily iso image. Then, I timed several bootups with a watch.

I am getting a consistent **18 seconds** from choosing which kernel to boot until I get the desktop login dialog. Then, after entering my password, it is a consistent **31 seconds** until the desktop is ready to use, with menus and usable controls. So, total time until I can actually use the system is **49 seconds**.

As you can see in my sig, I am not using the latest, hottest hardware.

Tim

Based upon your sig hard drive is biggest slowdown. 80gb, I'm guessing not even sataII? or is it laptop?
Nice video card for older hardware I must say.

---

### Post by The Real Dave on 2010-03-30
A3 was ~17 on my testing machine (3.4Ghz PIV, 440Mb RAM, IDE Hdd).

I'll install bootchart and see what B1 is like :)

---

### Post by ratcheer on 2010-03-30
> **andrewabc said:**
> Based upon your sig hard drive is biggest slowdown. 80gb, I'm guessing not even sataII? or is it laptop?
Nice video card for older hardware I must say.

It is a small form-factor desktop and it was new in late 2004. The original high-performance video card died about a year ago and I bought the current card for $40 from NewEgg. Cheap, but it does a good job.

According to Palimpsest, the disk drive is a Western Digital WD-800JD. After many, many hours of use, its SMART status is Healthy.

Tim

---

### Post by Omoronovo on 2010-03-30
Since I finally managed to get Lucid installed "native" instead of running through a VM, I can finally add a comparable bootchart to the thread.

My old one was 10.87 seconds over a VM, and my native one is currently at 8.53 seconds. 
This is without any modifications whatsoever, I have auto-login disabled, and HAL is still installed and starting with the system.

```
New chart: [http://rs680tg.rapidshare.com/files/370122764/novo-lucid-20100330-2.png](http://rs680tg.rapidshare.com/files/370122764/novo-lucid-20100330-2.png) 
Old Chart: [http://rs874tl4.rapidshare.com/files/369174961/bootchart.png](http://rs874tl4.rapidshare.com/files/369174961/bootchart.png)
```

> Did some more tweaking, and I managed to shave off another 3 seconds from my previous 18.xx second boot time down to 15.xx seconds. :3

[http://img185.imageshack.us/img185/3107/daniellaptoplucid201003.png](http://img185.imageshack.us/img185/3107/daniellaptoplucid201003.png)

I'd be really interested to find out exactly what you removed to get the speed up - from what I can tell between my (untouched) install and your modified one, your bootchart seems to be less than half the size.

---

### Post by folgado on 2010-03-31
> **folgado said:**
> On my Toshiba NB 200 he boot most of the times in 60 seconds but sometimes he boot in 30 seconds.

I have edited the grub. Removed noquietsplash and now he boots in 30 seconds.

---

### Post by seamuso on 2010-03-31
ionitx-f-e default install 15.47 seconds lucid x86_64

[lucid_boot.png](http://info.bluefrogcs.com/images/lucid_boot.png)

System -

ionitx-f-e @ 2.0ghz
4GB DDR2 800
WD Blue 500GB SATA

---

### Post by djchandler on 2010-04-03
Boot is now a bit slower than with previous kernel and Plymouth. Splashscreen garbled--getting the right background but logo and dots are a bunch of multi-colored tiny dots at the top of the screen. Probably that is a graphics driver problem. Now running proprietary ATI where I was running the OS Xorg Radeon driver before. Too many changes simultaneously for me to ferret out the culprit. Proprietary fglrx driver is better (faster) with streaming video and 3D stuff. Only problem (if it is the culprit) is the boot splash.

Boot time is up over two seconds from previous post here from 22.63 to 24.89.

[Here's the latest]("http://djchandler.files.wordpress.com/2010/04/lapbuntu-lucid-20100403-1.png").

---

### Post by dusdus on 2010-04-03
With kernel 2.6.32-18-generic I have a boottime of 26.40 seconds
With kernel 2.6.32-19-generic I have a boottime of 41.87 seconds

Can someone explain me how this is happening? I simply don't understand.
And does anyone have some tips? I mean, does my bootchart look fine?

I have uploaded my bootcharts

-18:
[http://img97.imageshack.us/img97/616/263218.png](http://img97.imageshack.us/img97/616/263218.png)

-19
[http://img532.imageshack.us/img532/6303/263219a.png](http://img532.imageshack.us/img532/6303/263219a.png)

Oh my... I rebooted again in -19 and its 23 seconds now!!
[http://img101.imageshack.us/img101/976/laptuxlucid201004034.png](http://img101.imageshack.us/img101/976/laptuxlucid201004034.png)

Still wondering why though :P

---

### Post by dusdus on 2010-04-03
btw, is it safe to just 
```

sudo apt-get remove hal

```
?
:)

---

### Post by Erlander on 2010-04-04
On my very old Athlon 3200+ 32 bit machine with an old 80 GB IDE hard drive and Lucid Lynx as a clean install I'm getting 00.32.11.

My main machine (Specs below) with Karmic 9.10 64 bit upgraded from 9.04 is only giving 1.15.71

Old upgraded install? or is all the difference in Lucid?

---

### Post by cimh on 2010-04-04
I agree that Lucid is fast (20 secs from switch on to desktop on my ssd powered eee. This includes 6s to grub.)

BUT. I will be very surprised if the team can reach their 10s goal on a dell mini ssd by sticking with gnome.

Looking at their daily boot charts:
[http://people.canonical.com/~scott/daily-bootcharts/](http://people.canonical.com/~scott/daily-bootcharts/)

They have levelled out at 17s. The desktop taking up about 10s of that. Their target is to reduce this from 10 to 4s. I'm a total ignoramus when it come to what's under the bonnet (hood) but I just cant see how gnome can be made to boot so quickly - if it could, would it not take away much of the raison d'etre of smaller dms such as lxde, xfce flux etc?


cimh
eee901, lucid gnome & lucid lxde

---

### Post by QwUo173Hy on 2010-04-04
Does this thread get actual developer attention, or is it just for our own purposes?

---

### Post by Orographic on 2010-04-04
45 seconds from power up to workable desktop in Lucid. 35 seconds was the time in Karmic. 

I get quite a long delay once the desktop background comes up in Lucid before I can see all of the menus - about 30 seconds. It was 20 seconds until the latest updates.

Gigabyte 945GZM-S2 board with E4300 CPU with intel onboard graphics that works perfectly in Karmic.

---

### Post by tommynz1975 on 2010-04-05
This is my boot chart
40.40 sec's
on a standard install without changing anything.
I honestly thought it was booting faster than that, wishful thinking I guess

[http://imgur.com/HnFAk.png](http://imgur.com/HnFAk.png)

---

### Post by Owen.C93 on 2010-04-05
> **tommynz1975 said:**
> This is my boot chart
40.40 sec's
on a standard install without changing anything.
I honestly thought it was booting faster than that, wishful thinking I guess

[http://imgur.com/HnFAk.png](http://imgur.com/HnFAk.png)
Uninstall HAL.

---

### Post by QwUo173Hy on 2010-04-05
45 secs. No nice boot either.
[http://dl.dropbox.com/u/464104/jarlath-laptop-lucid-20100405-1.png](http://dl.dropbox.com/u/464104/jarlath-laptop-lucid-20100405-1.png)

---

### Post by seamuso on 2010-04-05
Desktop boot - 18.45s

[Desktop bootchart](http://info.bluefrogcs.com/images/desktop_boot.png)

142MB/s is my raid5 activating and mounting (storage drive, not OS drive) .. OS drive (with raid5 removed from fstab) 75-80MB/s

---

### Post by Owen.C93 on 2010-04-05
HOLY CRAP, just deleted the ureadahead pack files to force a reprofile, boot down from 27sec, to 19sec!!!!!

Not bad for a two year old 5400rpm laptop hardrive! 

[http://img405.imageshack.us/img405/4232/owenclucid2010040611.png](http://img405.imageshack.us/img405/4232/owenclucid2010040611.png)

---

### Post by QwUo173Hy on 2010-04-05
> **Owen.C93 said:**
> HOLY CRAP, just deleted the ureadahead pack files to force a reprofile, boot down from 27sec, to 19sec!!!!!

How'd it go on the second boot? [https://bugs.launchpad.net/ureadahead/+bug/491956](https://bugs.launchpad.net/ureadahead/+bug/491956)

---

### Post by Owen.C93 on 2010-04-06
> **jarlath said:**
> How'd it go on the second boot? [https://bugs.launchpad.net/ureadahead/+bug/491956](https://bugs.launchpad.net/ureadahead/+bug/491956)
5 boots later all in between 19 and 20 sec. However I now think it's because I removed preload, when I reinstall it I'm back up to 26 seconds and back down to 19 when I get rid of it.

---

### Post by xir_ on 2010-04-06
> **Owen.C93 said:**
> 5 boots later all in between 19 and 20 sec. However I now think it's because I removed preload, when I reinstall it I'm back up to 26 seconds and back down to 19 when I get rid of it.

preload will cause slow boots in combination with ureadahead.

---

### Post by Owen.C93 on 2010-04-06
> **xir_ said:**
> preload will cause slow boots in combination with ureadahead.
I didn't know this..hmm I couldn't find a bug either. Was this our experience or something that has already been highlighted many times but I missed?

---

### Post by Speque on 2010-04-06
Bootchart measures the time from grub to login screen, am I right? My machine does that part quite quickly, but the time from login to fully loaded desktop takes quite a long time. Any ways to analyse that?

---

### Post by jontxo on 2010-04-06
Hello

My system is ubuntu lucid amd64. I have tried to get images of the boot time and in the folder where the images are stored no image have been created, only two tgz files. 

I have created a bug report: [https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/556704](https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/556704)

I don't know if there is something more I could do in order to fix this. 

Thanks

---

### Post by ranch hand on 2010-04-06
I have 7 variations of 10.04-64 on one drive.  On one bootchart has never worked except once since last November.  On one it works all the time.  The others are in between those extremes.

Good luck with the bug.  You seem to have the bug marked as "private".  If you change that to "public" others could join it on the fun and they may pay attention to it.  There needs to be confirmation from other users that it really is a bug.

I think it is just an unreliable app.

---

### Post by jontxo on 2010-04-06
Hello

Thanks for the answer. I have changed the bug to public. Let's see if it helps to fix the bug.

Greetings.

---

### Post by Korcia on 2010-04-06
This is my bootchart. I can't believe the huge regression comparing the boot time with jaunty. 
Ubuntu 9.04 (big development environment, LVM, 2 DB posgres, mysql, and a long etc..): boot time -> 13.54 seconds.

At first I did a fresh install with LVM, nvidia drivers, I mean, the exact configuration I had with jaunty and the boot time was 51 seconds. After this great surprise I did a new installation without LVM and with nouveau drivers and the result was:

Ubuntu 10.04 (fresh installation, just one DB and nothing else) boot time-> 32.11 seconds 237% MORE!!!!!!

I do not understand anything. People are getting very excited with new features: ubuntu music store, memenu, twitter integration, new buttons, etc, etc. Those should not be the priorites of an operating system. Those are irrelevant aesthetics for teenagers use.
How about a gwibber-service that is running even though many professionals do not care about gwibber. Ahh, but there is no way to find the gwibber service in a sysconfig-like or sysv-rc-conf. No. You have to go to terminal and to kill it. 

I'm going back to jaunty and in the meantime, with sadness, I'll try to get a feeling of other distros.

---

### Post by Owen.C93 on 2010-04-06
> **Korcia said:**
> This is my bootchart. I can't believe the huge regression comparing the boot time with jaunty. 
Ubuntu 9.04 (big development environment, LVM, 2 DB posgres, mysql, and a long etc..): boot time -> 13.54 seconds.

At first I did a fresh install with LVM, nvidia drivers, I mean, the exact configuration I had with jaunty and the boot time was 51 seconds. After this great surprise I did a new installation without LVM and with nouveau drivers and the result was:

Ubuntu 10.04 (fresh installation, just one DB and nothing else) boot time-> 32.11 seconds 237% MORE!!!!!!

I do not understand anything. People are getting very excited with new features: ubuntu music store, memenu, twitter integration, new buttons, etc, etc. Those should not be the priorites of an operating system. Those are irrelevant aesthetics for teenagers use.
How about a gwibber-service that is running even though many professionals do not care about gwibber. Ahh, but there is no way to find the gwibber service in a sysconfig-like or sysv-rc-conf. No. You have to go to terminal and to kill it. 

I'm going back to jaunty and in the meantime, with sadness, I'll try to get a feeling of other distros.
  Couldyou upload the image to imageshack so we can see it full size please :)
It looks like ureadahead isn't working though.

---

### Post by jmmL on 2010-04-06
> **Korcia said:**
> This is my bootchart. I can't believe the huge regression comparing the boot time with jaunty. 
Ubuntu 9.04 (big development environment, LVM, 2 DB posgres, mysql, and a long etc..): boot time -> 13.54 seconds.



If I was a betting man I would put money on that 14 seconds being the time taken to load the kernel. Since lucid the time reported by bootchart is the time taken to load the kernel and the rest of the desktop, giving a better impression of the total "boot" time. The time-to-desktop will obviously be longer than the time taken to load just the kernel.

---

### Post by recluce on 2010-04-06
I have a 25.74 second boot time with Lucid on my Dell Latitude D830 notebook with a Seagate 7200rpm 320GB drive. Not too shabby for a notebook without SSD! :P

[http://img202.imageshack.us/img202/4517/ellegon3ubuntutestlucid.png](http://img202.imageshack.us/img202/4517/ellegon3ubuntutestlucid.png)

---

### Post by cariboo on 2010-04-06
> **Korcia said:**
> This is my bootchart. I can't believe the huge regression comparing the boot time with jaunty. 
Ubuntu 9.04 (big development environment, LVM, 2 DB posgres, mysql, and a long etc..): boot time -> 13.54 seconds.



If I remember correctly bootchart in Jaunty only measured the time from Grub to GDM, where now it charts the time from Grub to usable desktop. There were a lot of people complaining when Karmic came out because of the 45 second pause added to the chart from Grub to Desktop.

---

### Post by artcarney on 2010-04-06
Here's mine.

Ubuntu is on an external USB hard drive so a bit over 56 seconds to a working desktop (automatic login) with default services starting up is not too bad ...

---

### Post by jontxo on 2010-04-07
Hello

I have discovered how to get the bootcharts. In order to get the png images the following change has to be made in one of the pybootchartgui package file that is in your computer:

The file that has to be modified is: 

/usr/share/pyshared/pybootchartgui/draw.py 

At the line 103 (in my system)

100	100		
101	101		# Convert ps process state to an int
102	102		def get_proc_state(flag):
103	-		return "RSDTZXW".index(flag) + 1
103	+		return "RSDTZXW".find(flag) + 1
104	104		
105	105		
106	106		def draw_text(ctx, text, color, x, y):
...			


This is the page where I have get the information: 

[http://code.google.com/p/pybootchartgui/source/detail?r=140](http://code.google.com/p/pybootchartgui/source/detail?r=140)

I have found this because the error with bootchart program has been marked as a duplicate of error 512172

[https://bugs.launchpad.net/bugs/512172](https://bugs.launchpad.net/bugs/512172)

Once the change in the file is posted you can get the bootcharts with the following command:


bootchart -f png -o path_and_name_of_the_png_image.png /var/log/bootchart/file_with_the_information_to_create_the_bootchart.tgz 

The images still don't appear in the system log viewer.

Greetings.

---

### Post by ranch hand on 2010-04-07
I have a clock with a second hand.  Works like a charm with any install of any distro.

Universal compatibility.  Easy to understand UI.

---

### Post by xir_ on 2010-04-07
> **Owen.C93 said:**
> I didn't know this..hmm I couldn't find a bug either. Was this our experience or something that has already been highlighted many times but I missed?

I have had this as an issue.

I suppose its logical. Preload moves common things into ram and ureadahead profiles things moved into ram at boot in order to speed things up. So when you preaload with ureadahead you end up with applications being loaded into ram that have nothing to do with boot up, thus slowing it down.

---

### Post by xir_ on 2010-04-07
> **ranch hand said:**
> I have a clock with a second hand.  Works like a charm with any install of any distro.

Universal compatibility.  Easy to understand UI.

better not be proprietary or you are going to get sooooo flamed...

---

### Post by artcarney on 2010-04-07
Hmmm, I'm new to this fastboot stuff, I should have read more before posting last night.

That initial post was after the first boot with bootchart installed.

I turned off a couple of services/boot items through BUM that I didn't want or need and now my boot time is in the 35 second range.

Hardware is an HP Pavilion dv6000 laptop with 2 gigs ram, Ubuntu is on an external Western Digital USB hard drive.

Here's mine. If anyone has any suggestions on how I can get a better boot time with this hardware I'd be willing to try. Certain services such as bluetooth are a necessity so I can't disable them.

[bootchart]("http://i586.photobucket.com/albums/ss305/artcarney/david-laptop-lucid-20100407-3.png")

---

### Post by Owen.C93 on 2010-04-07
> **artcarney said:**
> Hmmm, I'm new to this fastboot stuff, I should have read more before posting last night.

That initial post was after the first boot with bootchart installed.

I turned off a couple of services/boot items through BUM that I didn't want or need and now my boot time is in the 35 second range.

Hardware is an HP Pavilion dv6000 laptop with 2 gigs ram, Ubuntu is on an external Western Digital USB hard drive.

Here's mine. If anyone has any suggestions on how I can get a better boot time with this hardware I'd be willing to try. Certain services such as bluetooth are a necessity so I can't disable them.

[bootchart]("http://i586.photobucket.com/albums/ss305/artcarney/david-laptop-lucid-20100407-3.png")
Could you upload to imageshack so we can see it fullsize please :D

---

### Post by artcarney on 2010-04-07
> **Owen.C93 said:**
> Could you upload to imageshack so we can see it fullsize please :D

Not sure what imageshack will do over photobucket but I'll try. Waiting on the confirmation email now ...

---

### Post by Owen.C93 on 2010-04-07
> **artcarney said:**
> Not sure what imageshack will do over photobucket but I'll try. Waiting on the confirmation email now ...
I seems to keep it full size instead of downsizing it. I couldn't read the one you posted on photobucket. I don't know why it does that.

---

### Post by artcarney on 2010-04-07
> **Owen.C93 said:**
> I seems to keep it full size instead of downsizing it. I couldn't read the one you posted on photobucket. I don't know why it does that.

Try [this]("http://img202.imageshack.us/img202/9479/davidlaptoplucid2010040.png").

Dang, you're right about it keeping it full sized!

---

### Post by Owen.C93 on 2010-04-07
> **artcarney said:**
> Try [this]("http://img202.imageshack.us/img202/9479/davidlaptoplucid2010040.png").

Dang, you're right about it keeping it full sized!
That's better. Umm you can remove HAL which might help a little. But your hardrive throughput is pretty low so the boot time is quite good as it is :)

---

### Post by artcarney on 2010-04-07
> **Owen.C93 said:**
> That's better. Umm you can remove HAL which might help a little. But your hardrive throughput is pretty low so the boot time is quite good as it is :)

Removed HAL and rebooted a couple of times. [This]("http://img528.imageshack.us/i/davidlaptoplucid2010040.png/") is the last reboot.

Consistently under 35 seconds, not bad for an old WD USB external hard drive.

Edit: Reinstalled HAL as k9copy would not work without it.

---

### Post by jontxo on 2010-04-07
Without hal k3b doesn't work. I don't know but perhaps there are more programs that have problems without hal.

---

### Post by tommynz1975 on 2010-04-07
[I]Hi People 
This is my boot chart posted 2 days ago.

40.40 sec's 
on a standard install without changing anything. 
I honestly thought it was booting faster than that, wishful thinking I  guess 
 
[http://imgur.com/HnFAk.png](http://imgur.com/HnFAk.png)

Today some how the system has shaved almost 10 sec's off that.


Linux 10guitars-desktop 2.6.32-18-generic #27-Ubuntu SMP Fri Mar 26 19:51:10 UTC 2010 i686 GNU/Linux

have uploaded todays charts
before and after installing bum, and removing bluetooth and acpi for laptop.

thurs 12.21pm nzst 34.11 sec
[http://imgur.com/sEWUG.png](http://imgur.com/sEWUG.png)

thurs 12.37pm nzst 31.63 sec
[http://imgur.com/lL5i2.png](http://imgur.com/lL5i2.png)

This system is an NEC Powermate ML7 - q8200

standard install except automatic login, only due to being a test system.

So far loving 10.04

I am looking fwd to my dist-upgrade for beta2
Cheers

Tom
[/I]

---

### Post by linuxman94 on 2010-04-07
Here's mine:
[bootchart]("http://img340.imageshack.us/img340/4387/ubuntubasementlucid2010.png")

That was on a restart, not a cold boot. 32 seconds is pretty good.

Here is today's:
[bootchart]("http://img405.imageshack.us/img405/4387/ubuntubasementlucid2010.png")

Shaved off three seconds from yesterday.

It is an old computer. MSI MS-6390 mobo, AMD Athlon XP 1800+, nVidia Geforce FX 5500

---

### Post by siren09 on 2010-04-08
I am seeing 10-12 seconds boot time to usable desktop state for a clean install of the Netbook Remix version on my Intel Atom based Shuttle netbook with Lucid beta 1 and a 32GB SSD.  Very impressive.

My mythtv server, which is Q6400 based, also has an SSD system disk, but was an upgrade from 9.10, boots much slower (more like 30 secs).  Is a clean install required for an optimum boot experience, I wonder?

---

### Post by ranch hand on 2010-04-08
No matter what the upgrade fan boys say, a clean install is always a little better.

---

### Post by runesvend on 2010-04-08
My record is around 4.9 seconds so far (with ureadahead turned off). Here it is at 4.89 seconds (Intel X25-M Gen2 80GB).

SSD's rock! :D

[http://imgur.com/twMLm.png]("http://imgur.com/twMLm.png")

**EDIT:** FYI, the worst boot time I've recorded so far has been 6.17s:
[http://imgur.com/AtboZ.png]("http://imgur.com/AtboZ.png")

but average is around 5.5 seconds.

---

### Post by Owen.C93 on 2010-04-08
> **linuxman94 said:**
> Here's mine:
[bootchart]("http://img340.imageshack.us/img340/4387/ubuntubasementlucid2010.png")

That was on a restart, not a cold boot. 32 seconds is pretty good.
Your ureadahead seems to continue throughout boot. Does it do this every time?

---

### Post by cariboo on 2010-04-08
This is my office system, that was upgraded from Karmic to Lucid, It's not quite as fast as my home system, but I'm quite happy with the results.

This system has the same motherboard as my home system, a slower processor. slower ram and a GT210 video card.

[[IMG]http://imgur.com/rwmaZs.jpg[/IMG]](http://imgur.com/rwmaZ.png)

---

### Post by jontxo on 2010-04-08
I have reinstalled the system and now everything works ok. 

[IMG]http://imgur.com/M4ay6.png[/IMG]

---

### Post by null_pointer_us on 2010-04-08
14.99s on Virtual Box 3.1.6 (495 MB/sec. peak disk throughput)

3.0 GHz C2D
P35+ICH9 System Board
7200 rpm HDD

[[IMG]http://img704.imageshack.us/img704/2641/michaelvboxubuntulucid2.th.png[/IMG]](http://img704.imageshack.us/i/michaelvboxubuntulucid2.png/)

LOL, it took me a little while to realize what was happening. The host is caching the important parts of virtual drive image in memory, hence the huge virtual disk throughput numbers.

Even so, Lucid shaved about 10 sec. off my Karmic boot times in same setup.

---

### Post by linuxman94 on 2010-04-08
> **Owen.C93 said:**
> Your ureadahead seems to continue throughout boot. Does it do this every time?

It didn't do it today.

---

### Post by ghindo on 2010-04-08
[http://img682.imageshack.us/img682/761/gibsonlucid201004085.png](http://img682.imageshack.us/img682/761/gibsonlucid201004085.png)

Upgrade from 9.10 to 10.04.  Recently removed HAL and reprofiled ureadahead.  No autologin for security reasons.

Fairly modern machine (Core2Duo, 2GB RAM, SATA drive).

35.45 seconds.  I feel I can do better.  Any suggestions?

---

### Post by jmmL on 2010-04-08
> **ghindo said:**
> [http://img682.imageshack.us/img682/761/gibsonlucid201004085.png](http://img682.imageshack.us/img682/761/gibsonlucid201004085.png)

Upgrade from 9.10 to 10.04.  Recently removed HAL and reprofiled ureadahead.  No autologin for security reasons.

Fairly modern machine (Core2Duo, 2GB RAM, SATA drive).

35.45 seconds.  I feel I can do better.  Any suggestions?

You should be able to do better on your next boot. ureadahead was profiling on that boot, so on the next one you should get its full effect. I reckon that should shave at least 5 seconds off, if not 10 or more.

---

### Post by ranch hand on 2010-04-08
I am on a similar box (see sig) and the installs that boot well for me are doing just slightly better (I do not use auto login either - just gives me the willies) at around 30 seconds on an external usb drive (WD 7200rpm).

That seems like a very reasonable boot time to me.  If plymouth starts working right it may speed up some.

---

### Post by randomizer101 on 2010-04-09
[[IMG]http://i176.photobucket.com/albums/w179/random1301/th_bootchart-lucid.png[/IMG]](http://i176.photobucket.com/albums/w179/random1301/bootchart-lucid.png)
(clickable thumbnail)

7.33 seconds in a VM loading from a Western Digital Caviar Black. I certainly hope a "proper" installation is that fast, Win 7 boots off my SSD in at least double that time (admittedly with alot more loading).

EDIT: Subsequent boot times have been 11.32s and even 5.74s (!). I don't know if VB does some sort of caching, but the latter boot time should be impossible for a HDD.

---

### Post by perrantrevan on 2010-04-09
Running beta 1 + updates. Dell Studio XPS 13 with Nvidia and 500G 5400RPM HDD.

Lately there have been no updates to kernel, mountall or ureadahead but my boot times have varied between 19 and 35 seconds. Unfortunately, they are mostly around 35 seconds. It's frustrating to know that a faster boot is possible but rarely happens!

The culprit seems to be something to do with ureadahead.

On a good boot, it takes about 10 seconds of the overall time. On a bad boot it takes more like 20 seconds.

I have tried deleting the pack files but this does not help. Actually, when reprofiling, the boot from GRUB2 to login is faster than with ureadahead!

Is there anyone out there with a similar experience?

---

### Post by Owen.C93 on 2010-04-09
When I had auto login disabled the time I took to enter my password was included in the bootchart time. I suggest for testing the time and benchmarking then try auto login temporarily. Just to see if your login time is included in bootchart.

---

### Post by runesvend on 2010-04-09
> **perrantrevan said:**
> The culprit seems to be something to do with ureadahead.

On a good boot, it takes about 10 seconds of the overall time. On a bad boot it takes more like 20 seconds.

I have tried deleting the pack files but this does not help. Actually, when reprofiling, the boot from GRUB2 to login is faster than with ureadahead!

Is there anyone out there with a similar experience?
To find out if it *is* ureadahead that is slowing you down, follow Scott James Remnant's instructions under "**ureadahead slows down my boot!**" in his thread here: [http://ubuntuforums.org/showthread.php?t=1434502]("http://ubuntuforums.org/showthread.php?t=1434502")

---

### Post by null_pointer_us on 2010-04-09
I'm down 2 sec. to 12.75s now, with the latest updates (an optimized startup script?).

[[IMG]http://imgur.com/p9qdgs.jpg[/IMG]](http://imgur.com/p9qdg.png)

---

### Post by perrantrevan on 2010-04-09
> **runesvend said:**
> To find out if it *is* ureadahead that is slowing you down, follow Scott James Remnant's instructions under "**ureadahead slows down my boot!**" in his thread here: [http://ubuntuforums.org/showthread.php?t=1434502]("http://ubuntuforums.org/showthread.php?t=1434502")

I did that before posting here. I found a similar bug on launchpad and added my bootcharts (without ureadahead, during reprofiling, with ureadahead) and a ureadahead dump file. 

The next thing that happened was that all bugs for ureadahead were deleted and it is not possible to post new ones. Not very encouraging!

During the time I have been frustrated with my boot times, ureadahead has not been updated. However, it must be what data ureadahead saves for other processes, how it uses this, or where it is on the HDD that causes the problem.

IIRC updates to winbind and samba packages yielded a 10 second saving on boot times. However, updating KDE packages yesterday have now increased it again by 10 seconds.

---

### Post by Owen.C93 on 2010-04-09
> **perrantrevan said:**
> I did that before posting here. I found a similar bug on launchpad and added my bootcharts (without ureadahead, during reprofiling, with ureadahead) and a ureadahead dump file. 

The next thing that happened was that all bugs for ureadahead were deleted and it is not possible to post new ones. Not very encouraging!

During the time I have been frustrated with my boot times, ureadahead has not been updated. However, it must be what data ureadahead saves for other processes, how it uses this, or where it is on the HDD that causes the problem.

IIRC updates to winbind and samba packages yielded a 10 second saving on boot times. However, updating KDE packages yesterday have now increased it again by 10 seconds.
Are you sure the bug wasn't just set to private?

---

### Post by perrantrevan on 2010-04-09
[https://launchpad.net/ureadahead](https://launchpad.net/ureadahead)


"über-readahead does not use Launchpad for bug tracking."

However, it seems that I can now look at/report bugs at: -

[https://bugs.launchpad.net/ubuntu/+source/ureadahead](https://bugs.launchpad.net/ubuntu/+source/ureadahead)

---

### Post by runesvend on 2010-04-09
I'm down to 4.16 seconds with a fresh install:
[http://imgur.com/Iwyr6.png]("http://imgur.com/Iwyr6.png")

---

### Post by cariboo on 2010-04-09
> **perrantrevan said:**
> [https://launchpad.net/ureadahead](https://launchpad.net/ureadahead)


"über-readahead does not use Launchpad for bug tracking."

However, it seems that I can now look at/report bugs at: -

[https://bugs.launchpad.net/ubuntu/+source/ureadahead](https://bugs.launchpad.net/ubuntu/+source/ureadahead)

What's the bug #?

---

### Post by perrantrevan on 2010-04-09
I've now added some bootcharts and ureadahead dump to bug 552165

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/552165](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/552165)

---

### Post by tazd on 2010-04-10
Here's my boot chart from a dell inspirion 1721

[http://i41.tinypic.com/141jcja.png]("http://i41.tinypic.com/141jcja.png")

---

### Post by JoelThomas on 2010-04-12
Boot time is about 60 seconds for me, which isn't too bad, but it looks like I might be able to cut that down quite a bit if Xorg wasn't spinning the CPU for 30 seconds.  

Any ideas how I might be able to cut that down?

Here's my [**Bootchart**](http://img291.imageshack.us/i/jltdelli1520lucid201004.png/)

(Dell Inspiron 1520 upgraded to 10.04 from 9.10)

---

### Post by Sennaista on 2010-04-12
With automatic login it take around 19s for me.

---

### Post by ranch hand on 2010-04-12
Best time yet (password login) 26.63 seconds.  Plymouth disabled on this (one of the throw aways) install.

---

### Post by _h_ on 2010-04-12
> **JoelThomas said:**
> Boot time is about 60 seconds for me, which isn't too bad, but it looks like I might be able to cut that down quite a bit if Xorg wasn't spinning the CPU for 30 seconds.  

Any ideas how I might be able to cut that down?

Here's my [**Bootchart**]("http://img291.imageshack.us/i/jltdelli1520lucid201004.png/")

(Dell Inspiron 1520 upgraded to 10.04 from 9.10)

You might want to look into what is causing Xorg to cycle your CPU that hard, it doesn't look normal at all.

---

### Post by Calash on 2010-04-12
[[IMG]http://www.necrotania.com/vb/picture.php?albumid=42&pictureid=317&thumb=1[/IMG]](http://www.necrotania.com/vb/picture.php?albumid=42&pictureid=317)


26.21 on my 3.4g Pentium.  This is after a reload and includes some fstab mounting to a 1tb NAS.  In all I can not complain.

---

### Post by Owen.C93 on 2010-04-13
> **Calash said:**
> 


26.21 on my 3.4g Pentium.  This is after a reload and includes some fstab mounting to a 1tb NAS.  In all I can not complain.
What happens when you boot a second time? It looks like ureadahead was profiling:)

---

### Post by Calash on 2010-04-13
> **Owen.C93 said:**
> What happens when you boot a second time? It looks like ureadahead was profiling:)

22.27 this past boot.  Over the past 2 boots I have gained a steady 4 seconds on the first post.


Oddly the first screenshot I posted was my third boot after doing a reload and getting everything up to date.  I did not realize that the profiling could take so long.

[[IMG]http://www.necrotania.com/vb/picture.php?albumid=42&pictureid=318&thumb=1[/IMG]](http://www.necrotania.com/vb/picture.php?albumid=42&pictureid=318)

---

### Post by linusr on 2010-04-13
My laptop has some issues transistioning from gdm to desktop...
For 2GB ram, Core 2 duo machine 40-50 sec slow or normal?

---

### Post by seamuso on 2010-04-13
[[color=red]Getting faster[/color]](http://info.bluefrogcs.com/images/big-blue-lucid-20100413-10.png)

15.35s

---

### Post by tunin on 2010-04-14
Just updated to the -20 kernel.  20.99 on first boot, 15.15 on second according to bootchart.

---

### Post by vade on 2010-04-14
Getting below 5 seconds with an ssd :guitar:

[[IMG]http://img535.imageshack.us/img535/5043/vpclucid201004142.th.png[/IMG]](http://img535.imageshack.us/i/vpclucid201004142.png/)

---

### Post by ShadowDragon on 2010-04-14
One of the benefits of having an SSD indeed. :)

If I may ask, the first 2 seconds of your boot, what is your system doing then? I understand that since the collector isn't running, it looks like it's idling, but I sure hope it isn't, since it would be a bit stupid if almost half of your boot time would be just idling... So what is your system doing during those first 2 seconds?

---

### Post by vade on 2010-04-14
I presume it's waiting for hardware. Here's my kern.log: [http://pastebin.com/2asmETsR]("http://pastebin.com/2asmETsR")

---

### Post by ShadowDragon on 2010-04-14
You could be right, your Intel 40GB is only processed after 1.6 sec. Thanks for reply. :)

---

### Post by madsc89 on 2010-04-14
Running on a 1st gen intel X25-M 80 GB.

Did some partiton aligning, noop, noatime. No other tweaks.

[[IMG]http://img143.imageshack.us/img143/9461/madslaptoplucid20100414n.png[/IMG]](http://img143.imageshack.us/i/madslaptoplucid20100414n.png/)

EDIT: Do anyone see a relative easy way to boost it up a little? It's better than Final release 9.10, but slower than early beta 9.10.

---

### Post by His on 2010-04-14
33.75 Secs. I suppose I'm happy with that.

[http://j.imagehost.org/view/0269/spidersense-lucid-20100414-1]("http://j.imagehost.org/view/0269/spidersense-lucid-20100414-1")

---

### Post by julianb on 2010-04-14
> **linusr said:**
> My laptop has some issues transistioning from gdm to desktop...
For 2GB ram, Core 2 duo machine 40-50 sec slow or normal?

Slow, I'd say. My cheap Asus netbooks are faster using 10.04beta1 and 10.04beta2. 

Given the same OS and the same settings, the hard disk speed is the main factor in how fast you boot.

---

### Post by vade on 2010-04-15
3.14 seconds using 2.6.32-22-preempt and noop scheduler for the ssd. :)

[[IMG]http://img219.imageshack.us/img219/7493/vpclucid2010041511c.th.png[/IMG]](http://img219.imageshack.us/i/vpclucid2010041511c.png/)

---

### Post by His on 2010-04-15
> **vade said:**
> 3.14 seconds using 2.6.32-22-preempt and noop scheduler for the ssd. :)


ftw!

---

### Post by ghindo on 2010-04-15
[http://img145.imageshack.us/img145/6962/gibsonlucid201004152.png](http://img145.imageshack.us/img145/6962/gibsonlucid201004152.png)

About 35 seconds.  I went to go delete the pack files for ureadahead to try to speed up boot, but /var/lib/ureadahead/ doesn't seem to have any pack files :?

Very odd.

---

### Post by Miguel on 2010-04-15
ghindo, it's possible that some of the updates you've installed since your last boot are related to the boot process. In such cases, I believe it's normal that your pack files have been deleted and that a new profile will be performed on next boot.

---

### Post by uid313 on 2010-04-16
> **vade said:**
> 3.14 seconds using 2.6.32-22-preempt and noop scheduler for the ssd. :)

What time do you get without the -preempt kernel?
Why use the -preempt kernel? Does it boot faster?

What time do you get without the noop scheduler?
Is it faster?

What SSD do you got?

---

### Post by salva84 on 2010-04-16
[IMG]http://xs.to/image-B989_4BC89224.jpg[/IMG]

---

### Post by julianb on 2010-04-16
> 3.14 seconds using 2.6.32-22-preempt and noop scheduler for the ssd. 

Betcha in two years (Ubuntu 12.04), half the machines running Ubuntu will be starting this quickly... & most of the rest will start in less than 10 seconds.

---

### Post by Cavsfan on 2010-04-16
I am kind of confused - I am dual booting and have to move the cursor and hit enter.
Then when booting up every time it goes through some sort of disk check although it's fairly fast. 
Then I have to login. Does these interventions factor in as well?

[[IMG]http://img691.imageshack.us/img691/7452/cavsfandesktoplucid2010.png[/IMG]]("http://img691.imageshack.us/i/cavsfandesktoplucid2010.png/")

---

### Post by vade on 2010-04-19
> **uid313 said:**
> What time do you get without the -preempt kernel?
Why use the -preempt kernel? Does it boot faster?

What time do you get without the noop scheduler?
Is it faster?

What SSD do you got?
-preempt kernel seems to initialize nearly a second faster than non-preempt on my machine. There's always some variation to the time it takes to init cpu, though.

The default cfq scheduler adds nearly a second to boot time in contrast to using the noop scheduler.

I have the intel x25-v 40GB ssd using firmware version 02hd.

---

### Post by wbar2 on 2010-04-21
Over 40 seconds... my desktop does much better!

[[IMG]http://imgur.com/IcWrrs.jpg[/IMG]](http://imgur.com/IcWrr.png)

---

### Post by Cavsfan on 2010-04-21
Better than last time, but there was a long pause at the beginning.

[[IMG]http://img695.imageshack.us/img695/7452/cavsfandesktoplucid2010.png[/IMG]]("http://img695.imageshack.us/i/cavsfandesktoplucid2010.png/")

---

### Post by Cavsfan on 2010-04-21
> **ghindo said:**
> [http://img145.imageshack.us/img145/6962/gibsonlucid201004152.png](http://img145.imageshack.us/img145/6962/gibsonlucid201004152.png)

About 35 seconds.  I went to go delete the pack files for ureadahead to try to speed up boot, but /var/lib/ureadahead/ doesn't seem to have any pack files :?

Very odd.


nvm, my system is already fast enough for me! :)

Thanks

---

### Post by ankspo71 on 2010-04-21
Kubuntu Lucid beta 2 + Pentium4 3.0 = 34.10 seconds.
[[IMG]http://img121.imageshack.us/img121/1157/kubuntulucid201004213.th.png[/IMG]](http://img121.imageshack.us/i/kubuntulucid201004213.png/)

---

### Post by wbar2 on 2010-04-22
Somehow after rebooting once (without changing anything), I get around 25 seconds instead of 40. Much better!

[[IMG]http://img62.imageshack.us/img62/3180/weslaptoplucid201004221.th.png[/IMG]](http://img62.imageshack.us/i/weslaptoplucid201004221.png/)

---

### Post by Slorg on 2010-04-22
Here are my system requirements:

Pentium 4: 2.6GHz (Single core)
1GB Memory (DDR333MHz)
160GB IDE Hard Disk (Western Digital)
And some less important stuff..

19s
Not bad for an older computer :)

[http://img215.imageshack.us/img215/2046/sjoerddesktoplucid20100.png](http://img215.imageshack.us/img215/2046/sjoerddesktoplucid20100.png)

EDIT:
Ha, 16 seconds this time:
[http://nl.tinypic.com/r/qsqycn/5](http://nl.tinypic.com/r/qsqycn/5)

---

### Post by ShadowDragon on 2010-04-22
> **wbar2 said:**
> Somehow after rebooting once (without changing anything), I get around 25 seconds instead of 40. Much better!


That's because ureadahead does a reprofile on the boot (the first one) after you installed some stuff. The boot after the reprofile (the second one) you are using the full potential of the generated .pack file of ureadahead.

So guys, try to reboot for a second time and use that bootchart, the one without the profiling.

---

### Post by dangmc on 2010-04-23
I have a new system: dual boot win xp/10.04 amd64 beta2 and from OS selection to desktop complete-21 secs. (not counting P.O.S.T or login).
Needless to say I'm well pleased with 'Lucid' so far.The only real nasty I've found so far is: No microphone! I sure hope this is fixed soon since I use Skype Out.
Seasonic X-650 psu
Asus P7P55D-E mobo
I5-750 2.66ghz.cpu w/Zalman CNPS 9900 heatsink
4ghz G-Skill F3-12800 ddr3 ram
WD caviar black 1tb.hd
dual boot WinXP and Lucid 10.04 amd64 beta 2
BFG GeForce 9800GT graphics card

update: I finally was able to get my microphone working. 
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574504?comments=all](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574504?comments=all)

---

### Post by gthou on 2010-04-23
Cool, my bootchart tells me 9.65s.

---

### Post by mk04 on 2010-04-23
36 seconds to internet connecetion. Minus 1.5sec for me to type in password + clicking on the network manager to click on my network to connect (3sec). Approx. = 30-32sec

Shutdown time approx. 15sec

---

### Post by grandtoubab on 2010-04-23
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic-pae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 (Ubuntu 2.6.32-21.32-generic-pae 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017fd0000 (usable)
[    0.000000]  BIOS-e820: 0000000017fd0000 - 0000000017fdf000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017fdf000 - 0000000018000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x17fd0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF8000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000017fd0000 (usable)
[    0.000000]  modified: 0000000017fd0000 - 0000000017fdf000 (ACPI data)
[    0.000000]  modified: 0000000017fdf000 - 0000000018000000 (ACPI NVS)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000017fd0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0017e00000 page 2M
[    0.000000]  0017e00000 - 0017fd0000 page 4k
[    0.000000] kernel direct mapping tables up to 17fd0000 @ 10000-16000
[    0.000000] RAMDISK: 118b2000 - 1201b76e
[    0.000000] ACPI: RSDP 000f8500 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 17fd0000 00038 (v01 A M I  OEMRSDT  06000602 MSFT 00000097)
[    0.000000] ACPI: FACP 17fd0200 00081 (v01 A M I  OEMFACP  06000602 MSFT 00000097)
[    0.000000] ACPI: DSDT 17fd0400 04D48 (v01  410M1 410M1602 00000602 INTL 02002026)
[    0.000000] ACPI: FACS 17fdf000 00040
[    0.000000] ACPI: APIC 17fd0390 0006C (v01 A M I  OEMAPIC  06000602 MSFT 00000097)
[    0.000000] ACPI: SSDT 17fd5150 0007B (v01 OEM_ID OEMTBLID 00000001 INTL 02002026)
[    0.000000] ACPI: OEMB 17fdf040 00040 (v01 A M I  AMI_OEM  06000602 MSFT 00000097)
[    0.000000] ACPI: MCFG 17fd51d0 0003C (v01 A M I  OEMMCFG  06000602 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 383MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 17fd0000
[    0.000000]   low ram: 0 - 17fd0000
[    0.000000]   node 0 low ram: 00000000 - 17fd0000
[    0.000000]   node 0 bootmap 00012000 - 00014ffc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0017fd0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000092f7d8]    TEXT DATA BSS ==> [0000100000 - 000092f7d8]
[    0.000000]   #4 [00118b2000 - 001201b76e]          RAMDISK ==> [00118b2000 - 001201b76e]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000930000 - 0000937189]              BRK ==> [0000930000 - 0000937189]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000015000]          BOOTMAP ==> [0000012000 - 0000015000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00017fd0
[    0.000000]   HighMem  0x00017fd0 -> 0x00017fd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00017fd0
[    0.000000] On node 0 totalpages: 98143
[    0.000000] free_area_init_node: node 0, pgdat c07d4d20, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 736 pages used for memmap
[    0.000000]   Normal zone: 93424 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 18000000 (gap: 18000000:e6e00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1400000 s39448 r0 d21992 u524288
[    0.000000] pcpu-alloc: s39448 r0 d21992 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 97375
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=ae02ece1-192f-4996-8067-144aaa760f93 ro quiet quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1964800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 370372k/393024k available (4826k kernel code, 21680k reserved, 2211k data, 672k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xd87d0000 - 0xff9fe000   ( 626 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xd7fd0000   ( 383 MB)
[    0.000000]       .init : 0xc07e0000 - 0xc0888000   ( 672 kB)
[    0.000000]       .data : 0xc05b6a1b - 0xc07df7a8   (2211 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b6a1b   (4826 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using PMTIMER reference calibration
[    0.000000] Detected 3058.905 MHz processor.
[    0.016006] Calibrating delay loop (skipped), value calculated using timer frequency.. 6117.81 BogoMIPS (lpj=12235620)
[    0.016028] Security Framework initialized
[    0.016053] AppArmor: AppArmor initialized
[    0.016063] Mount-cache hash table entries: 512
[    0.016222] Initializing cgroup subsys ns
[    0.016227] Initializing cgroup subsys cpuacct
[    0.016233] Initializing cgroup subsys memory
[    0.016242] Initializing cgroup subsys devices
[    0.016245] Initializing cgroup subsys freezer
[    0.016248] Initializing cgroup subsys net_cls
[    0.016279] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.016284] CPU: L2 cache: 1024K
[    0.016287] CPU: Physical Processor ID: 0
[    0.016289] CPU: Processor Core ID: 0
[    0.016294] mce: CPU supports 4 MCE banks
[    0.016308] CPU0: Thermal monitoring enabled (TM2)
[    0.016314] using mwait in idle threads.
[    0.016324] Performance Events: no PMU driver, software events only.
[    0.016334] Checking 'hlt' instruction... OK.
[    0.036094] ACPI: Core revision 20090903
[    0.049513] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.049521] ftrace: allocating 22402 entries in 44 pages
[    0.052101] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.052974] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.095854] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
[    0.096001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.020000] CPU: L2 cache: 1024K
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 0
[    0.020000] CPU1: Thermal monitoring enabled (TM2)
[    0.180054] CPU1: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
[    0.180071] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.184001] Measured 996179841 cycles TSC warp between CPUs, turning off TSC clock.
[    0.184001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.184033] Brought up 2 CPUs
[    0.184038] Total of 2 processors activated (12300.70 BogoMIPS).
[    0.184554] CPU0 attaching sched-domain:
[    0.184562]  domain 0: span 0-1 level SIBLING
[    0.184565]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.184574]   domain 1: span 0-1 level MC
[    0.184577]    groups: 0-1 (cpu_power = 1178)
[    0.184586] CPU1 attaching sched-domain:
[    0.184589]  domain 0: span 0-1 level SIBLING
[    0.184592]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.184599]   domain 1: span 0-1 level MC
[    0.184602]    groups: 0-1 (cpu_power = 1178)
[    0.185641] devtmpfs: initialized
[    0.185641] regulator: core version 0.5
[    0.185641] Time:  8:19:17  Date: 04/23/10
[    0.185641] NET: Registered protocol family 16
[    0.185641] Trying to unpack rootfs image as initramfs...
[    0.185641] EISA bus registered
[    0.185641] ACPI: bus type pci registered
[    0.185641] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.185641] PCI: Not using MMCONFIG.
[    0.185641] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.185641] PCI: Using configuration type 1 for base access
[    0.189246] bio: create slab <bio-0> at 0
[    0.190906] ACPI: EC: Look up EC in DSDT
[    0.202027] ACPI: Executed 1 blocks of module-level executable AML code
[    0.219377] ACPI: Interpreter enabled
[    0.219392] ACPI: (supports S0 S3 S4 S5)
[    0.219435] ACPI: Using IOAPIC for interrupt routing
[    0.219705] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.237067] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.237074] PCI: Using MMCONFIG for extended config space
[    0.261929] ACPI Warning: Incorrect checksum in table [OEMB] - 20, should be 11 (20090903/tbutils-314)
[    0.262148] ACPI: No dock devices found.
[    0.262402] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.262499] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.262805] pci 0000:00:1c.0: reg 10 32bit mmio: [0xff6ff000-0xff6fffff]
[    0.262906] pci 0000:00:1c.1: reg 10 32bit mmio: [0xff6fe000-0xff6fefff]
[    0.263006] pci 0000:00:1c.2: reg 10 32bit mmio: [0xff6fd000-0xff6fdfff]
[    0.263139] pci 0000:00:1c.3: reg 10 32bit mmio: [0xff6fcc00-0xff6fccff]
[    0.263250] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.263260] pci 0000:00:1c.3: PME# disabled
[    0.263357] pci 0000:00:1d.0: reg 10 64bit mmio: [0xff6f8000-0xff6fbfff]
[    0.263434] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.263443] pci 0000:00:1d.0: PME# disabled
[    0.264106] pci 0000:00:1e.1: quirk: region 4000-403f claimed by ali7101 ACPI
[    0.264246] pci 0000:00:1f.0: reg 20 io port: [0xff00-0xff0f]
[    0.264362] pci 0000:00:1f.1: reg 10 io port: [0xec00-0xec0f]
[    0.264377] pci 0000:00:1f.1: reg 14 io port: [0xe800-0xe807]
[    0.264391] pci 0000:00:1f.1: reg 18 io port: [0xe400-0xe40f]
[    0.264404] pci 0000:00:1f.1: reg 1c io port: [0xe000-0xe007]
[    0.264417] pci 0000:00:1f.1: reg 20 io port: [0xdc00-0xdc1f]
[    0.264430] pci 0000:00:1f.1: reg 24 32bit mmio: [0xff6fc800-0xff6fcbff]
[    0.264475] pci 0000:00:1f.1: PME# supported from D3hot
[    0.264483] pci 0000:00:1f.1: PME# disabled
[    0.264564] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.264575] pci 0000:01:05.0: reg 14 io port: [0xb800-0xb8ff]
[    0.264585] pci 0000:01:05.0: reg 18 32bit mmio: [0xff4f0000-0xff4fffff]
[    0.264608] pci 0000:01:05.0: reg 30 32bit mmio pref: [0xff4c0000-0xff4dffff]
[    0.264634] pci 0000:01:05.0: supports D1 D2
[    0.264696] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.264707] pci 0000:00:01.0: bridge 32bit mmio: [0xff400000-0xff4fffff]
[    0.264715] pci 0000:00:01.0: bridge 32bit mmio pref: [0xbff00000-0xdfefffff]
[    0.264876] pci 0000:02:15.0: reg 10 32bit mmio: [0xff5fc000-0xff5fffff]
[    0.264892] pci 0000:02:15.0: reg 14 io port: [0xc800-0xc8ff]
[    0.264946] pci 0000:02:15.0: reg 30 32bit mmio pref: [0xff5c0000-0xff5dffff]
[    0.264997] pci 0000:02:15.0: supports D1 D2
[    0.265001] pci 0000:02:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.265010] pci 0000:02:15.0: PME# disabled
[    0.265086] pci 0000:02:16.0: reg 10 32bit mmio: [0xff5fb800-0xff5fbfff]
[    0.265103] pci 0000:02:16.0: reg 14 io port: [0xcc00-0xcc7f]
[    0.265212] pci 0000:02:16.0: supports D2
[    0.265217] pci 0000:02:16.0: PME# supported from D2 D3hot D3cold
[    0.265226] pci 0000:02:16.0: PME# disabled
[    0.265272] pci 0000:00:19.0: bridge io port: [0xc000-0xcfff]
[    0.265281] pci 0000:00:19.0: bridge 32bit mmio: [0xff500000-0xff5fffff]
[    0.265307] pci_bus 0000:00: on NUMA node 0
[    0.265317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.265468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.265625] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE2P._PRT]
[    0.283203] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15), disabled.
[    0.283563] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.283885] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.284247] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.284602] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.284919] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.285262] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.285589] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.285911] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.286158] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.286166] vgaarb: loaded
[    0.286410] SCSI subsystem initialized
[    0.286616] libata version 3.00 loaded.
[    0.286761] usbcore: registered new interface driver usbfs
[    0.286787] usbcore: registered new interface driver hub
[    0.286836] usbcore: registered new device driver usb
[    0.287118] ACPI: WMI: Mapper loaded
[    0.287123] PCI: Using ACPI for IRQ routing
[    0.287145] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.287151] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.287423] NetLabel: Initializing
[    0.287427] NetLabel:  domain hash size = 128
[    0.287431] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.287454] NetLabel:  unlabeled traffic allowed by default
[    0.291321] AppArmor: AppArmor Filesystem Enabled
[    0.291357] pnp: PnP ACPI init
[    0.291411] ACPI: bus type pnp registered
[    0.305711] pnp 00:0f: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.305720] pnp 00:0f: mem resource (0xc0000-0xdffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.305727] pnp 00:0f: mem resource (0xe0000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.305734] pnp 00:0f: mem resource (0x100000-0x17ffffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.306489] pnp: PnP ACPI: found 16 devices
[    0.306494] ACPI: ACPI bus type pnp unregistered
[    0.306501] PnPBIOS: Disabled by ACPI PNP
[    0.306533] system 00:0b: ioport range 0xa00-0xa0f has been reserved
[    0.306539] system 00:0b: ioport range 0xa10-0xa1f has been reserved
[    0.306545] system 00:0b: ioport range 0xa20-0xa2f has been reserved
[    0.306556] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.306570] system 00:0c: ioport range 0x28d-0x28e has been reserved
[    0.306577] system 00:0c: ioport range 0x480-0x48f has been reserved
[    0.306582] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.306589] system 00:0c: iomem range 0xff380000-0xff3fffff has been reserved
[    0.306595] system 00:0c: iomem range 0xfff80000-0xffffffff has been reserved
[    0.306601] system 00:0c: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.306607] system 00:0c: iomem range 0xfeb00000-0xfeb00fff has been reserved
[    0.306613] system 00:0c: iomem range 0xff780000-0xff7fffff has been reserved
[    0.306625] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.306631] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.306643] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    0.341572] Switching to clocksource acpi_pm
[    0.341830] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.341830] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    0.341830] pci 0000:00:01.0:   MEM window: 0xff400000-0xff4fffff
[    0.341830] pci 0000:00:01.0:   PREFETCH window: 0xbff00000-0xdfefffff
[    0.341830] pci 0000:00:19.0: PCI bridge, secondary bus 0000:02
[    0.341830] pci 0000:00:19.0:   IO window: 0xc000-0xcfff
[    0.341830] pci 0000:00:19.0:   MEM window: 0xff500000-0xff5fffff
[    0.341830] pci 0000:00:19.0:   PREFETCH window: disabled
[    0.341830] pci 0000:00:19.0: setting latency timer to 64
[    0.341830] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.341830] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.341830] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.341830] pci_bus 0000:01: resource 1 mem: [0xff400000-0xff4fffff]
[    0.341830] pci_bus 0000:01: resource 2 pref mem [0xbff00000-0xdfefffff]
[    0.341830] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.341830] pci_bus 0000:02: resource 1 mem: [0xff500000-0xff5fffff]
[    0.341830] NET: Registered protocol family 2
[    0.341830] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.341830] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.341830] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.341830] TCP: Hash tables configured (established 16384 bind 16384)
[    0.341830] TCP reno registered
[    0.341830] NET: Registered protocol family 1
[    0.341830] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.341830] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.341830] pci 0000:00:19.0: Disabling HT MSI Mapping
[    0.828161] pci 0000:01:05.0: Boot video device
[    0.828554] cpufreq-nforce2: No nForce2 chipset.
[    0.828614] Scanning for low memory corruption every 60 seconds
[    0.828816] audit: initializing netlink socket (disabled)
[    0.828840] type=2000 audit(1272010757.828:1): initialized
[    0.841268] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.844164] VFS: Disk quotas dquot_6.5.2
[    0.844285] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.845479] fuse init (API version 7.13)
[    0.845671] msgmni has been set to 724
[    0.846121] alg: No test for stdrng (krng)
[    0.846229] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.846235] io scheduler noop registered
[    0.846239] io scheduler anticipatory registered
[    0.846243] io scheduler deadline registered
[    0.846324] io scheduler cfq registered (default)
[    0.846554] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.846600] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.846799] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.846807] ACPI: Power Button [PWRB]
[    0.846925] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.846930] ACPI: Power Button [PWRF]
[    0.847768] processor LNXCPU:00: registered as cooling_device0
[    0.848122] processor LNXCPU:01: registered as cooling_device1
[    0.860354] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.860592] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.860768] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.861349] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.861598] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.863878] brd: module loaded
[    0.864929] loop: module loaded
[    0.865128] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.865515]   alloc irq_desc for 21 on node -1
[    0.865521]   alloc kstat_irqs on node -1
[    0.865535] pata_acpi 0000:00:1f.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.865620] pata_acpi 0000:00:1f.0: PCI INT A disabled
[    0.866274] Fixed MDIO Bus: probed
[    0.866347] PPP generic driver version 2.4.2
[    0.866437] tun: Universal TUN/TAP device driver, 1.6
[    0.866441] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.866615] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.866653]   alloc irq_desc for 23 on node -1
[    0.866657]   alloc kstat_irqs on node -1
[    0.866666] ehci_hcd 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.866699] ehci_hcd 0000:00:1c.3: EHCI Host Controller
[    0.866759] ehci_hcd 0000:00:1c.3: new USB bus registered, assigned bus number 1
[    0.866818] ehci_hcd 0000:00:1c.3: debug port 1
[    0.866904] isapnp: Scanning for PnP cards...
[    0.916099] ehci_hcd 0000:00:1c.3: cache line size of 128 is not supported
[    0.916149] ehci_hcd 0000:00:1c.3: irq 23, io mem 0xff6fcc00
[    0.928375] ehci_hcd 0000:00:1c.3: USB 2.0 started, EHCI 1.00
[    0.928608] usb usb1: configuration #1 chosen from 1 choice
[    0.928665] hub 1-0:1.0: USB hub found
[    0.928684] hub 1-0:1.0: 8 ports detected
[    0.928831] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.928871]   alloc irq_desc for 17 on node -1
[    0.928875]   alloc kstat_irqs on node -1
[    0.928886] ohci_hcd 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.928921] ohci_hcd 0000:00:1c.0: OHCI Host Controller
[    0.928996] ohci_hcd 0000:00:1c.0: new USB bus registered, assigned bus number 2
[    0.929045] ohci_hcd 0000:00:1c.0: irq 17, io mem 0xff6ff000
[    0.947482] Freeing initrd memory: 7589k freed
[    0.990304] usb usb2: configuration #1 chosen from 1 choice
[    0.990358] hub 2-0:1.0: USB hub found
[    0.990382] hub 2-0:1.0: 3 ports detected
[    0.990492]   alloc irq_desc for 18 on node -1
[    0.990496]   alloc kstat_irqs on node -1
[    0.990510] ohci_hcd 0000:00:1c.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    0.990544] ohci_hcd 0000:00:1c.1: OHCI Host Controller
[    0.990607] ohci_hcd 0000:00:1c.1: new USB bus registered, assigned bus number 3
[    0.990663] ohci_hcd 0000:00:1c.1: irq 18, io mem 0xff6fe000
[    1.050137] usb usb3: configuration #1 chosen from 1 choice
[    1.050182] hub 3-0:1.0: USB hub found
[    1.050197] hub 3-0:1.0: 3 ports detected
[    1.050273]   alloc irq_desc for 19 on node -1
[    1.050277]   alloc kstat_irqs on node -1
[    1.050284] ohci_hcd 0000:00:1c.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.050301] ohci_hcd 0000:00:1c.2: OHCI Host Controller
[    1.050366] ohci_hcd 0000:00:1c.2: new USB bus registered, assigned bus number 4
[    1.050408] ohci_hcd 0000:00:1c.2: irq 19, io mem 0xff6fd000
[    1.110136] usb usb4: configuration #1 chosen from 1 choice
[    1.110188] hub 4-0:1.0: USB hub found
[    1.110202] hub 4-0:1.0: 3 ports detected
[    1.110294] uhci_hcd: USB Universal Host Controller Interface driver
[    1.110474] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.113097] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.113108] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.113327] mice: PS/2 mouse device common for all mice
[    1.113553] rtc_cmos 00:02: RTC can wake from S4
[    1.113620] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.113669] rtc0: alarms up to one month, 114 bytes nvram
[    1.113855] device-mapper: uevent: version 1.0.3
[    1.114048] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.114181] device-mapper: multipath: version 1.1.0 loaded
[    1.114186] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.114372] EISA: Probing bus 0 at eisa.0
[    1.114405] Cannot allocate resource for EISA slot 4
[    1.114435] EISA: Detected 0 cards.
[    1.114574] cpuidle: using governor ladder
[    1.114578] cpuidle: using governor menu
[    1.115427] TCP cubic registered
[    1.115659] NET: Registered protocol family 10
[    1.116544] lo: Disabled Privacy Extensions
[    1.117138] NET: Registered protocol family 17
[    1.117220] Using IPI No-Shortcut mode
[    1.117353] PM: Resume from disk failed.
[    1.117374] registered taskstats version 1
[    1.117761]   Magic number: 6:832:321
[    1.117802] tty tty46: hash matches
[    1.117910] rtc_cmos 00:02: setting system clock to 2010-04-23 08:19:18 UTC (1272010758)
[    1.117916] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.117919] EDD information not available.
[    1.140630] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.225562] isapnp: No Plug & Play device found
[    1.225593] Freeing unused kernel memory: 672k freed
[    1.226406] Write protecting the kernel text: 4828k
[    1.226512] Write protecting the kernel read-only data: 1876k
[    1.250689] udev: starting version 151
[    1.445487]   alloc irq_desc for 20 on node -1
[    1.445493]   alloc kstat_irqs on node -1
[    1.445513] skge 0000:02:15.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.445610] skge 1.13 addr 0xff5fc000 irq 20 chip Yukon-Lite rev 9
[    1.447145] skge eth0: addr 00:16:ec:9f:83:9a
[    1.473729] pata_ali 0000:00:1f.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.479974] scsi0 : pata_ali
[    1.482909] scsi1 : pata_ali
[    1.485918] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.485924] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.486019] sata_uli 0000:00:1f.1: version 1.3
[    1.486049] sata_uli 0000:00:1f.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.486440] scsi2 : sata_uli
[    1.486565] scsi3 : sata_uli
[    1.486668] scsi4 : sata_uli
[    1.486767] scsi5 : sata_uli
[    1.486854] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 21
[    1.486861] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 21
[    1.486868] ata5: SATA max UDMA/133 cmd 0xec08 ctl 0xe806 bmdma 0xdc10 cmd 0xe409 ctl 0xe006 bmdma 0xdc18 irq 21
[    1.486876] ata6: SATA max UDMA/133 irq 21
[    1.487315] ohci1394 0000:02:16.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.496154] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    1.496636] FDC 0 is a post-1991 82077
[    1.546117] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[23]  MMIO=[ff5fb800-ff5fbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.664413] ata1.00: ATAPI: LITE-ON DVDRW SHW-160P6S, PRS2, max UDMA/66
[    1.664445] ata1.00: WARNING: ATAPI DMA disabled for reliability issues.  It can be enabled
[    1.664448] ata1.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    1.696348] ata1.00: configured for UDMA/66
[    1.697873] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-160P6S PRS2 PQ: 0 ANSI: 5
[    1.702521] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.702526] Uniform CD-ROM driver Revision: 3.20
[    1.702677] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.702775] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.712149] usb 4-1: configuration #1 chosen from 1 choice
[    1.723601] Initializing USB Mass Storage driver...
[    1.723793] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.724002] usb-storage: device found at 2
[    1.724006] usb-storage: waiting for device to settle before scanning
[    1.724047] usbcore: registered new interface driver usb-storage
[    1.724174] USB Mass Storage support registered.
[    1.956090] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.964597] ata3.00: ATA-7: WDC WD1600JS-22NCB1, 10.02E02, max UDMA/133
[    1.964602] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.972616] ata3.00: configured for UDMA/133
[    1.972770] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600JS-22N 10.0 PQ: 0 ANSI: 5
[    1.973055] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.973277] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.973352] sd 2:0:0:0: [sda] Write Protect is off
[    1.973356] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.973394] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.973605]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.004798] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.820189] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff55c3b8]
[    3.365022] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    6.726155] usb-storage: device scan complete
[    6.733100] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    6.740098] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    6.747096] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    6.754092] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    6.754850] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.755068] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    6.755353] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    6.755575] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    6.787078] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    6.820073] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    6.831073] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    6.842076] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    9.776759] Adding 1020088k swap on /dev/sda5.  Priority:-1 extents:1 across:1020088k 
[   10.460185] udev: starting version 151
[   10.483452] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   11.447817] type=1505 audit(1272010768.826:2):  operation="profile_load" pid=491 name="/sbin/dhclient3"
[   11.448761] type=1505 audit(1272010768.830:3):  operation="profile_load" pid=491 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.449201] type=1505 audit(1272010768.830:4):  operation="profile_load" pid=491 name="/usr/lib/connman/scripts/dhclient-script"
[   11.642848] parport_pc 00:0a: reported by Plug and Play ACPI
[   11.643004] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   11.667425] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.681275] ppdev: user-space parallel port driver
[   11.778500] ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
[   11.778507] ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not inserted.
[   11.792385] lp0: using parport0 (interrupt-driven).
[   11.828938] ali15x3_smbus 0000:00:1e.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   11.829014] ali15x3_smbus 0000:00:1e.1: ALI15X3 not detected, module not inserted.
[   11.839793] type=1505 audit(1272010769.218:5):  operation="profile_load" pid=586 name="/usr/sbin/ntpd"
[   11.845561] psmouse serio1: ID: 10 00 64
[   11.984176] Linux agpgart interface v0.103
[   12.096181] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.293855] [drm] Initialized drm 1.1.0 20060810
[   12.317528] it87: Found IT8712F chip at 0xa10, revision 7
[   12.317543] it87: in3 is VCC (+5V)
[   12.317546] it87: in7 is VCCH (+5V Stand-By)
[   12.405752] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   12.917589] [drm] radeon defaulting to kernel modesetting.
[   12.917596] [drm] radeon kernel modesetting enabled.
[   12.917683] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.921339] [drm] radeon: Initializing kernel modesetting.
[   12.921508] [drm] register mmio base: 0xFF4F0000
[   12.921512] [drm] register mmio size: 65536
[   12.924923] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   12.926084] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   12.926161] [drm] Generation 2 PCI interface, using max accessible memory
[   12.926167] [drm] radeon: VRAM 128M
[   12.926171] [drm] radeon: VRAM from 0x18000000 to 0x1FFFFFFF
[   12.926175] [drm] radeon: GTT 32M
[   12.926178] [drm] radeon: GTT from 0x20000000 to 0x21FFFFFF
[   12.926229] [drm] radeon: irq initialized.
[   12.926685] [drm] Detected VRAM RAM=128M, BAR=256M
[   12.926691] [drm] RAM width 128bits DDR
[   12.927069] [TTM] Zone  kernel: Available graphics memory: 189578 kiB.
[   12.927097] [drm] radeon: 128M of VRAM memory ready
[   12.927102] [drm] radeon: 32M of GTT memory ready.
[   12.927129] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   12.927890] [drm] radeon: 4 quad pipes, 1 z pipes initialized.
[   12.927921] [drm] radeon: cp idle (0x10000C03)
[   12.927988] [drm] Loading R300 Microcode
[   12.928555] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   12.944419] nf_conntrack version 0.5.0 (5924 buckets, 23696 max)
[   12.945373] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   12.945380] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   12.945384] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   12.970498] [drm] radeon: ring at 0x0000000020000000
[   12.970529] [drm] ring test succeeded in 1 usecs
[   12.970858] [drm] radeon: ib pool ready.
[   12.970993] [drm] ib test succeeded in 0 usecs
[   12.971084] [drm] Default TV standard: NTSC
[   12.971089] [drm] 14.318180000 MHz TV ref clk
[   12.971240] [drm] Default TV standard: NTSC
[   12.971244] [drm] 14.318180000 MHz TV ref clk
[   12.971302] [drm] Radeon Display Connectors
[   12.971306] [drm] Connector 0:
[   12.971310] [drm]   VGA
[   12.971314] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   12.971318] [drm]   Encoders:
[   12.971322] [drm]     CRT1: INTERNAL_DAC2
[   12.971325] [drm] Connector 1:
[   12.971328] [drm]   S-video
[   12.971331] [drm]   Encoders:
[   12.971334] [drm]     TV1: INTERNAL_DAC2
[   13.087084] [drm] fb mappable at 0xC0040000
[   13.087089] [drm] vram apper at 0xC0000000
[   13.087092] [drm] size 5184000
[   13.087095] [drm] fb depth is 24
[   13.087098] [drm]    pitch is 5760
[   13.087252] fb0: radeondrmfb frame buffer device
[   13.087256] registered panic notifier
[   13.087267] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   13.218990] vga16fb: initializing
[   13.218997] vga16fb: mapped to 0xc00a0000
[   13.219006] vga16fb: not registering due to another framebuffer present
[   13.351777]   alloc irq_desc for 22 on node -1
[   13.351782]   alloc kstat_irqs on node -1
[   13.351795] HDA Intel 0000:00:1d.0: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   13.395984] Console: switching to colour frame buffer device 180x56
[   13.415442] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   13.606921] hda_codec: ALC880: BIOS auto-probing.
[   13.608930] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1d.0/input/input5
[   15.819780] skge eth0: enabling interface
[   15.823561] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.168457] type=1505 audit(1272010774.550:6):  operation="profile_load" pid=1014 name="/usr/share/gdm/guest-session/Xsession"
[   17.171618] type=1505 audit(1272010774.550:7):  operation="profile_replace" pid=1015 name="/sbin/dhclient3"
[   17.172452] type=1505 audit(1272010774.554:8):  operation="profile_replace" pid=1015 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.173074] type=1505 audit(1272010774.554:9):  operation="profile_replace" pid=1015 name="/usr/lib/connman/scripts/dhclient-script"
[   17.192739] type=1505 audit(1272010774.574:10):  operation="profile_load" pid=1016 name="/usr/bin/evince"
[   17.202817] type=1505 audit(1272010774.582:11):  operation="profile_load" pid=1016 name="/usr/bin/evince-previewer"
[   17.208590] type=1505 audit(1272010774.590:12):  operation="profile_load" pid=1016 name="/usr/bin/evince-thumbnailer"
[   17.326206] type=1505 audit(1272010774.706:13):  operation="profile_load" pid=1018 name="/usr/bin/freshclam"
[   17.347961] type=1505 audit(1272010774.726:14):  operation="profile_load" pid=1019 name="/usr/lib/cups/backend/cups-pdf"
[   17.348927] type=1505 audit(1272010774.730:15):  operation="profile_load" pid=1019 name="/usr/sbin/cupsd"
[   17.506903] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   17.507047] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```
:popcorn: 17,5s:)

---

### Post by Owen.C93 on 2010-04-23
> **mk04 said:**
> 36 seconds to internet connecetion. Minus 1.5sec for me to type in password + clicking on the network manager to click on my network to connect (3sec). Approx. = 30-32sec

Shutdown time approx. 15sec
My startup is around 22 sec, but shutdown is only about 3sec. Providing I shut all running apps though.

---

### Post by mk04 on 2010-04-23
Mine is much less than 15 sec, not sure why I posted 15 sec. It's more like 3-5 seconds. SO MUCH FASTER THAN VISTA!! I could take a nap while Vista boots up.

---

### Post by franc00018 on 2010-04-23
[http://img402.imageshack.us/img402/1659/francoiskubuntulucid201.png](http://img402.imageshack.us/img402/1659/francoiskubuntulucid201.png)

This is really really slow compared to 9.10
I also have a heavy load on RAM
Where should I begin for some tweaking ?

---

### Post by MacUntu on 2010-04-23
Yes, shutdown time has improved for me as well (usually 3-5 seconds).

---

### Post by Longinus00 on 2010-04-23
> **franc00018 said:**
> [http://img402.imageshack.us/img402/1659/francoiskubuntulucid201.png](http://img402.imageshack.us/img402/1659/francoiskubuntulucid201.png)

This is really really slow compared to 9.10
I also have a heavy load on RAM
Where should I begin for some tweaking ?

Looks like it was profiling during the boot so of course it was slow. See how your subsequent boots go.

---

### Post by franc00018 on 2010-04-23
> **Longinus00 said:**
> Looks like it was profiling during the boot so of course it was slow. See how your subsequent boots go.

22.58 seconds

francois@francois-kubuntu:/var/log/bootchart$ free
             total       used       free     shared    buffers     cached
Mem:       1890444     868176    1022268          0      45208     358848
-/+ buffers/cache:     464120    1426324
Swap:      5535736          0    5535736

Which is better.

[http://yfrog.com/2pfrancoiskubuntulucid201p](http://yfrog.com/2pfrancoiskubuntulucid201p)

---

### Post by Longinus00 on 2010-04-23
> **franc00018 said:**
> 22.58 seconds

francois@francois-kubuntu:/var/log/bootchart$ free
             total       used       free     shared    buffers     cached
Mem:       1890444     868176    1022268          0      45208     358848
-/+ buffers/cache:     464120    1426324
Swap:      5535736          0    5535736

Which is better.

[http://yfrog.com/2pfrancoiskubuntulucid201p](http://yfrog.com/2pfrancoiskubuntulucid201p)

ureadahead has a problem with not freeing memory after a reprofile so that was the high memory usage you were seeing. You can also see that booting is faster after it profiles.

---

### Post by Martijnvdc on 2010-04-24
65 seconds:
[http://img191.imageshack.us/img191/2296/ubuntulucid201004242.png](http://img191.imageshack.us/img191/2296/ubuntulucid201004242.png)
seems very slow, how could i improve this?
(i use wubi by the way)

---

### Post by jocko on 2010-04-24
Below 9 seconds. I'm pretty impressed...
[http://img46.imageshack.us/img46/5551/jockodesktoplucid201004.png](http://img46.imageshack.us/img46/5551/jockodesktoplucid201004.png)

Edit: [Below 8 seconds with the preemt kernel]("http://img249.imageshack.us/img249/5551/jockodesktoplucid201004.png")...

---

### Post by jocko on 2010-04-24
> **Martijnvdc said:**
> 65 seconds:
[http://img191.imageshack.us/img191/2296/ubuntulucid201004242.png](http://img191.imageshack.us/img191/2296/ubuntulucid201004242.png)
seems very slow, how could i improve this?
(i use wubi by the way)
If you want to see a real improvement, you probably need to ditch wubi and do a "real" install with it's own file system.
Also, your cpu is 64 bit, so I'm guessing you would gain from installing 64 bit ubuntu instead of crippling it with a 32 bit install...

---

### Post by psusi on 2010-04-24
6.28 seconds on an OCZ Vertex 64gb ssd:

[http://img189.imageshack.us/img189/2173/faldaralucid201004241.png](http://img189.imageshack.us/img189/2173/faldaralucid201004241.png)

---

### Post by Netich on 2010-04-25
[http://img62.imageshack.us/img62/7392/davidlaptoplucid2010042.png](http://img62.imageshack.us/img62/7392/davidlaptoplucid2010042.png)

It was faster in my testing partition, but since i upgraded from karmic, it has slowed down. There seems to be a delay just after grub, and another one when in desktop, before the panels appears.
And of course, no plymouth at all.

Any tip?

---

### Post by mrpinchy on 2010-04-25
[http://img717.imageshack.us/img717/8270/josephlaptoplucid201004.png](http://img717.imageshack.us/img717/8270/josephlaptoplucid201004.png)

33.21 seconds.

Hey,

I think I know how to read this chart, but could someone give a quick explanation of it.

Thanks,
Joe.

---

### Post by Owen.C93 on 2010-04-25
> **mrpinchy said:**
> [http://img717.imageshack.us/img717/8270/josephlaptoplucid201004.png](http://img717.imageshack.us/img717/8270/josephlaptoplucid201004.png)

33.21 seconds.

Hey,

I think I know how to read this chart, but could someone give a quick explanation of it.

Thanks,
Joe.
Looks like ureadahead was profiling in that boot. It should be faster the next time. You can probably remove HAL. Also I think you are manually logging in? Make sue you have auto login enabled for a real boot time. :)

---

### Post by mrpinchy on 2010-04-25
I apologize as I'm sure this question belongs elsewhere, but it seems to apply to what Owen.C93 just said...   ...so.

What would the ups & downs of removing HAL be?

Thanks,
Joe.

---

### Post by sh1ny on 2010-04-25
11.79 seconds

[IMG]https://dl.dropbox.com/u/442808/shiny-PC-lucid-20100425-2.png[/IMG]

---

### Post by Jordanwb on 2010-04-25
[http://img28.imageshack.us/img28/4959/jordancd3cda3blucid2010.png](http://img28.imageshack.us/img28/4959/jordancd3cda3blucid2010.png)

~21 seconds. Feels good bro. I'm not sure what the bottleneck is. I would not be surprised if it is the hard drive.

Dropbox and Docky are taking a fair bit of CPU power.

> **psusi said:**
> 6.28 seconds on an OCZ Vertex 64gb ssd:

[http://img189.imageshack.us/img189/2173/faldaralucid201004241.png](http://img189.imageshack.us/img189/2173/faldaralucid201004241.png)

Good god that's insane.

---

### Post by jocko on 2010-04-25
Hmmm... I thought ureadahead was supposed to improve boot speed, but it actually adds 0.6 seconds...
[With ureadahead 7.15 s]("http://img710.imageshack.us/img710/5551/jockodesktoplucid201004.png"), [without ureadahead 6.55 s]("http://img163.imageshack.us/img163/5551/jockodesktoplucid201004.png")...
Not that I should complain with these crazy fast boot speeds (intel X25-V 40Gb SSD)

---

### Post by psusi on 2010-04-25
> **jocko said:**
> Hmmm... I thought ureadahead was supposed to improve boot speed, but it actually adds 0.6 seconds...
[With ureadahead 7.15 s]("http://img710.imageshack.us/img710/5551/jockodesktoplucid201004.png"), [without ureadahead 6.55 s]("http://img163.imageshack.us/img163/5551/jockodesktoplucid201004.png")...
Not that I should complain with these crazy fast boot speeds (intel X25-V 40Gb SSD)

It looks like your system is not detecting you have an SSD.  When you have an ssd the ureadahead forks into the background and reads in parallel with the rest of the boot.  On a rotational hard disk it reads first, then returns, allowing the boot to continue, since that is preferable to taking the seek penalties on rotational media.

---

### Post by lockalidiot on 2010-04-25
47,34 sec... pretty far from the 10 sec...

EDIT: 44,03 sec after removing stuff from the Startup Applications. Still not good.

---

### Post by jocko on 2010-04-26
> **psusi said:**
> It looks like your system is not detecting you have an SSD.  When you have an ssd the ureadahead forks into the background and reads in parallel with the rest of the boot.  On a rotational hard disk it reads first, then returns, allowing the boot to continue, since that is preferable to taking the seek penalties on rotational media.

Thanks for the hint. That was not the problem (cat /sys/block/sd*/queue/rotational said "0", so it was properly detected as a SSD), but it got me thinking:

I had a rotational hard drive as /dev/sda and the SSD as /dev/sdb, so I just switched the sata cables around to make the SSD become /dev/sda, and now ureadahead behaves properly and makes it [boot in less than 6 seconds]("http://img717.imageshack.us/i/jockodesktoplucid201004.png/")!

---

### Post by Otustelija on 2010-04-28
> **jocko said:**
> Thanks for the hint. That was not the problem (cat /sys/block/sd*/queue/rotational said "0", so it was properly detected as a SSD), but it got me thinking:

I had a rotational hard drive as /dev/sda and the SSD as /dev/sdb, so I just switched the sata cables around to make the SSD become /dev/sda, and now ureadahead behaves properly and makes it [boot in less than 6 seconds]("http://img717.imageshack.us/i/jockodesktoplucid201004.png/")!

You should maybe file a bug?

In any case I get around 9.50s on a hard drive!

[[IMG]http://img88.imageshack.us/img88/6721/snotralucid201004273.th.png[/IMG]](http://img88.imageshack.us/i/snotralucid201004273.png/)

---

### Post by cguy on 2010-04-28
> **lockalidiot said:**
> 47,34 sec... pretty far from the 10 sec...

EDIT: 44,03 sec after removing stuff from the Startup Applications. Still not good.

Did you *upgrade* from an earlier version?

---

### Post by Merk42 on 2010-04-28
> **lockalidiot said:**
> 47,34 sec... pretty far from the 10 sec...

EDIT: 44,03 sec after removing stuff from the Startup Applications. Still not good.

Do you have an SSD? If not, you shouldn't expect 10 seconds

---

### Post by Owen.C93 on 2010-04-28
Could you post a bootchart please :).

43 seconds is too long.

---

### Post by brunogirin on 2010-04-28
10.09 seconds. Not bad for a 6 year old laptop!

The one thing I did to get such times is swap the original HDD for an SSD when I upgraded to Karmic last year. The increase in performance was definitely worth the investment.

See [the bootchart]("http://www.flickr.com/photos/brunogirin/4560526627/") for details.

---

### Post by andrewabc on 2010-04-28
> **brunogirin said:**
> 10.09 seconds. Not bad for a 6 year old laptop!

The one thing I did to get such times is swap the original HDD for an SSD when I upgraded to Karmic last year. The increase in performance was definitely worth the investment.

See [the bootchart]("http://www.flickr.com/photos/brunogirin/4560526627/") for details.

Yep, with good 30gb SSD approaching $100, it makes a huge difference in speed for laptops.

Hmm, your bootchart only shows top speed of 51mb/s
What SSD do you have? Maybe your SATA or something is slowing it down?
Usually people with retail SSD (not cheap/slow ones) get at least 100mb/s in bootchart.

Still a good time. My 60gb ssd gets 6 seconds with ubuntu 9.10, although in bootchart it would show up to 144mb/s. This is on a 3.5 year old desktop.

---

