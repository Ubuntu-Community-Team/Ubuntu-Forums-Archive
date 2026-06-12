---
title: "Nvidia drivers not working"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by rapattack1 on 2010-01-06
Hi I just installed Karmic Koala and i am not able to get the Nvidia driver. It says in synaptic that it is installed already i think from what i could see when i did a nvidia search and i went into system>administration>hardware drivers and that was blank. I have installed this with the 8.04 version of Ubuntu so i knew what to look for and i am not sure where to go from here...:(

Is this something i should use? [http://www.sizzledcore.com/2009/11/02/nvidia-graphics-drivers-19042-for-ubuntu-910/](http://www.sizzledcore.com/2009/11/02/nvidia-graphics-drivers-19042-for-ubuntu-910/)
As there are so many websites with misinformation or they have malicious software i thought i should ask first.

---

### Post by dstew on 2010-01-06
The open source driver that comes with 9.10 is probably all you need. There will not be any third-party driver in the hardware drivers menu. This is different than the older versions.

If you are running an Nvidia card, the system should detect it and the nvidia driver should claim it. Look at the output of **sudo lshw** to see what driver has claimed your display adapter.

Do you have some specific problem you are trying to solve? Multiple monitors or TV-out, something like that?

---

### Post by rapattack1 on 2010-01-06
```
chable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV25 [GeForce4 Ti 4400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:fd000000-fdffffff memory:e0000000-e7ffffff(pre
```

Yeah i noticed the difference in this version though not understanding it much! I just wanted the desktop to sit within the monitors frame...it was out of it on the right hand side which seems to always happen with nvidia cards...i have had 3 machines with those cards.
Well somehow i came on the solution. I started messing with the monitors settings and it has rectified itself now.
Thanks!!!

What is tv-out for by the way? Always wondered and never understood it....

---

### Post by dstew on 2010-01-07
TV-out is for a S-video or other connector on the display adapter card that allows you to display on a regular TV. I use it to watch movies and TV shows that are on the internet.

---

### Post by rapattack1 on 2010-01-07
Is that because a TV has higher resolution than a computer monitor?

---

### Post by dstew on 2010-01-08
No, a regular TV has a lower resolution, about 480 lines. An HDTV has up to 1080 lines, simililar to medium resolution on a computer monitor. I just find it more convenient to watch a movie or TV show on the TV instead of the computer monitor.

Usually, you send the same resolution as the desktop through the TV-out connector, that is, you can "clone" the desktop to the TV screen. The detail on the TV will usually be less than what you see on your desktop -- fine print for example cannot be read on the TV, but you can see that it is there. I used the **nvidia-settings** tool to make the TV output work, plus some tinkering with the xorg.conf file (configuration for the computer display software).

---

### Post by rapattack1 on 2010-01-08
Ah ok well I only have a small tv so it won't be useful to me....interesting finding out all this stuff though so thanks for the info!!!!

---

