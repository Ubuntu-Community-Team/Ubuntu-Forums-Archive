---
title: "Boot time regressions since jaunty"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-08-25
The fastest time bootchart ever recorded booting jaunty was ~16 seconds. Granted, this was with 2.6.30. With the stock kernel I achieved ~21s. With 2.6.31 on karmic I get around 21s, before the latest batch of updates. The newest update replaces readahead with sreadahead. This adds about 9s to my boot time.

I have heard that sreadahead is traditionally much better with SSDs. My question is: will sreadahead see significant work to bring it in line with readahead in terms of performance on HDDs? Will sreadahead even remain default for karmic? Also, does anyone know the causes between the slight regression in boot time between 2.6.28 and 2.6.30? Does anyone else even experience this?

---

### Post by MacUntu on 2009-08-25
AFAIK the plan is to make sreadahead work with ordinary HDDs - no idea about the timeline. As you can see in your bootchart sreadahead isn't doing anything as it's running in the background (makes sense for SSDs, not so for HDDs). You can put it in the foreground by adding "--no-fork" to the exec-line in /etc/init/sreadahead.conf (but make sure you already have the file list at /var/lib/sreadahead/pack - my system didn't boot if not).

---

### Post by rednus on 2009-08-25
> **jmmL said:**
> The newest update replaces readahead with sreadahead.
Which update got you the sreadahead installed... I just updated the system (26/08/2009 - 00.16AM GMT).. I still only have standard readahead package.. :(

---

### Post by tekstr1der on 2009-08-25
sreadahead replaced readahead on my system per the updates today, and I also can see about 5-6 seconds added to boot time.

Unfortunately, this is only half the story when it comes to Karmic boot time regressions as the time from gdm login to desktop has more than doubled for me since intrepid & jaunty. Combined boot for me has gone from averaging 48 seconds to averaging 1:16 seconds. This is from after grub until usable desktop. I only have one panel and 5 applets, but I can shave 10 seconds off of gdm to desktop time by creating a user with one panel and one applet.

Karmic has some serious ground to make up in this area just to be on par with previous releases. It's by far the slowest booting since I got on board with Feisty. I'm definitely getting nervous that the hole is dug too deep for this release as we approach Alpha 5 and will be majorly impressed if it can get back to Jaunty boot times.

EDIT: Bootcharts mean absolutely nothing if all the time saved is added onto the other side of the login!

---

### Post by MacUntu on 2009-08-25
K, forget my --no-fork advise as it's even making the boot slower with the new version of sreadahead. Now it's: readahead (20s) < sreadahead background (25s) < sreadahead foreground (32s). [For a fair comparison I disabled GDM and stopped at the login prompt till the pack file was generated.]

---

### Post by MacUntu on 2009-08-26
Bah, I had orphaned inodes - the cleanup delayed the last boot. Retested:

* without (s)readahead: 23.1 sec.

* readahead: 20.2 sec.
- package's (outdated) boot file list: 583 files with 25473444 bytes

* readahead: 21.9 sec.
- file list extracted from pack file: 829 files with 57408165 bytes

* sreadahead: 24.6 sec.
- pack file: 829 files with 57408165 bytes

* sreadahead with --no-fork: 24.3 sec.
- pack file: 829 files with 57408165 bytes

So on this machine sreadahead is not on par with readahead yet and even slower than using no caching at all.

---

### Post by fifth on 2009-08-26
> **tekstr1der said:**
> 
Unfortunately, this is only half the story when it comes to Karmic boot time regressions as the time from gdm login to desktop has more than doubled for me since intrepid & jaunty. 

I can concur on the time to usable desktop, not with Gnome but KDE, so I guess this just adds weight to a Karmic specific issue.

---

### Post by jmmL on 2009-09-01
This hasn't got any better over the past few days. It's now taking 44s just to boot!
I've heard that the current usplash/xsplash situation is a bit of a mess. From looking at bootcharts, it appears both are still being loaded. Once xsplash completely replaces usplash, I suppose it might bring down the time a bit.

Does anyone have any links to acknowledgments from the developers? It would be nice to know that they recognise the problem.

---

