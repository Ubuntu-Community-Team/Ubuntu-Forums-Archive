---
title: "Is newer better?"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Mr_VeRiTy on 2010-05-20
Hi, I'm new to linux, but from the stories i've read about the different releases of ubuntu i'm wondering If I should consider downgrading from  lucid to one of the more stable releases, should I?

---

### Post by patchwork on 2010-05-20
It all depends on the problems you're having.  I'm not really convinced Lucid is more/less stable than any other release at the same point in its lifecycle.  I run lucid on my laptop for about 8 - 12 hours per day, and have not experienced any stability issues.  In fact, the only issue I've run into has been a screen resolution issue which I ran into in earlier releases of Ubuntu as well, and was easily fixed by adding an Xorg.conf.

Perhaps if you outline some of the problems you're experiencing someone can help you settle them.

---

### Post by Mr_VeRiTy on 2010-05-20
Some problems are:
firefox and some other application quit unexpectedly, with no warning and no recovery of any work lost.

This isn't really a problem, but I heard that in the older versions (8.10?) you can change the gdm theme, I tried downgrading gdm in lucid but it wouldn't work.

In lucid the bootscreen is managed by plymouth and that sometimes freezes on boot, for about a minute.

these aren't big problems but are annoying nonetheless.

---

### Post by patchwork on 2010-05-20
Well, we'll start with the easier things.  

Post # 10 in this thread covers managing the bootsplash and gdm login screen appearence.
 [URL="http://ubuntuforums.org/showthread.php?t=1446949&highlight=plymouth+custom"]http://ubuntuforums.org/showthread.php?t=1446949&highlight=plymouth+custom
[/URL]
What kind of hardware are you running?

Have you already checked your logs to see what (if any) errors are thrown during boot?

It's also possible that the 'freeze' you're talking about is a scheduled fsck on your hard drive(s) (similar to a checkdisk on windows)  If this is the case, you will see it appear in the logs.

---

### Post by Mr_VeRiTy on 2010-05-20
My hardware should be good enough, as I have 4gb ram and 2.10ghz intel dual core cpu, gpu I don't know intel chipset somthing (i think) anyways I an running ubuntu on an advent roma 3000 laptop

as for the logs I don't really know what they say and under System>administration>log file viewer and in the boot section it says "(nothing has been logged yet)"
also another error I have been having is that packages in /var/cache/apt/archives kept becoming corrupt (or something) I made a topic [here]("http://ubuntuforums.org/showthread.php?t=1485581") but nobody answered, lol 

and I think fsck only runs briefly every other boot, but i'm not the expert.

---

### Post by patchwork on 2010-05-20
Look in the boot.log, the syslog, and the dmesg log.

In the syslog and the dmesg log, the string of numbers in barackets indicates the time in seconds after the kernel has statred to load, like this (15.935782 seconds):

```
lucid kernel: [   15.935782]
```

If there is a freeze, you will either see a large jump in the numbers during the initialization, or you will see many smaller, (but probably still large) jumps with a message indicating an error.  Not all messages in the log are errors, however.

---

### Post by patchwork on 2010-05-20
The problem with hardware and linux isn't necessarilly whether the specifications are 'good enough', but whether the hardware has a good set of linux compatible drivers.  The processor undoubtedly is not the problem, and the ram isn't an issue.  My best advice to you is to try running a Ubuntu 9.10 live cd for awhile, and see if the stability issues are resolved.  Yes, it will be slower when using the cd, but if 9.10 dramatically improves your experience, I'd be hard pressed to encourage you to stay on 10.04.  

9.10 will continue to be supported for some time, though not as long as 10.04.

---

### Post by Mr_VeRiTy on 2010-05-20
I have both dmesg and dmesg.0 

In dmesg in brackets Its just zeros for a while "[0.000000]" (around 80 lines) then "[    0.004005]" and rising steadily

and in syslog it just rises nornally

and i also have both boot and bootstrap.log but not boot.log

---

### Post by Mr_VeRiTy on 2010-05-20
But would you suggest downgrading to jaunty for the added use of theming in gdm (more than just the background)? 'cos I love to customize stuff

---

### Post by patchwork on 2010-05-20
I've never tried theming gdm in jaunty, so I don't have an answer for that.

---

### Post by Mr_VeRiTy on 2010-05-20
It seems I'll have to ask around :)

---

