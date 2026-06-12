---
title: "What's up with boot-up speed?"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-02-22
Installed today's x64 daily build and it boots in 27 seconds.
I know ppl don't like to hear this but it looks like it won't make it in 10 seconds for Lucid, ppl will say it's early to judge but I disagree, it's time if not a bit late already.

I hope I'm totally wrong?

Pentium D 3.4Ghz each core, 4GB ram.

---

### Post by anders_c_ on 2010-02-22
The 10 seconds is supposed to be on a SSD.
And also, are you using automatic login? I think 10 seconds is from grub to login screen, not usable desktop.
Not sure about this though.

---

### Post by Jay_Bee on 2010-02-22
10 seconds is the target for some Dell netbook with SSD hard drive. 
Between 20 to 30 seconds is expected for mechanical hard drive.
Boot times are almost all about the speed of the hard drive, processor and ram don't have as much impact on it.

---

### Post by andrewabc on 2010-02-22
> **kahumba said:**
> Installed today's x64 daily build and it boots in 27 seconds.
I know ppl don't like to hear this but it looks like it won't make it in 10 seconds for Lucid, ppl will say it's early to judge but I disagree, it's time if not a bit late already.

I hope I'm totally wrong?

Pentium D 3.4Ghz each core, 4GB ram.

I get 6 seconds on good SSD ubuntu 9.10.

The reason why people won't get 10 seconds on high end systems is because they are running crappy 7200 or 5400 RPM hard drives.

I'm sure we'll see lots of laptop owners complaining of this even though they have 8mb cache 5400RPM hard drives limited to SATA I speeds.

also you don't state how you measure time. Was it stop watch from power button to usable desktop, or bootchart?

---

### Post by diebels on 2010-02-22
The 10 seconds goal is from grub to desktop with autologin.  The bootup speed of my laptop with a 5400rpm drive has dropped from about 1 minute to about half a minute.  Thats a good improvement, it looks much better during bootup as well.

---

### Post by 23meg on 2010-02-22
10 seconds is a rough boot speed aim for a specific piece of reference hardware (a Dell netbook), which has an SSD drive. It doesn't mean every machine is supposed to boot in 10 seconds.

---

### Post by kahumba on 2010-02-22
> **andrewabc said:**
> I get 6 seconds on good SSD ubuntu 9.10.

The reason why people won't get 10 seconds on high end systems is because they are running crappy 7200 or 5400 RPM hard drives.

In other words the message about fast boot-up was just overrated hype and the HDD folks won't see a sensible difference and it only applies to SSD where there's no need to improve it anyway (according to your 6 secs)? Hmm what is it all about then? A tiny improvement? That's it?

ps: i use autologin and 7400rpm as almost all others

---

### Post by Merk42 on 2010-02-22
> **kahumba said:**
> In other words the message about fast boot-up was just overrated hype and the HDD folks won't see a sensible difference and it only applies to SSD where there's no need to improve it anyway (according to your 6 secs)? Hmm what is it all about then? A tiny improvement? That's it?

ps: i use autologin and 7400rpm as almost all others

No, the goal of 10 second may have been for SSDs, but the optimizations will mean a faster boot for everyone.

Also Karmic already had some of those improvement implemented, thus andrewabc's 6sec boot

---

### Post by kahumba on 2010-02-22
Ok, for me Karmic boots slower than Jaunty did and roughly saying Lucid so far just equals Jaunty boot-up speed. So for non-SSD users (which is the (overwhelming) majority) the Lucid bootup time is just that of Jaunty. Well, thanks at least for this, but I expected more (not that I deserve it or contributed..).

ps: now I wonder whether win7 also boots that fast on SSD

---

### Post by teh603 on 2010-02-22
> **kahumba said:**
> Ok, for me Karmic boots slower than Jaunty did and roughly saying Lucid so far just equals Jaunty boot-up speed. So for non-SSD users (which is the (overwhelming) majority) the Lucid bootup time is just that of Jaunty. Well, thanks at least for this, but I expected more (not that I deserve it or contributed..)I have the same problem on Karmic. I can boot to Jaunty in less than 30 seconds, while the boot time for Karmic seems like its well over a minute. Half of which is spent at the sitting pulsing white ubuntu logo and the other at some kind of slow-moving thermometer bar. With Jaunty there's only one splash, and its a lot faster.

---

### Post by MacUntu on 2010-02-22
Here are some numbers from the target machine (and the same one with an ordinary HDD):

[http://people.canonical.com/~scott/daily-bootcharts/](http://people.canonical.com/~scott/daily-bootcharts/)

The HDD system boots 7 seconds faster than three months ago!

---

### Post by philinux on 2010-02-22
7200 HD. I was getting 1.05 with karmic and Jaunty.

I now get 30 seconds. I'd call that a brilliant improvement.

---

### Post by ranch hand on 2010-02-22
The one install that I have of 10.04 that doesn't have the "plymouth problem for some reason (plymouth loves it) is booting in 39 seconds with password login and booting from an external enclosure (usb on esata) with WD 7200 rpm drives.

I would say that is pretty darned good.

---

### Post by andrewabc on 2010-02-22
Hmm, for everyone saying they used to get 1 min, and are now getting 1/2 that time. This is using bootchart?

Bootchart in 9.10 introduced +45 delay. 10.04 as far as I'm told it got rid of 45 second delay (otherwise 30 second bootchart not possible).

To the person saying they got 1.05 in jaunty and karmic and now 30 sec in lucid, I'm not sure how that is possible, unless there was a misconfiguration that caused 30 second delay in karmic (Karmic did not have +45 second delay in bootchart).

To reiterate: 45 second delay in karmic caused lots of confusion when people are comparing bootcharts. I see beenfit of it (not really +45, +10 would have been fine) but not worth the confusion.

Yes the 10 second boot was mostly marketing. But they did set a target for specific hardware. Doesn't mean it will be the same for everyone. Biggest aspect is hard drive input (SSD speed). Good SSD gets 250mb/s read. Poor (old or laptop) hard drive gets 60mb/s read.

---

### Post by MacUntu on 2010-02-22
It IS confusing for people not following the threads.

_Pre-Karmic_: Bootchart's 'time' value = GRUB -> GDM. Everything was fine.

_Karmic_: Bootchart's 'time' value =  GRUB -> (AFAIK) some 'rc' process + 45 sec. 'Boot time' got redefined as time needed from GRUB to a usable desktop (autologin enabled). Ignore the 'time' values, just look at the graphs: system idle = system booted.

_Lucid_: Bootchart's 'time' value =  GRUB -> usable desktop. Everything's fine.

---

### Post by Jay_Bee on 2010-02-22
I just use my stopwatch for measuring boot times, I start counting when I press enter on grub menu and stop when nautilus shows desktop icons or network manager connects.
That way I avoid this confusion, but I only do this once per release, so... probably not a good idea for frequent testing.

---

### Post by diebels on 2010-02-22
I've been using autologin for several years, and never understood the concept of timing up to the gdm login screen.  No other competing operating system was advertising such silly measurements. 

The 30 second grub to desktop I get with my 5400rpm laptop drive today(stopwatch) is speed I haven't seen since playing with gentoo years ago and stripping off startup services.

---

