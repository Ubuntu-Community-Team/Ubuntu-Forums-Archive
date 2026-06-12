---
title: "partitioning questions: force shrink vista, virtual disk partition?"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by ninjaPants on 2007-05-15
I just got a new hp laptop with vista preloaded and I'm getting ready to load Feisty onto it. I have a couple of issues before I get started though:

I don't want to destroy the Vista partition if I can help it. From reading other posts, I've determined there are two options.
1. Use Vista's shrink partition feature under disk management. 
    This would work... if Vista would let me shrink the partition as much as I want to. I think it's pagefiles/virtual memory/restore points in my way, but I can't find any place that explicitly tells me how to do that. 

2. Force gParted to size the partition, then run ntfsfix from Ubuntu. 
    I know how to do this... but I'm nervous about how well ntfs fix will repair the damage done by gparted. Anyone have soothing words or cautionary tales on this point?

Second issue is that I plan to have an XP virtual machine so I can use a couple programs without rebooting into Windows. I thought it might be a good idea to put it on a separate partition since I'm partitioning anyways. I know that the virtual disk files are pretty much contained and aren't likely to affect any systems or files outside of itself, but somehow it makes sense to put it on its own partition. Any opinions or advice on this? 

Here's my proposed partitioning scheme for reference and comment:

120gb hard drive

#1 60gb Vista
#2 4gb swap
#3 20gb root
#4 Extended
    4.1 20gb home
    4.2 15gb virtual machine

Thanks in advance,
Andrew

---

### Post by ninjaPants on 2007-05-19
No love... 
*bump*

---

### Post by 67GTA on 2008-03-15
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

