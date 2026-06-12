---
title: "Slow boot into Lucid."
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by X-Windows on 2010-06-11
I keep hearing about how Ubuntu is supposed to be so much faster than Windows 7, but have yet to see any major difference in their boot times. I am dual-booting Windows 7 and Ubuntu 10.04 on an intel Centrino 2 processor with 4Gb of ram and both OS's take about the same time to boot. After I get to the bootmanager to select OS, if I click on Windows 7 it almost immediately goes to the GUI load screen with the windows logo. On the other hand, if I boot into Ubuntu I get a black screen for ~30 seconds before the Ubuntu logo even appears. Comparing GUI boot times, Ubuntu is clearly the winner, but they take the same time total.

 Does anyone know what is making the long black screen or how to reduce the time? I would really like to show people how fast Ubuntu really boots.

Edit: Immediatly before Ubuntu Gui starts, an message shows up for a second saying something like "Unknown adaptor version (2): You may experience some problems", it flies past so quickly that may not be verbatim.

---

### Post by X-Windows on 2010-06-12
*bump

Is this normal, all the videos I've seen of Lucid's boot time don't have this huge delay.

---

### Post by X-Windows on 2010-06-12
Ran a bootchart to see what's going on. I don't think Ubuntu is supposed to take 45 seconds from bootloader to login...

Here is my bootloader chart, is something running that shouldn't be? Would installing Ubuntu as sda1 help, currently Windows 7 is sda1.

---

### Post by Futurian on 2010-07-21
Lucid booted quickly for me after I did a clean install of it on my System76 panp5, but has become slower and slower since. After selecting the boot image from the BIOS display, I seem to spend a long time looking at a black screen with blinking cursor.

I haven't timed it, but I would not want to show this slow boot to prospective linux converts.

Any ideas?

Thanks.

---

### Post by bwana on 2010-07-23
Same here. After upgrading to lucid, my boot seems to take longer than when I was on karmic.

Dell Studio 1555

Linux geekling 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux 

My boot chart:
[http://www.flickr.com/photos/51176038@N02/4706053758/](http://www.flickr.com/photos/51176038@N02/4706053758/)

Does anyone have any ideas about 1) is this normal ? 2) if its not normal, then what is going wrong ?

As suspend stopped working when I upgraded, I would really appreciate some help .. the 1.5 minutes I have to wait until the laptop is usable is too long, so considering moving back to 9.10.

---

### Post by Joseph Schwenker on 2010-07-25
My Lucid bootup time has also become slower after time.  On my computer, I am waiting at the Ubuntu screen with the five dots for quite some time.

---

### Post by kulkarni.ankur on 2010-07-31
My boot is rather slow too and I remember it being much faster with Karmic. I see that my CPU is hardly being utilized to its full potential. Any suggestions? Here is my bootchart:

[http://img833.imageshack.us/img833/5761/kennellucid201007319.png](http://img833.imageshack.us/img833/5761/kennellucid201007319.png)

---

### Post by kulkarni.ankur on 2010-08-04
Ok. I was mounting an ntfs drive and mountall was preventing ureadahead from using its full potential. Now I dont mount that any more and I have brought down my boot time by about 15-20 seconds. It is now between 50 and 55 secs. Any further suggestions for improvement?

Here's my new bootchart: [http://img718.imageshack.us/img718/4496/kennellucid201008049.png](http://img718.imageshack.us/img718/4496/kennellucid201008049.png) 
Can someone help me optimize this further? I run gnome and have only one user and log that in by default.

---

