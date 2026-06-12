---
title: "Help! Monitor &quot;No Signal&quot; on Bootup"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by ohmysql on 2012-10-01
I have a desktop with dual monitors. It has been working fine for a little while.

Then this morning, I booted up and there is no signal from either of them. No signal during BIOS, no signal during GRUB. No signal at all. 

I can hear the BIOS beep, and then grub beeps, too. I couldn't tell you if I get to the Ubuntu login screen because I don't have a sound assigned to that event.

Any clues or advice would be much appreciated. I can't change almost any settings though, because I never get a monitor signal.

Possible culprits? I would think "maybe one of the cables came loose" except that wouldn't explain why both monitors go black simultaneously at start-up. Last night both monitors were working by the time we got to the Ubuntu login screen.

I've had this problem once before, but it cleared up after a day or two.

Possible culprits: nVidia driver? (can that affect the BIOS?) xorg config file (can that affect the BIOS?). I built this computer myself... do I need to more firmly plug in my video card? Since I have a motherboard video card as well as one I installed, I wonder if plugging one monitor into the motherboard will help anything....

Even if you don't have any advice, please answer my questions about how the video file and monitor settings affect the BIOS!

Like, Ohhhh MySQL!

---

### Post by windscape on 2012-10-01
Hi,

Since the BIOS isn't outputting anything, it more than likely caused by loose cables, loose video card, or BIOS settings. I'd start by removing the discrete video card and try the integrated one. You also want to consider resetting the CMOS BIOS settings.

AFAIK, the video file (driver?) don't affect the BIOS, nor do the monitor settings.

---

### Post by ohmysql on 2012-10-01
Hi there,

Thanks for the reply. I certainly appreciate everyone who puts their two cents in.

I certainly agree that it's more likely caused by cables. It seems like linux shouldn't have the ability to screw up the BIOS.

Still, something is strange. For instance, after tightening the cables, I just booted up to no signal. I unplugged one monitor ... it was blank until I restarted. Then it worked. When I logged in, the system froze - which is wasn't doing before. I plugged the other one, it was blank (BIOS and all) until I rebooted.

I know it seems unlikely - I'm just having a hard time believing that this is entirely a hardware problem. It seems like a software problem to me - BIOS through Ubuntu.

I thought that changing the primary monitor in the xorg settings changed the primary monitor in the BIOS - not so?

---

### Post by ohmysql on 2012-10-01
Good news to report. If I boot up with one monitor at a time, it seems to like that better.

That said, obviously, I'd like to boot with both. And I don't think Linux likes my ViewSonic monitor very much. It behaves much better with the other one.

Even when I autodetect it and change the xorg file to match it, I still get a lengthy error message when I start up.

And when I booted last time, I saw BIOS ***then*** it froze after the GRUB. And I mean it froze totally - I didn't hear the startup sound, so it wasn't just no image to the monitor. It was a blank screen. Totally dead in the water.

Ideas on how to get rid of the giant monitor configuration error message when I boot up?

---

### Post by ohmysql on 2012-10-06
This seems to have gone away but I really didn't do anything.

I suspect it will be back soon...


:popcorn:

---

