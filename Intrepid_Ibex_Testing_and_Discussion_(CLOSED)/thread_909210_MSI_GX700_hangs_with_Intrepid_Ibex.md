---
title: "MSI GX700 hangs with Intrepid Ibex"
date: 2008-09-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bobya on 2008-09-03
Hello guys, 
I have this really strange problem. I have a laptop MSI GX700 and I am using Intrepid Ibex on it. I had no problems with the machine before coming to the new kernel, or maybe before starting to use my wireless under Linux. Anyway, the problem is that after a couple of hours, sometimes , 1 hour, 2 hours, it's different but usually it is after around 2 hours the machine hangs totally and the NumLock and ScrollLock leds start flashing. I suspect the problem could be somewhere between the new kernel and the MSI compatibility :) but I can't find anything in the logs after a cold reset. It could also be caused by my wireless card because I started using it , just around the same time when I changed the kernel.
The main thing I want to ask you is how can I debug this problem, is there a way to start a more thorough trace on the kernel, so that I can see what seems to be the problem after the reset.

Some more info: I have no problems under windows (Vista) and the problem is reproducible under Fedora 10 Alpha 1 , and it even hangs faster under Fedora , which is kind a funny :)
Any suggestions on how to find the cause of the problem are welcome. Thanks a lot for any help given.

---

### Post by bobya on 2008-09-04
:arrow:

---

### Post by bobya on 2008-09-05
Hi guys, Now I am pretty sure that the problem is in the wireless card driver. The laptop doesn't hang under windows, and it also works under ubuntu when the wireless is switched off. The card is intel wireless adapter and the driver for it is iwlagn. is there a way to overcome the problem? do you think that I can use ndiswrapper instead and install the windows driver?

---

### Post by fahree on 2008-10-11
I can't tell whether or not it's due to the wireless driver, but as soon as I login to KDE (but no sooner), kubuntu-fr 8.10 amd64 freezes with the a graphics card crash: the screen is in text mode with funky characters all over, no keyboard, no ping, machine dead.

I tried logging in KDE after having disabled the wireless driver (from a console login), and it still crashes. (note: graphics card is a NV 8600GT.) The X server itself looks like it's working: it is indeed working on the liveCD, and working enough to display kdm. So I have no idea what crashes.

---

### Post by fahree on 2008-10-11
Note that on same machine, 8.04.01 seems to work well. I'll stick to that for now.

---

### Post by fahree on 2008-10-11
I spoke too fast. 8.04.01 works better: it only crashes (with a blank screen) when I logout...

That's great progress in my book.

(Note also that 8.10's initial graphic screen is garbled during bootup, but that's only a cosmetic problem.)

jockey-kde just prompted me to install the nvidia drivers under 8.04.01. We'll see what gives...

Note: jockey-kde then complained I was not root and had to restart it with ksudo or such -- but didn't tell me its name was jockey-kde, so how was I to know? Doing a pstree before and after I closed the window told me.

---

