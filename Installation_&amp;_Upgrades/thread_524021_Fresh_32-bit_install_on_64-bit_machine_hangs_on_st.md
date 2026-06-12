---
title: "Fresh 32-bit install on 64-bit machine hangs on startup"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by colincalvert on 2007-08-12
I recently got a **Asus M2A-VM motherboard** with a **AMD 3000+ Athlon 64 Processor** to use as a media center computer. I tried installing Ubuntu 64-bit on it but the media center software I'm trying to use, Elisa, runs really bad (even with the *linux32* command) so I tried to just go with the 32-bit version of Ubuntu (since I don't really need the performance to watch some movies).

**The problem is** when I put the **32-bit live cd** in it **hangs on startup**, right about the time when it's has the tan background and is loading gnome (or x-windows...I'm not sure savvy with what exactly it's loading). Anyways, I **_can_ get the 32-bit text installer** to fully run and install Ubuntu but I end up with the same problem; with the i**nstalled 32-bit version** I'm able to **reach the login screen** and log in but it **won't go much further than loading the tan background, top nav bar and the bottom bar.** I can still move the mouse around, access the menu, click on programs (which won't start) but I'm not able to do much else.

I've installed a few times with a few new downloads and cd burns so **I know the install isn't bad**. I would even appreciate someone telling me where to look (like in a log file or something) as I've been all over Google and these forums and I can't find anyone with similar problems (seems like everyone else can get 32-bit installed on a 64-bit). I'm pretty resourcefully so even a point in the right direction would probably help me figure out the rest of my problem on my own.

Thanks for anyone's help!
Colin C.

---

### Post by clyrrad on 2007-08-12
I have very similar hardware to you, and also had a very similar error to you a while back.  It ended up being the issue was that I downloaded the wrong ISO for my hardware.

I was able to get it working with the "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)" ISO Image.

I recall reading a while back there is something with our particular CPU's that are not "Fully 64bit Compatible".   For example on my CPU AMD 2800 Athlon 64 I can NOT run Windows Vista under a virtual machine because the chip only emulates the 64bit architecture - or something along these lines.

Anyway to make a long story short, i re-downloaded the proper ISO and installed and all was dandy.

Hope this helps!

---

### Post by colincalvert on 2007-08-12
clyrrad, 

Unfortunately the '*Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)*' iso image is the one that gives me problems but is the image I'm trying to get installed.

Using the '*64bit AMD and Intel computers*' iso image I'm able to install and run Ubuntu fine I just am not able to run Elisa fine (or even ok for that matter).

Thanks for the help though,
Colin C.

---

### Post by logos34 on 2007-08-12
try the text-mode alternate desktop cd.  (On the [download page]("http://www.ubuntu.com/getubuntu/download") check the box just below green "start download" link)

---

### Post by colincalvert on 2007-08-12
logos34,

I have tried the text-mode alternate cd (both for 32-bit and 64-bit) and that's how I'm able to get the 32-bit version to install (as the live-cd won't ever load). 

The only problem is when I get the 32-bit version installed it won't ever completly load and hangs on startup (somewhere just after loading the top and bottom bars).

Thanks for the help though,
Colin C.

---

