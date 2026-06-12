---
title: "Serious CPU load bug with Nvidia 8200 platform still persists"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Lem on 2008-10-03
I tried Alpha 2 and experienced huge CPU loads on idle, swapping between processors.
The latest Beta has the same problem - see attached. Banshee isn't playing in this shot. Nothing running other than the screenshot app.

I'm running an AMD 4850e on the nvidia 8200 platform (jetway nc62k)

Hardy doesn't exhibit this behaviour.

---

### Post by philinux on 2008-10-03
What's going on under the processes tab?

---

### Post by Lem on 2008-10-03
Nothing hogging the CPU there. I also tried the 173 driver as that's what I'm using in Hardy but no different. Flash video playback was also terrible. I have a feeling this is linked to the nvidia drivers. Might try using the drivers from the nvidia site instead as I did for Hardy.

---

### Post by psyke83 on 2008-10-03
> **Lem said:**
> I tried Alpha 2 and experienced huge CPU loads on idle, swapping between processors.
The latest Beta has the same problem - see attached. Banshee isn't playing in this shot. Nothing running other than the screenshot app.

I'm running an AMD 4850e on the nvidia 8200 platform (jetway nc62k)

Hardy doesn't exhibit this behaviour.

1. The Nvidia 8xxx series has well known, serious performance problems with the default driver settings. You *must* use the 177 driver, and look at this thread to apply the appropriate configuration: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

2. Gnome System Monitor is an awful, awful method to gauge CPU usage. The process monitor hogs the CPU/graphics card due to the cairo rendering (which  isn't surprising if you haven't configured the graphics driver optimally). Use something simpler, like top or htop.

3. The version of Flash in the repository is outdated and has severe performance problems for everyone. If it were possible, I'd be hoarse from repeating myself so many times, so please, simply do a search for Flash & PulseAudio and you'll find the answer.

---

### Post by plun on 2008-10-03
Maybe to wait a little...  :)

I am just testing the new kernel with nVidias 177.78 driver and its excellent.

It should appear soon and hopefully also the new driver.

The nVidia URL which psyke83 posted is nevertheless important. 

Also to use latest Adobe Flash version, RC.

---

### Post by hdhrnova on 2008-10-04
> **plun said:**
> Maybe to wait a little...  :)

I am just testing the new kernel with nVidias 177.78 driver and its excellent.

It should appear soon and hopefully also the new driver.

The nVidia URL which psyke83 posted is nevertheless important. 

Also to use latest Adobe Flash version, RC.

I can confirm the same problem.  Using a the very popular and CHEAP (~$450) Compaq Presario CQ50-115NR.  8200M video.  AMD Turion RM-70 Dual Core.  Seems to be linked to Intrepid. Using 8.10 Beta.  

Have tried this driver in 8.04 and performance is good.   With 8.10 Beta you can see the process /usr/X11R6/bin/X always using lots of CPU for easy stuff like moving the Windows around.  Here is a test. Run htop in a xterm and move it around.. watch X CPU time go nuts in the X process.

177.78 is definitely helped things a bit compared to 177.76.  But it still is hogging CPU.  8.04 did not have this problem.

So close...  BTW, if anyone else has this laptop.  You must do a TEXT based Intrepid Beta install, a GUI install fails to support the 8200 GPU.
After the install completes. go into /etc/X11 and copy the xorg.conf failsafe file over /etc/X11/xorg.conf.  Then reboot.  From there 8.10 will detect the video and allow you to install the 177 beta driver.
Also, set you Audio configuration to use OSS instead of ALSA.

We have come a long way on this laptop since 8.04.  Just this video problem left which we seemed to have gone backwards on.

---

### Post by hdhrnova on 2008-10-04
1. ok.. I did some more research and I want to correct a few things I said.
Looks like running htop in a Terminal and moving around the terminal on the screen to see the X server load go up is probably related to the terminal text corruption that others have posted about on the nvidia forum.

2. Looks like Flash playback in Firefox is a problem in general in Intrepid and other are looking into it. Not so much specific to the Nvidia driver.

3. Turns out my other video playback benchmarks are gated by some kind of Network Manager problem.  I tried both both my wired 1Gbit link and my 802.11g and both throughputs are terrible. There seems to be a periodic delay every 5 seconds with both.  I moved the video to my hdd and it played fine.

4. I ran gtkperf and performance seems to be very good.

So I think there are many things wrong which I tought were related to video performance.  But it seems that the problems are elsewhere.

sorry about the false alarm. We will sort it out.  Now, I am off to figure out how to shut off the roaming Network manager mode.  If anyone has any ideas let me know. Thanks

---

### Post by plun on 2008-10-04
Yes and therefore its important now that everyone is running latest kernel
latest nVidia driver and latest Adobe Flash version. (IMHO)

Networking and Samba is a complete mess and NM 0.7 got a bunch of bugs.

Just to sort this out and bugs must be read or filed.

nVidias thread must be read.

---

### Post by hdhrnova on 2008-10-04
> **plun said:**
> Yes and therefore its important now that everyone is running latest kernel
latest nVidia driver and latest Adobe Flash version. (IMHO)

Networking and Samba is a complete mess and NM 0.7 got a bunch of bugs.

Just to sort this out and bugs must be read or filed.

nVidias thread must be read.

yep.. I read the nVidia thread..  got latest everything.  Network Manager is broken. confirmed.  I removed my wired network card from its management and am playing back 1080i HD video perfectly at 30% load.  The CPU is even scaling back to 500Mhz vs 2Ghz most of the time. With the Network Manager managing my wired connect it was very very broken. Couldn't even do 480i without a skip every 5 seconds.

ok cool.. looking forward to the Network manager fix.  Interesting you said Samba is broken too.. I noticed that was a bit low as well. only getting about 5MB/sec transfers even with the Network manager taken out of the picture. That helped clear that up for me too.

awesome.. Thanks again.

---

### Post by plun on 2008-10-04
> **hdhrnova said:**
> y
ok cool.. looking forward to the Network manager fix.  Interesting you said Samba is broken too.. I noticed that was a bit low as well. only getting about 5MB/sec transfers even with the Network manager taken out of the picture. That helped clear that up for me too.



Well, this is the challenge with testing...:D

About networking I filed a overall bug because I cannot identify which package, but all developers work "downtown" with his/hers package...
At least 20 packages directly involved.

But now we are OT...:)

---

### Post by Lem on 2008-10-04
I tried the very latest beta, and also the tweaks described above which did abate a little of the CPU load and also caused some windows not to display properly.

In either instance I still get a lot more load at idle than with my Hardy setup. As this is a media centre mainly composed of heatsinks and minimal fan instrusion, I shall sit this one out until Intrepid stops cooking my box! :)

---

### Post by plun on 2008-10-04
> **Lem said:**
> I tried the very latest beta, and also the tweaks described above which did abate a little of the CPU load and also caused some windows not to display properly.

In either instance I still get a lot more load at idle than with my Hardy setup. As this is a media centre mainly composed of heatsinks and minimal fan instrusion, I shall sit this one out until Intrepid stops cooking my box! :)

Quote from psyke83

> 3. **The version of Flash in the repository is outdated** and has severe performance problems for everyone. If it were possible, I'd be hoarse from repeating myself so many times, so please, simply do a search for Flash & PulseAudio and you'll find the answer.

Have you done it  ?  

This is the thread

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)


I have great performance on a 7600GS card.

---

### Post by Lem on 2008-10-06
I didn't bother with the flash update yet as I doubt it has much influence on idle loads.

---

