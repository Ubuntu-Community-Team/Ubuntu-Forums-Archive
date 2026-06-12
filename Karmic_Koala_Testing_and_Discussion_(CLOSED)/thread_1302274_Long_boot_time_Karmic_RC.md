---
title: "Long boot time Karmic RC"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by humphreybc on 2009-10-26
I think this boot time is ridiculously long at over one minute on my system...

What's the command that you add to the grub boot options to update the list of boot files?

-------------------------

**EDIT:** I just found my bootchart from Jaunty. It was 24 seconds. Compared to Karmic, which is now 1 minute, 8 seconds. That's a HUGE difference.

[B]Jaunty: 24 Seconds
Karmic: 1 MINUTE, 8 Seconds[/B]

That's on a dual core, 3GB ram, 64 bit, 5400 RPM system...

I've updated the attached .zip file to include both bootcharts.

---

### Post by froggyswamp on 2009-10-26
Afaik to deliver on all ambitions previously set the devs simply didn't have enough time, hence Karmic will deliver a **stable** boot while Lynx should also make it fast + fixed artwork and other fixes.

---

### Post by Sashin on 2009-10-26
That's no excuse for a ridiculously slow boot though...

---

### Post by froggyswamp on 2009-10-26
I partially agree, but let's also consider that Karmic has received the biggest artwork overhaul ever (the win-95 icons are gone! yeeah!! + almost all of them are .svg)

---

### Post by humphreybc on 2009-10-26
Read the edit that I just added in the original post.

I don't care how much new artwork and stability they bring, an increase in boot time by 44 seconds, that's THREE times as slow, isn't acceptable.

I'm guessing something's screwed up somewhere to cause this, but I can't read boot charts.. so if someone could give me some advice that'd be appreciated...

... maybe start with the command to update the boot file locations?

---

### Post by cdahmedeh on 2009-10-26
Did you do a clean install of RC or did you update from beta ? I noticed that installing a clean RC boots up much faster than RC updated from beta.

---

### Post by humphreybc on 2009-10-26
It's an upgrade from Jaunty to Karmic RC.

I can't be bothered doing another fresh install, i'd prefer to fix the boot time as everything else is working fine. If it can't be fixed then I guess i'll have to do a fresh install next week.

---

### Post by humphreybc on 2009-10-26
I just read this from another thread regarding slow karmic boot times:

> 
In Karmic, Bootchart does not stop anymore once the desktop is shown. Instead, it continues to log boot activity until everything is loaded, hence the radical time difference between Karmic's and former bootcharts. For example, on my computer 9.04 booted in 11 seconds according to bootchart, now in 9.10 bootchart shows that the time is 1 min 15 s.

- a6jarvi


Is this true?

---

### Post by lovinglinux on 2009-10-27
I'm experiencing long boot times, but because of the artwork or gdm/kdm. My problem is with grub. I have two Karmic installations on different partitions and one generates a fast grub, while the other generates a grub that needs 23 extra seconds to load.

When I get an update that requires updating grub, if I install the updates from my main installation first then the second installation, I get the fast grub loading. If I update the second installation, then the main one, I get slow boots.

I have installed Karmic several times and it appears to me the slow grub loading time is pretty much random. Sometimes it results in a fast loading grub, sometimes it doesn't. So is not dependent on which partition is the OS generating the grub.

---

### Post by Elfy on 2009-10-27
> while the other generates a grub that needs 23 extra seconds to load.How conincidental - I had an issue wher it took about that long to get from the Grub loading ... text to actually presenting me with the menu list.

Once I had set the disk order in bios to go to the disk with grub installed it stopped taking so long.

---

### Post by dino99 on 2009-10-27
Welcome to Krappy Koala :D

---

### Post by MacUntu on 2009-10-27
> **humphreybc said:**
> Is this true?

Look at the charts and not just at the 'time' value. It's pretty obvious that Jaunty's chart shows less action than Karmic's.

