---
title: "Karmic is slow."
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by stuart.reinke on 2009-07-28
I've noticed that Karmic moves a lot slower than Jaunty does on my machine.  Has anyone else noticed the same thing? Is this normal for alpha releases or do I need to report it.

---

### Post by philcamlin on 2009-07-28
mine seems faster my a tad
well we cant really judge karamic yet though because its still in testing :popcorn:
do you have all your drivers installed? that can slow a pc down :o

---

### Post by durand on 2009-07-28
I think karmic is slower for me as well, but I can't quantitavely prove that..

---

### Post by philcamlin on 2009-07-28
> **durand said:**
> I think karmic is slower for me as well, but I can't quantitavely prove that..
they will probably improve before the release :P its aparently suposed to be faster :o

---

### Post by stuart.reinke on 2009-07-28
I've never had to install drivers. Everything has always worked out of the box. I used Update Manager to upgrade to Karmic from Jaunty. Maybe that was the wrong way to go.

---

### Post by Darkshade on 2009-07-28
Karmic is almost twice faster than Jaunty for me :o

---

### Post by philcamlin on 2009-07-28
see mine is really fast and some are really slow i guess its just compatibility and they will work that out b the release most liekly :D

---

### Post by Dullstar on 2009-07-28
I think I've heard that sometimes updating like that can be a problem, but I don't know for sure.  You could ask someone with more knowledge, after all I started out with Jaunty, and don't feel the need to upgrade to Karmic for now.

---

### Post by philcamlin on 2009-07-28
> **Dullstar said:**
> I think I've heard that sometimes updating like that can be a problem, but I don't know for sure.  You could ask someone with more knowledge, after all I started out with Jaunty, and don't feel the need to upgrade to Karmic for now.

fresh install is always better :) 
upgrading causes too much issues

---

### Post by durand on 2009-07-28
Mine was an upgrade. That could be it. One real problem I have is that while bootup (to gdm) is fast, gdm to desktop ready is unbelievably slow. It takes about a two minutes to get to a state where I can actually do something.

---

### Post by froggyswamp on 2009-07-28
> **stuart.reinke said:**
> I've never had to install drivers. Everything has always worked out of the box. I used Update Manager to upgrade to Karmic from Jaunty. Maybe that was the wrong way to go.
Yes. You should've installed it on a new partition and keep Jaunty intact. Since Karmic is in alpha you can't rely on it unless for testing.

---

### Post by scaine on 2009-07-28
I don't think you get the new Grub loader either unless you do a clean install.

---

### Post by wayne_cat on 2009-07-28
> **scaine said:**
> I don't think you get the new Grub loader either unless you do a clean install.

```
sudo apt-get install grub2
```

---

### Post by stuart.reinke on 2009-07-28
> **froggyswamp said:**
> Yes. You should've installed it on a new partition and keep Jaunty intact. Since Karmic is in alpha you can't rely on it unless for testing.

I do have Karmic on a separate (5 Gb) partition. I kept a Jaunty install for normal use.

I turned my last blank cd into a coaster while trying to burn the Karmic A3 iso. Since I didn't know when I would make it into town to get more cds  I decided to install another Jaunty and upgrade it to Karmic. (seemed like a good plan B)  

I think I'll make a trip into town tomorrow so I can do a clean install and see if there is a difference. That way I can try the ext4 file system and Grub 2.

---

### Post by alphacrucis2 on 2009-07-28
I upgraded to Karmic from Jaunty by editing my sources at pre alpha time. Manually installed grub2. Haven't had any problem that wasn't related to particular updates that others saw too. Generally Karmic seems faster to boot and gnome seems snappier. Part of this may be that the full benefit of EXT4 is now kicking in as under Jaunty I migrated to EXT4 via tune2fs so all the system files were still stored as EXT3. By now a goodly percentage of those files have been rewritten by various updates.

---

### Post by psyke83 on 2009-07-28
> **stuart.reinke said:**
> I've noticed that Karmic moves a lot slower than Jaunty does on my machine.  Has anyone else noticed the same thing? Is this normal for alpha releases or do I need to report it.

What graphics chipset do you have?

```
$ lspci | grep VGA
```

---

### Post by nanog on 2009-07-28
I've run Ubuntu on over dozen boxes/laptops since 2006ish and have done a clean reinstall exactly once (the user installed poorly packaged third party debs). There is virtually no difference between an upgrade and clean install.

---

