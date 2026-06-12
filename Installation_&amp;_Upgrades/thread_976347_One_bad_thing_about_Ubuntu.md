---
title: "One bad thing about Ubuntu"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by khelben1979 on 2008-11-09
I have tried Ubuntu 8.04 on my brothers computer and I'm very dissipointed in the way it handles partitioning.

Why has the installer been made in the way that it doesn't allow me to choose how I want to partition up the harddrive for myself? :-k

This is something I can do on my Debian system.

---

### Post by 73ckn797 on 2008-11-09
I have been able to select for manual partitioning in the setup process. This was when installing to a drive with another OS installed. You could also use Gparted from the live CD and set it up how you like.

---

### Post by pastalavista on 2008-11-09
> **khelben1979 said:**
> Why has the installer been made in the way that it doesn't allow me to choose how I want to partition up the harddrive for myself? ....

If you use the manual option you can format it however you want, unless you have data (or another OS) in the way.

---

### Post by bulldog on 2008-11-09
I tend to agree with you,BUT not everyone is a 'pro' in making partitions when installing an OS.
I think they have tried to make it as simple as possible.

Someone who is experienced enough,will find their way to partition the hdd to their likings.

---

### Post by khelben1979 on 2008-11-09
I see.

I do want to mention that when I chose manual partitioning which was available from the standard installer, that it didn't accept my partitioning and actually forced me to default settings.

Maybe that GParted software solves that issue, then. Interesting.

---

### Post by IshikawaNakano on 2008-11-09
> **73ckn797 said:**
> You could also use Gparted from the live CD and set it up how you like.

Thats how I do it.

If you can't get the live CD to boot you might also use [System Rescue CD]("http://www.sysresccd.org/Main_Page") to format your Hard Disk. It has Gparted and fdisk.

---

### Post by aikiwolfie on 2008-11-09
I've always been able to partition the drive anyway I liked. The partitioning software will even resize and move partitions. This sounds like simple user error.

If you want to mess with partitions fire up Gparted and have a brows around and see how things are laid out and how they work. You won't break anything if you always select "cancel". So it's fairly safe.

Then when you're installing Ubuntu select "manual" for partitioning and you should be able to partition the drive anyway you like. Remember you need to select your mount points for / (root as in root file system and not Root user). The / partition must also be formated. I recommend using ext3. That seems to be the Ubuntu prefered formating.

I also recommend setting up at least three partitions. One for / (root file system where all the technical bits live) one for /home where your home folder and data will live. And finally a swap partition. For the / (root file system) you should allow at least 10GB. For the swap partition my rule of thumb is to make it twice the actual amount of RAM. Then just make the rest your /home partition.

Now obviously if you have a lot of RAM you're not going to need to follow my rule of thumb. For example if you have 8GB of RAM, clearly a 16GB swap partition would just be wasted hard drive space. But if you have 2GB of RAM then a 4GB swap partition is a good size. You could however get away with as little as 500MB.

---

### Post by khelben1979 on 2008-11-09
> **aikiwolfie said:**
> Now obviously if you have a lot of RAM you're not going to need to follow my rule of thumb. For example if you have 8GB of RAM, clearly a 16GB swap partition would just be wasted hard drive space. But if you have 2GB of RAM then a 4GB swap partition is a good size. You could however get away with as little as 500MB.

4GB of harddrive swap when you have 2GB of RAM? I would choose a swap which is 1GB or less with that to not sacrifice performance.

I am not sure, however, if the newer Linux kernels have made improvement in memory management which might justify your recommendation as a good one. What do you think?

---

### Post by bulldog on 2008-11-09
I speak only for myself,but I have 4GB memory installed on a 64bit 8.10.
In the past I made a 2GB swap and I didn't bother to adjust it,so I use it still today.
But never seen it being used by ubuntu,not even when I had only 2GB memory installed.
So I think that,when you use 2GB or more,a swap could be 1GB or even less.

---

### Post by aikiwolfie on 2008-11-09
> **khelben1979 said:**
> 4GB of harddrive swap when you have 2GB of RAM? I would choose a swap which is 1GB or less with that to not sacrifice performance.

I am not sure, however, if the newer Linux kernels have made improvement in memory management which might justify your recommendation as a good one. What do you think?

Linux kernels are already pretty good at memory management. Like I said it's a rule of thumb and you can get away with as little as 500MB with 2GB of RAM.

You can do that because Linux unlike Windows doesn't use it's swap space until it's actual physical RAM is all but gone and used. So if all you're doing is browsing the web then 500MB with even just 1GB of RAM is easily enough because you'll be using actual RAM most of the time.

But if your like me and like to try and kill your CPU you will need more. Currently I run several BONIC projects on my PC. I have a Core 2 Quad and 2GB of RAM. So I can afford to let them run all the time. Even when I'm playing Nexiuz or watching a DVD. But the more I do the more my system uses the swap space.

It's all about the load you place on the PC. Sometimes you need to experiment a little.

---

### Post by 73ckn797 on 2008-11-09
> **IshikawaNakano said:**
> Thats how I do it.

If you can't get the live CD to boot you might also use [System Rescue CD]("http://www.sysresccd.org/Main_Page") to format your Hard Disk. It has Gparted and fdisk.


Thanks for this info. I was not aware of the tool. I like to have several options/tools at my disposal to accomplish various tasks. Being a mechanic for 33 year (not bragging), a variety of tools to accomplish a task is a necessity.

---

