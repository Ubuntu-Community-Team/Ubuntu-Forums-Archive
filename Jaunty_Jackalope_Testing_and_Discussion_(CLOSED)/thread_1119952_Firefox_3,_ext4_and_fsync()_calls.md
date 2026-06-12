---
title: "Firefox 3, ext4 and fsync() calls"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cicoandcico on 2009-04-08
as far as i can remember, soon before firefox 3 was out there were a lot of discussions regarding excessive fsync() calls, resulting in a high disk usage and lockups (of firefox itself or other apps).

at that time, the problem was partially "solved" by reducing the number of fsyncs,  developers saying that the the TRUE solution would've come only when new filesystems like ext4 would've been out. (grammar is right?)
in the meanwhile, with hardy and intrepid, people have been always experiencing firefox slowdowns and lockups. but no data loss!

ok, now ext4 is out, but the delayed allocation mode (which i think would give the promised performance boost) was on the center of another discussion, due to applications losing data. apparently, there are some patches that solve the problem - but i don't know how they work.

my question is: what's the current state? is the problem solved? or do the ext4 patches  - necessary to prevent data loss - inhibit the preformance boost? 
in that case, what should we wait for now (no polemic here ;))?

PS: can't wait to install jaunty on my box :popcorn:

---

### Post by whoop on 2009-04-08
I'm running jaunty 64bit with ext4. Firefox speed problems and hick-ups are still here, did not have any data loss even with some (deliberate) system crashes...

---

### Post by cicoandcico on 2009-04-09
bad news :(

can someone give a technical explanations (or supposition)?

---

### Post by taavikko on 2009-04-09
[http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=4](http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=4)

there's a related article on performance in kernel.
This affecting sqlite and hence firefox.

---

### Post by cicoandcico on 2009-04-10
> **taavikko said:**
> [http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=4](http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=4)

there's a related article on performance in kernel.
This affecting sqlite and hence firefox.

according to those numbers, you should get a reduction in lockups number and/or a general speed improvement when using a 2.6.29 kernel.

so, there was another problem apart the fsync() slowness...

does using 2.6.29 and ext4 speed up firefox, actually?

---

### Post by Bossieman on 2009-04-11
Mounting my Firefox profile into computers RAM solves high disk activity and makes Firefox operate flawless. 
I wrote a guide if you want to try it out: [Howto; Firefox profile in RAM for increased speed and stability ]("http://ubuntuforums.org/showthread.php?t=1120475")

:guitar:

---

### Post by amano on 2009-04-11
Just stay with ext3 for this cycle and upgrade to ext4 for Karmic.

Unless most if not all applications will be converted to use fysnc() extensivly, data loss will occur with ext4.

Only some bad cornercases are fixed at the moment (the ones when files were zero'ed, resulting in a loss of the original file and the loss of your current edit of this file).

---

### Post by cariboo on 2009-04-11
I've been using ext4 since about a week after it was available, and haven't noticed any firefox slow downs, and have only had one or two crashes due the default flash plugin. Since upgrading to the 64-bit alpha plugin, sites where Firefox was crashing no longer have any effect.

Jim

---

### Post by cicoandcico on 2009-04-17
i think i'll stay with ext3 ATM, i was just curious about the current state and what's being done to fix this boring issue

hope to have nice news with koala (2.6.30, ext4 and FF3.5)

---

### Post by cicoandcico on 2009-04-20
nevermind, i couldn't resist :)

i've just installed jaunty 64-bit (i've always installed the i386 flavour) with ext4, and the general speed seems improved... the system is more responsive, and damn it boots fast! :)

however, fas for the firefox issue, no noticeable difference. i've come to think it could also be a nvidia-related problem... the same version, on windows (as far as i can remember) has no speed problems at all.

---

### Post by psyke83 on 2009-04-20
> **cicoandcico said:**
> nevermind, i couldn't resist :)

i've just installed jaunty 64-bit (i've always installed the i386 flavour) with ext4, and the general speed seems improved... the system is more responsive, and damn it boots fast! :)

however, fas for the firefox issue, no noticeable difference. i've come to think it could also be a nvidia-related problem... the same version, on windows (as far as i can remember) has no speed problems at all.

It sounds to me that you're defining speed as the responsiveness of your interface, which may have nothing to do with the fsync problem (which I haven't noticed since the Intrepid beta, by the way). There are two crucial tweaks you should make to the closed-source NVIDIA driver.

First, you need to disable "DynamicTwinView" because it makes applications such as compiz think that your screen is running at 50Hz, which causes compiz to throttle rendering to 50fps (when it should be 60, 70, 75 or 85fps, depending on your real refresh rate). This will make all applications on your system seem visually sluggish.

Add this line to your xorg.conf in the "Device" section:
```
        Option        "DynamicTwinView"        "false"
```

Restart X for changes to take effect.

Secondly, you need to change the "initial pixmap placement" method of the driver to improve 2D performance:
```
$ nvidia-settings -a InitialPixmapPlacement=2
```

This needs to be done each time you restart X. You can add an entry to System/Preferences/Startup Applications if you like.

---

