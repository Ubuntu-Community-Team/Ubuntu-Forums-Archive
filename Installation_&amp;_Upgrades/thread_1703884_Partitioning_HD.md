---
title: "Partitioning HD"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by Vega1184 on 2011-03-09
[FONT=Arial]Hi all[/FONT]
 
[FONT=Arial]I new to Ubuntu (and linux for that mater) and need some advice on partitioning. I am building a small ruggedized computer for my boat, it will be used as a navigation system and HTPC. I am using Ubuntu 10.10. AMD64 edition.[/FONT]
 
[FONT=Arial]System specs:[/FONT]
[FONT=Arial]Case &#8211; Homemade aluminum[/FONT]
[FONT=Arial]Motherboard/CPU - Gigabyte E350-USB3 (AMD Fusion),[/FONT]
[FONT=Arial]Ram &#8211; Corsair 4 GB DDR3,[/FONT]
[FONT=Arial]HD &#8211; 2.5 WD Scorpio Black 500 Gb,[/FONT]
[FONT=Arial]TV Tuner &#8211; Hauppauge Win-TV 1250,[/FONT]
[FONT=Arial]WIFI &#8211; Engenius EOC 2611 + 8 Db antenna[/FONT]
[FONT=Arial]Power Supply &#8211; Mini-box 250W M4-ATX (6 to 30V input), and[/FONT]
[FONT=Arial]Monitor &#8211; Shark 10&#8221; touch screen + another 20-22? inch for inside.[/FONT]
 
[FONT=Arial]I am used to partitioning in windows XP using Partitionmagic and my home system (300 GB+150 GB) is set like this:[/FONT]
 
[FONT=Arial]C: removable[/FONT]
[FONT=Arial]D: O/S and programs &#8211; 30GB[/FONT]
[FONT=Arial]E: Docs &#8211; 20GB[/FONT]
[FONT=Arial]F: Games/other software &#8211; [/FONT][FONT=Arial]40GB[/FONT]
[FONT=Arial]G: Music &#8211; 60GB[/FONT]
[FONT=Arial]H: Photos/Video &#8211; 150GB [/FONT]
[FONT=Arial]K: back up &#8211; 150GB[/FONT]
 
[FONT=Arial]I have been reading up on Ubuntu but have some questions about partitioning. I have been using the guide here [[COLOR=#800080]https://help.ubuntu.com/10.10/installation-guide/amd64/directory-tree.html[/COLOR]]("https://help.ubuntu.com/10.10/installation-guide/amd64/directory-tree.html"). but need more help with definitions and with to group together and which should have their on partition. [/FONT]
 
[FONT=Arial]What I have got so far is:[/FONT]
[FONT=Arial]/boot - 500 MB[/FONT]
[FONT=Arial]/usr &#8211; 6 GB or should this be larger, I tend to collect a lot of software?[/FONT]
[FONT=Arial]/var &#8211; 4 GB (??)[/FONT]
[FONT=Arial]/tmp &#8211; 500 MB[/FONT]
[FONT=Arial]Swap &#8211; 8 GB[/FONT]
[FONT=Arial]/home &#8211; Whatever is left[/FONT]
 
[FONT=Arial]I think I am missing / but not sure.[/FONT]
 
[FONT=Arial]Does this sound right or am I right out to lunch here? I sort of wanted to divide the O/S from the other software and the static stuff (i.e. music, video, charts, etc).[/FONT]
 
[FONT=Arial]Also have 16GB USB for critical back up. [/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]thanks [/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Glenn[/FONT]

---

### Post by mikewhatever on 2011-03-10
```
What I have got so far is:
/boot - 500 MB
/usr – 6 GB or should this be larger, I tend to collect a lot of software?
/var – 4 GB (??)
/tmp – 500 MB
Swap – 8 GB
/home – Whatever is left

I think I am missing / but not sure.

```

Not really sure why you want to make so many separate partitions, but since you do, I'd advise the following corrections:
/usr - 25-30GB.
Swap - no more then 4GB, and that only to be able to suspend to disk.
/ is necessary, about 1GB should suffice.

---

### Post by Dutch70 on 2011-03-10
Welcome to UF Vega1184. Nice to see someone is doing some homework before installing an OS, but I tend to agree with mikewhatever, you may be over doing it just a little. :) Unless you have a specific reason to. 

This is all debatable, but a good set up to start with is 3 partitions. 

1. for "/" (root) This is your sysytem or Ubuntu itself.
2. for /home, this is similar to "documents & settings" in windows.
3. for Swap, equal to your physical RAM & works like a pagefile.

If you want to separate everything into partitions instead of folders, then that's totally up to you. If you create a partition for /home, there is not even really a reason to have a separate partition for "back-ups"  as /home will serve the same purpose, because "/" or (root) is in it's own partition, even if you re-install, you won't lose your data.

Imho a good partitioning scheme for your set up would be...

20-30 GB for "/" (root) 
4GB for Swap
the remainder for /home

_

---

### Post by Vega1184 on 2011-03-10
[COLOR=black][FONT=Verdana]Well thanks guys[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]But my thinking was since this a ruggedized computer and it will get knocked about the more partitions the better and I will have complete copies of priority software on the USB Drive.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]The partitions I finally went with are:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]/boot - 500 MB[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]/ - 10 GB[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Swap &#8211; 4 GB[/FONT][/COLOR]
[FONT=Verdana][COLOR=black]/usr &#8211; 20 GB [/COLOR][/FONT]
[COLOR=black][FONT=Verdana]/var &#8211; 4 GB [/FONT][/COLOR]
[FONT=Verdana][COLOR=black]/tmp &#8211; 4 GB[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]/home &#8211; Whatever was left[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]It may not be the most logical, but it's up and running.:) Install when pretty smoothly, just trying to sort out touch screen.[/FONT][/COLOR]
 
Glennn
 
A couple of shots(Bad resize) of system.

---

### Post by Vega1184 on 2011-03-10
Better resize.

---

### Post by Dutch70 on 2011-03-10
> **Vega1184 said:**
> Better resize.

Nah, I think the sizes you settled on are fine...lol j/k. 
(and I'm not familiar with sizing those partitions btw)

Thanks for that, I can see them now & I'm definitely learning something as well. So keep us up to date on this thing. 
Where are your vents? It's gonna need a lot of air circulation out in the hot sun, unless you're putting a water cooler or something on there.

---

### Post by psusi on 2011-03-10
Why do you want to break it into separate partitions?  For most people a single partition is plenty.  You certainly don't need one for /boot, /usr, /var, and /tmp.  Some people like to have a separate /home, but even that has no benefit if you aren't dual booting other Linux distros.

---