### Post by scaine on 2009-07-28
> **nanog said:**
> I've run Ubuntu on over dozen boxes/laptops since 2006ish and have done a clean reinstall exactly once (the user installed poorly packaged third party debs). There is virtually no difference between an upgrade and clean install.

Not sure about that - I think that it utterly depends on whether you keep your meta packages such ubuntu-desktop installed.  And it only takes a couple of PPAs to stretch out and contort dependencies to breaking  point.  A clean install is the best way.

And new tech, such as grub 2 is not carried into an in-place update.  As a few have noted, you have to know to install it to keep pace with a clean install.

---

### Post by stuart.reinke on 2009-07-28
> **psyke83 said:**
> What graphics chipset do you have?

```
$ lspci | grep VGA
```

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

---

### Post by psyke83 on 2009-07-28
> **stuart.reinke said:**
> 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

Ok, now a question: do you feel that your impression of the system being "slow" is due to slow graphical performance? I happen to have an old laptop (Compaq NX9010) which has the same controller, and 2D performance is awful by default.

If you could get a "bare" xorg.conf, you could attempt to test the "greedy" migration heuristic - that restored performance back to normal for me.

See "man exa" for the migration heuristic information, and "man radeon" for other driver options that you can tweak. You'll first need to generate or find a bare xorg.conf file in order to customize... *sigh*.

---

### Post by stuart.reinke on 2009-07-28
I really don't know if the slow speed is due to graphics or not. It just seems everything is slow. Boot time is slow, programs are slow to load, web pages are slow to load. I even can see the difference in the slower speed that pages scroll up and down. (all compared to the Jaunty install on the same laptop)

---

### Post by nanog on 2009-07-28
> And it only takes a couple of PPAs to stretch out and contort dependencies to breaking point. 
Not my experience at all. You have to be trolling some really venereal ppas to have problems with dependencies.

---

### Post by thezood on 2009-07-29
> **stuart.reinke said:**
> I really don't know if the slow speed is due to graphics or not. It just seems everything is slow. Boot time is slow, programs are slow to load, web pages are slow to load. I even can see the difference in the slower speed that pages scroll up and down. (all compared to the Jaunty install on the same laptop)

That's exactly the kind of problem I've experienced when my machines haven't had proper graphics acceleration. It's like using the default graphics drivers in Windows. If graphics acceleration doesn't work, everything feels slow. Try the things the previous poster wrote; however, if boot and and starting programs also is slow, there could be other issues as well.

---

### Post by stuart.reinke on 2009-07-29
I think you guys are right about the graphics. After a couple of rounds of updates and a partial upgrade, boot time and program loading time is improved. However, things that are directly related to the display are still notably slower.

---

### Post by stuart.reinke on 2009-07-29
It appears that a clean install solved my speed issues. Anybody care to speculate as to why?

---

### Post by 23meg on 2009-07-29
> **stuart.reinke said:**
> It appears that a clean install solved my speed issues. Anybody care to speculate as to why?

It's impossible to tell without knowing your exact specs, and whether / how you made any modifications to any components, with or without knowing, that affect "speed" or your perception thereof. It's also to be expected in the development branch at this stage, so there's not much use in speculating.

---

### Post by jerrylamos on 2009-07-29
Slow is best shown with measurements and specifics on hardware & software.

For video performance I use GtkPerf from synaptic.  On my IBM Thinkpad R31 with i830 video graphics Karmic is twice as slow.  There's a launchpad bug on that.  i845 is 34% slow, there's another bug, and even ATI Radeon is 22% slower, there's a bug on that one too.

I think all of these are that the video drivers, KMS, DRI, etc. are all still being worked on.  It's hard to tell how much improvement the developers will be able to get.  Right now, with the latest intel driver 2.8.0, both the i830 and i845 boot to black screen death.  There's bugs for those too.

So I multi boot; if I need speed I run jaunty or intrepid, if I'm looking for bugs I run karmic.

Cheers, Jerry

---

### Post by mariner09 on 2009-07-29
I have a current issue with Compiz on Intel GM965 where after a couple of hours, X gets really sluggish.  I trace this to CPU utilization and the fact that temps go over 140F.  If I leave Compiz off, CPU is nominal and temps are normal.

I think the video stack has some work still to be done...

---

### Post by psyke83 on 2009-07-29
> **mariner09 said:**
> I have a current issue with Compiz on Intel GM965 where after a couple of hours, X gets really sluggish.  I trace this to CPU utilization and the fact that temps go over 140F.  If I leave Compiz off, CPU is nominal and temps are normal.

