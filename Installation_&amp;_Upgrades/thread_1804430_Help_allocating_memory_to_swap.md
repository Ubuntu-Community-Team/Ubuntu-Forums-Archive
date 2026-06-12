---
title: "Help allocating memory to swap"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by stroiker on 2011-07-14
I did a standard install of Ubuntu 9.10, then upgraded to 10.04 LTS. 

Whenever I run htop I get:
CPU [~3.8%] Mem [100/244MB] Swp [87/713MB]

And free -m
Mem- total:244 used:214 free:29
Swap- total:713 used:86 free:626

It seems like I should be using allocating more memory to swap. Can anyone tell me if 
A. I should be using more swap, or if this looks normal
B. If so, how do I re allocate more memory to swap?

I am new to linux and still trying to figure out a lot of things. Any help is appreciated
running on Dell Dimension 8200

---

### Post by mikewhatever on 2011-07-14
You probably mean disk space and not memory. If so, I think 713MB of swap is enough. Do you know why you want more?

---

### Post by stroiker on 2011-07-14
Sorry I messed up my wording. What I was trying to say was is there a way to split the disk-space evenly between Mem and Swap, say like 478MB each instead 244mb and 713mb, respectively. It just seemed weird that more space was allocated to swap than memory. 

Would there be a reason to do this?
I just was wondering how disk-space gets allocated and why

thanks

---

### Post by mikewhatever on 2011-07-14
Several things to keep in mind: disk space is not allocated to memory, because memory (aka RAM) is not disk space. RAM and disk are two different separate entities, check out the links for more info:
[http://computer.howstuffworks.com/ram.htm](http://computer.howstuffworks.com/ram.htm)
[http://computer.howstuffworks.com/hard-disk.htm](http://computer.howstuffworks.com/hard-disk.htm)

---

### Post by Herman on 2011-07-15
Also see [What is swappiness and how do I change it?]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?") - Ubuntu Community Docs - Swap FAQ

---