And to make you feel worse - it doesn't look like your boot was finished at the end of the chart. Try increasing the 45s 'sleep'-value in /etc/init/bootchart.conf till you see the CPU- and I/O-graphs idling at the end of the chart.

On my systems there's no change in total boot time between Jaunty and Karmic, so I guess all those people reporting a significant increase in boot time are either hit by bugs or can't read their bootcharts right.

---

### Post by lovinglinux on 2009-10-27
> **forestpixie said:**
> How conincidental - I had an issue wher it took about that long to get from the Grub loading ... text to actually presenting me with the menu list.

Once I had set the disk order in bios to go to the disk with grub installed it stopped taking so long.

Thanks for the tip, but it didn't work.

It seems this issue happens when the mbr is not in the same drive as the grub folder.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

---

### Post by philinux on 2009-10-27
The bootchart on Jaunty only measures the time up to the GDM. On Karmic it is measured up to the desktop. Big difference.

The bootchart png is still being created when you see the desktop on Karmic.

---

### Post by guv999 on 2009-10-27
> **froggyswamp said:**
> Afaik to deliver on all ambitions previously set the devs simply didn't have enough time, hence Karmic will deliver a **stable** boot while Lynx should also make it fast + fixed artwork and other fixes.

If this is the case, and the boot process is working as designed, then has this been formally announced anywhere officially?   Like many others I was expecting a quicker boot on Karmic.    
In Jaunty my power on to usable desk top was 55 seconds, In karmic this has increased to 78 secs.

---

### Post by humphreybc on 2009-10-27
> **guv999 said:**
> If this is the case, and the boot process is working as designed, then has this been formally announced anywhere officially?   Like many others I was expecting a quicker boot on Karmic.    
In Jaunty my power on to usable desk top was 55 seconds, In karmic this has increased to 78 secs.

No this is not the case, that was rubbish.

---

### Post by Elfy on 2009-10-27
> **lovinglinux said:**
> Thanks for the tip, but it didn't work.

It seems this issue happens when the mbr is not in the same drive as the grub folder.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

YEa - I found that bug - full of hope I was - but it didn't help in my case as boot and / were all on the same drive/partition - the only thing that helped in my case was telling BIOS to boot the slave drive first.

Only putting this here in case someone comes looking :)

---

### Post by the.lost.one on 2009-10-27
Correct me if I am wrong but isn't that root and grub in the same partition thing applicable to only boot menu taking time to load?

Regarding reading bootcharts, well, I have measured reboot times using a clock. It could be off by a few seconds but when the time to desktop is twice as much, it is definitely a slower boot.

On the screenlet, note the minute and seconds when you hit reboot. Note it again when it loads (also note that the screenlet is not loaded later than desktop). The difference is reboot time. Do it for Jaunty and Karmic and do it a few times at least. The difference is significant esp considering faster shutdown of Karmic.

---

### Post by lovinglinux on 2009-10-27
> **the.lost.one said:**
> Correct me if I am wrong but isn't that root and grub in the same partition thing applicable to only boot menu taking time to load?

Yes.

---

### Post by guv999 on 2009-10-27
> **guv999 said:**
>     
In Jaunty my power on to usable desk top was 55 seconds, In karmic this has increased to 78 secs.

I would like to log a bug report, something I have not done for this type of issue previously.   
What type of infomration should I submit, over and above the nature of the issue?
Thanks for any guidance.

---

### Post by patrickdk on 2009-10-28
I am getting long boot times also, I was comparing the time my wifi connects, in jaunty it takes 38 seconds, and in karmic the BEST was 73, normally around 82.

I didn't have bootgraph loaded for jaunty, and the wifi connects after I login to the desktop.

I removed sreadahead and replaced with readahead-list, and boot times fell to 65seconds, then changing /etc/init/sreadahead to use readahead-list (so readahead-list didn't run parrallel but by itself) dropped it again down to 58 seconds.

---