I think the video stack has some work still to be done...

Well, there's a fairly serious performance issue for 8xx class Intel graphics chipsets. See: [https://bugs.freedesktop.org/show_bug.cgi?id=22877](https://bugs.freedesktop.org/show_bug.cgi?id=22877)

That most likely won't apply to you, but perhaps there's a similar issue at work.

---

### Post by stuart.reinke on 2009-07-29
> **jerrylamos said:**
> Slow is best shown with measurements and specifics on hardware & software.

For video performance I use GtkPerf from synaptic.  On my IBM Thinkpad R31 with i830 video graphics Karmic is twice as slow.  There's a launchpad bug on that.  i845 is 34% slow, there's another bug, and even ATI Radeon is 22% slower, there's a bug on that one too.

I think all of these are that the video drivers, KMS, DRI, etc. are all still being worked on.  It's hard to tell how much improvement the developers will be able to get.  Right now, with the latest intel driver 2.8.0, both the i830 and i845 boot to black screen death.  There's bugs for those too.

So I multi boot; if I need speed I run jaunty or intrepid, if I'm looking for bugs I run karmic.

Cheers, Jerry

That is good info to know. My Thinkpad R40e is using the ATI Radeon. I'm glad that it isn't my imagination.  

Will it help if report the problem also? 

This is my first time at testing a pre-release system. Please excuse me if I haven't yet mastered all the procedures and protocols yet.

---

### Post by Eskobar on 2009-10-01
I've owned and operated a computer repair business since 99. From my experience a clean install is always better than an upgrade.  Simply because there is always remnants of the old system on your hard drive.

---

### Post by ozorba on 2009-10-01
But if you do 

sudo apt-get autoremove

almost all the old stuff is removed.

---

### Post by psyke83 on 2009-10-01
> **ozorba said:**
> But if you do 

sudo apt-get autoremove

almost all the old stuff is removed.

"Almost" is the operative word. Upgrading from a previous distribution also means that some *user* configuration will be outdated. New user defaults do not always get retroactively applied to existing user accounts from older releases.

---

### Post by kimda on 2009-10-01
I have also reinstalled completely on both my pc's. Karmic has ext4 and encrypted /home which is a lot easier to get working properly with a clean install than upgrading from Jaunty. Also i've read that the extends function wont work on converted filesystems on pre existing files. 

In both pc's i have a second harddrive which i used to backup up /home, /etc and other important stuff. Also I made a dump of all packages installed (dpkg --get-selections > packages) and a backup of the crontabs. Karmic has an amazing performance on both machines..I really notice the difference with Jaunty. Great work guys!

---

### Post by sliketymo on 2009-10-01
> **Dullstar said:**
> I think I've heard that sometimes updating like that can be a problem, but I don't know for sure.  You could ask someone with more knowledge, after all I started out with Jaunty, and don't feel the need to upgrade to Karmic for now.

:guitar:My feelings exactly! I've got Jaunty smokin' right along.I'll wait for the next LTS,then think about it.Don't fix it if it ain't broke.

---

### Post by Anubis on 2009-10-02
[http://global.phoronix-test-suite.com/index.php?k=profile&u=darthanubis-12377-13848-2528]("http://global.phoronix-test-suite.com/index.php?k=profile&u=darthanubis-12377-13848-2528")

Nothing slow about Karmic on this machine. In most of the tests there was either no difference or Karmic was faster.

Karmic is NOT slow by any stretch of the imagination. If Karmic is "slow" on your system, look to user error FIRST.

:guitar:

---

### Post by venkatad on 2009-10-02
> **stuart.reinke said:**
> I've noticed that Karmic moves a lot slower than Jaunty does on my machine.  Has anyone else noticed the same thing? Is this normal for alpha releases or do I need to report it. mine is much faster...i love it esp browsing is electric fast in firefox 3.5

---

### Post by jasondean on 2009-10-04
For me Karmic is faster, I have Jaunty and Karmic installed on the same machine but on different partitions. Mame for me was unusable(choppy,slow etc) on Jaunty, it was so bad that to get decent performance I had to run the windows version of Mame via Wine. On Karmic, Mame runs full speed and is fast like it was in Intrepid.

---

### Post by ToxinPowe on 2009-10-04
I have Jaunty and Karmic too, same machine. Karmic is more faster for me.

---

