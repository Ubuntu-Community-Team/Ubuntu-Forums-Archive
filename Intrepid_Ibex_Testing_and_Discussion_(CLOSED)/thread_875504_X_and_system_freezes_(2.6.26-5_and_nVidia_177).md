---
title: "X and system freezes (2.6.26-5 and nVidia 177)"
date: 2008-07-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aikishugyo on 2008-07-30
I've noted that on my AMD64 system, the latest 2.6.26-5 kernel together with nVidia 177 drivers works, but invariably freezes the system (no remote ssh possible) after some period (from 30 minutes to 2 hours in my experience over the last two days).

Operations I carried out at time of freeze included web browsing with Firefox, writing a CD (gah!), and browsing with Opera shortly after completing a download of an update. I don't know if the freeze would happen if I did nothing at all, since I do not have the time right now to "do nothing".

I haven't had time to check operation with the 2.6.26-4 and 2.6.26-3 kernels, plan to do that today if work conditions permit the time. I'll also have a look at the X logs and post here in case anything interesting is found. This is a very preliminary report!

Regards, Gernot

---

### Post by autocrosser on 2008-07-30
I have been having the same issues with the -3 & -4 kernels----the -5 is "better", but still doing it. I have not checked Launchpad about this, but I am sure that we are not the only ones. I am running a Core Duo Extreme 3.4 & the 177 driver, so I would think that Nvidia factors in there.......

I will look for bugreports on Launchpad & see if it well reported--if not, I will start one & post back---in any case, will post findings.

---

### Post by vhaarr on 2008-07-31
I'm freezing as well! It has happened for a long time now, running with the nvidia driver.

The system just freezes completely and if I am playing any music at the time, the last 0.1 seconds of the music repeats infinitely. Screen locks up completely and the only thing that works is a hard reboot.

Nothing in any system logs about it. It happens at LEAST once per day. Very annoying if I forget to save whatever I'm working on, and it can't be good for the hardware either I guess.

---

### Post by autocrosser on 2008-07-31
OK--take a look at: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/251430](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/251430)

I think we could add some info there......

---

### Post by Trueno22 on 2008-07-31
It is happening to me as well, but only on 2 cores.  2 of my cores stay locked at 100% load and the other 2 are normal.  Thank god for quads.

---

### Post by aikishugyo on 2008-07-31
Just to add info on my system: I have two 2.2GHz dual-core processors in my system. And ominously, Debian unstable with 2.6.25-2 kernel and the nVidia 173 binary blob also froze today for I think the first time, plus the DVD multidrive gives a write error whenever I try to write something. It cannot be excluded that I have some hardware problem in addition to whatever might be afflicting the Ibex software.

---

### Post by DavidONE on 2008-09-09
I'm suffering occasional random freezes too.  Running 2.6.27-x / nVidia 177 on Core 2 Duo.

The freezes can happen immediately on Gnome startup without me touching the mouse or keyboard, or they happen an hour later while I'm browsing / whatever.  Or not at all.

Any suggestions on troubleshooting?


/edit to correct spelling

---

### Post by jaymode on 2008-09-09
You may want to try disabling C1E in your BIOS. That helped solve some issues for me.

Other than that, I have read that the 173 nvidia driver is more stable.

---

### Post by plun on 2008-09-09
> **DavidONE said:**
> 

Any suggestions on troubleshooting?

nVidias "stability" thread:
[http://www.nvnews.net/vbulletin/showthread.php?t=58498](http://www.nvnews.net/vbulletin/showthread.php?t=58498)

Also this one can be useful for performance
[http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

---

### Post by DavidONE on 2008-09-09
jaymode, thanks - I've disabled C1E and back in Ubuntu for an hour without freeze so far.  However, I did a little research and found that [disabling C1E also stops EIST which means I don't get power saving features]("http://forums.extremeoverclocking.com/t259119.html").  Although [another thread doesn't mention that but does suggest I'm losing some power saving function]("http://forums.techpowerup.com/showthread.php?t=61174") - which I don't want to lose.

Is this issue a known one and waiting a fix from nVidia do you know?

---

### Post by jaymode on 2008-09-09
Please see this thread:

[http://ubuntuforums.org/showthread.php?t=900286](http://ubuntuforums.org/showthread.php?t=900286)

I am not sure if this is an nvidia bug or a kernel bug. I do not recall having the issue with my ATI card, so it may be a combination.

I do not believe you lose speedstep with C1E disabled, you just lose an extra low power state.

---

### Post by DavidONE on 2008-09-10
My machine froze again - with C1E disabled.

plun, I looked at [http://www.nvnews.net/vbulletin/showthread.php?t=58498](http://www.nvnews.net/vbulletin/showthread.php?t=58498) again and some of the recommendations I don't want to use ('idle=poll' will make CPUs run hot, 'maxcpus=1' cripples the machine) and others on that page do not apply to 2.6.27 kernel.

Not sure what to try next other than wait for a new kernel / new nVidia driver and hope it's fixed.

I've added note to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260639) + [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/251430/](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/251430/).

---

### Post by jaymode on 2008-09-10
What about trying the 173 nvidia driver? Is there a reason why you would not want to do that?

---

### Post by DavidONE on 2008-09-10
I've switched to 173 - see how that goes.  The only reason I don't want to use 173 is that I assume there are performance / bug fixes in 177.

---

### Post by jaymode on 2008-09-13
Any update on freezing with the 173 driver?

---

### Post by DavidONE on 2008-09-15
I think it was OK - I didn't get a freeze with 173, although I didn't spend very long using it.  I also tried switching back to 177 with the recent kernel update - that froze again.

I've been away a few days, so will play some more in the next day or two.  I'll update this thread as necessary.

---

### Post by DavidONE on 2008-09-23
Update: looks like the problem is fixed for me. Presumably one of the recent kernel or nVidia driver releases fixed it.

---

### Post by jaymode on 2008-09-23
Using the 177 driver your issues have been fixed?

---

### Post by DavidONE on 2008-09-24
Yes, 177 has been good for the past week - until last night with a rebuild of 2.6.27-4 and it locked up again.  I'll try again later.

---

### Post by DavidONE on 2008-10-14
Still getting occasional, random lock ups with all updates to date.  

Given how close to release we are ([https://wiki.ubuntu.com/IntrepidReleaseSchedule](https://wiki.ubuntu.com/IntrepidReleaseSchedule)) I'm getting a little concerned that this has not been fixed.

Any one else suffering still?

---

