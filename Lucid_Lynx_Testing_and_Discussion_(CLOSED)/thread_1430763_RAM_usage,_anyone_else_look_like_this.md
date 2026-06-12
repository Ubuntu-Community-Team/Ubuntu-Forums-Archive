---
title: "RAM usage, anyone else look like this"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Digital Hick on 2010-03-15
I have installed Ubuntu 10.04 32-bit on my laptop.  I have noticed that the RAM usage is 'off the charts' compared to 9.10 and how 10.04 acted in VirtualBox.

Granted, this is still technically an alpha-stage build, but does anyone else have usage like the attached screen shot?  Yes, I know, I am not in any danger of running out of RAM, but that is not the point.

It has regularly been over 400MB and their is nothing in the process list to add up to this figure.  Is it doing a RAM-cache for recent applications or what?  It is a bit Vista-like.  I have never seen a pre-release eat memory like this. :o

---

### Post by kelvin spratt on 2010-03-15
Looks fairly OK to me for ubuntu. I,d be more concerned by wasting so much space to swap I have never seen any swap usage on my machine I allocate 250mb and use ram instead.

---

### Post by howefield on 2010-03-15
> **Digital Hick said:**
> I have noticed that the RAM usage is 'off the charts' compared to 9.10 and how 10.04 acted in VirtualBox.

What is it at fresh boot ?

At boot mine sits around 370 megs on 64 bit Alpha 3 and would expect a good bit less on 32 bit. (That's pretty much a default install, with compiz)

> It is a bit Vista-like.

Not even close. imhe :o

---

### Post by NightwishFan on 2010-03-15
My Ubuntu regularly uses over 600mb. It leads me to swap all the time on my desktop and lose reponsiveness. Is this temporary? I am beginning to lose faith in the 400mb system requirements for it.

---

### Post by Digital Hick on 2010-03-15
> **howefield said:**
> What is it at fresh boot ?

At boot mine sits around 370 megs on 64 bit Alpha 3 and would expect a good bit less on 32 bit. (That's pretty much a default install, with compiz)


Wow, what a difference.  Down to 170MB, 200MB if I start Firefox and System Monitor to recreate previous situation app wise.  So that means one of two things.  It is caching stuff in RAM for faster response time.  This would be consistent with experiences I have had on Ubuntu.  It could also be some memory leaks they have not stomped yet.:D

---

### Post by MacUntu on 2010-03-15
Those 521 MiB shown in the pic are memory in use, not including cache.

I'm at 270 MiB right now (nothing running but Opera and a terminal), six hours uptime, x86 with 2 GB RAM, nvidia-current and no visual effects. Pretty much the same as with the last releases.

---

### Post by Owen.C93 on 2010-03-15
After a few hours of uptime but with everything close mine uses 164mb. Firefox will eat some more but unless i' photo editing it has never even been to a GB (which was windows 7 idle stare)

---

### Post by andrewabc on 2010-03-15
> **NightwishFan said:**
> My Ubuntu regularly uses over 600mb. It leads me to swap all the time on my desktop and lose reponsiveness. Is this temporary? I am beginning to lose faith in the 400mb system requirements for it.

What's your computer specs? I assume less than 1gb? 400mb is minimum for a reason.

There is an option to reduce swap usage (assuming you have ram for programs).

[Linux - Tips, tweaks and alignment for SSD](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)
Go to swap area.
> The solution is setting kernel swappiness
to zero, by adding a line vm.swappiness = 0 to /etc/sysctl.conf.
A temporary change for trying out the effect is possible by calling
echo 0 > /proc/sys/vm/swappiness (as root) from the command line.
I think goes from 0-10. I think I have mine set to 1 and rarely get swap, but then I have 3gb ram.
Do some googling on that file to figure out for sure.

---

### Post by dxxvi on 2010-03-15
500 is too much if you have nothing running.

Attached is mine with 1 terminal and swiftfox.

---

### Post by ankspo71 on 2010-03-15
I always thought the more ram you have, the more ram the OS is going to try to use. That's the way it seems to be with my systems anyway.

```
james@James:~$ free
             total       used       free     shared    buffers     cached
Mem:       2060300     690912    1369388          0      71240     321760
-/+ buffers/cache:     297912    1762388
Swap:      4096532          0    4096532

```There is mine after doing some general web browsing in firefox, and running tests on cairo-dock with strace.

Edit: After a reboot:
```
james@James:~$ free
             total       used       free     shared    buffers     cached
Mem:       2060300     435452    1624848          0      50564     155988
-/+ buffers/cache:     228900    1831400
Swap:      4096532          0    4096532
```
The only thing running now is cairo-dock.
hope this helps

---

### Post by tad1073 on 2010-03-15
At one point yesterday, my ram usage was up to 1.3gb's, now it is at 898gb's

---

### Post by grandtoubab on 2010-03-16
You can tweak your swapiness parameter
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

---

### Post by xir_ on 2010-03-16
well i totally broke something in my system my ram starts off at over 1gb.

---

### Post by Half-Left on 2010-03-16
Don't rely on top or the system monitor giving you accurate memory readings. :D

[http://www.kdedevelopers.org/node/4166](http://www.kdedevelopers.org/node/4166)

---

### Post by howefield on 2010-03-16
> **xir_ said:**
> well i totally broke something in my system my ram starts off at over 1gb.

Do you have two disks in your machine ?

Following a reboot after updating with update manager, my ram usage is 1.4 gig. Commenting out the line for the second disk in fstab and rebooting takes the ram to 370megs. Until update manager is used again and I need to uncomment the line in fstab.

I haven't looked for a solution, but your post has prompted me to do so.

---

### Post by NightwishFan on 2010-03-16
I installed Debian Sid (with Gnome), and found it to be using only 130mb of RAM. That is 5 times less than Ubuntu. There is no way a few services add up to 650mb of RAM.

---

### Post by ibuclaw on 2010-03-16
Not sure what everyone's fuss over RAM is.

For me, it is rather typical to have 200-20MB **free**.

```

[~] free -m
             total       used       free     shared    buffers     cached
Mem:          2017       1907        109          0        281        812
-/+ buffers/cache:        813       1203
Swap:         3623          3       3620
[~] uptime
 11:56:03 up 3 days, 13:27,  1 user,  load average: 0.43, 0.30, 0.27
[~] top -n1

top - 11:56:13 up 3 days, 13:27,  1 user,  load average: 0.52, 0.33, 0.28
Tasks: 148 total,   3 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.7%us,  3.2%sy,  0.0%ni, 84.8%id,  2.2%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   2065592k total,  1952444k used,   113148k free,   288488k buffers
Swap:  3710972k total,     3300k used,  3707672k free,   831600k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
25730 jstdio    20   0  225m  41m  18m S   13  2.1 149:05.71 chrome             
  932 jstdio    20   0  269m  87m  26m S    4  4.3  24:13.44 firefox-bin        
 1357 root      40   0 46168  12m 5944 R    4  0.6 102:14.43 Xorg               
 3185 jstdio    40   0  2460 1072  780 R    4  0.1   0:00.05 top                
 2107 jstdio    40   0  3284 1164  916 S    2  0.1  21:38.43 xcompmgr           
 2116 jstdio    40   0 11696 4828 3688 S    2  0.2   3:15.30 tint2              
 2998 jstdio    40   0 52888  17m  12m S    2  0.9   0:11.09 xchat              
    1 root      40   0  2036  616  572 S    0  0.0   0:02.91 init               
    2 root      40   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.19 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:01.29 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      20   0     0    0    0 S    0  0.0   0:02.85 events/0           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr   

```
Regards
Iain

---

### Post by Digital Hick on 2010-03-16
> **dxxvi said:**
> 500 is too much if you have nothing running.

Attached is mine with 1 terminal and swiftfox.

This morning, after just some forum browsing with FF, 257MB.  I don't know, chalk it up to random chance.  I had ran around the Internet with FF for a while, maybe there was a bunch of stuff in memory even though System Monitor did not show it???  If Half-Left if correct, and I looked at the link, maybe relying on system monitor is not the best anyway.

Just never seen it that high with only one application open before unless it was Virtualbox.:popcorn:

---

### Post by xir_ on 2010-03-16
> **howefield said:**
> Do you have two disks in your machine ?

Following a reboot after updating with update manager, my ram usage is 1.4 gig. Commenting out the line for the second disk in fstab and rebooting takes the ram to 370megs. Until update manager is used again and I need to uncomment the line in fstab.

I haven't looked for a solution, but your post has prompted me to do so.

Thanks for the reply. My system is a bit odd, i have only one hard disk but unless i set the system to raid in the bios i cannot access the CD drive. I'm note sure if that is related.

Although my system has one disk it has three partitions. So i don't think my problem is as such.

---

### Post by howefield on 2010-03-16
> **Digital Hick said:**
> This morning, after just some forum browsing with FF, 257MB.  I don't know, chalk it up to random chance.

IME, Firefox can easily chalk up shed loads of memory, especially if you are using flash. I'm only interested in the memory usage at boot, after that, the system can use as much as it likes.

Nice to know that the hardware I've paid for is being used. :)

---

### Post by andrewabc on 2010-03-20
I booted beta1 liveusb, have firefox open with 5 tabs, and gnome-monitor reports 276mb of ram in use.

> Tasks: 177 total,   1 running, 176 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.7%sy,  0.0%ni, 98.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3071240k total,   984220k used,  2087020k free,   115096k buffers
Swap:   506008k total,        0k used,   506008k free,   582588k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4017 root      20   0 74196  26m  11m S    1  0.9   0:39.58 Xorg               
 4097 ubuntu    20   0 90016  25m 7900 S    1  0.8   0:06.04 compiz             
 4328 ubuntu    20   0  302m  75m  27m S    0  2.5   0:34.28 firefox-bin        
    1 root      20   0  2700 1680 1204 S    0  0.1   0:00.40 init               


Making a lot of use of buffers.

---

### Post by NightwishFan on 2010-03-20
My RAM went usage is much more smooth on lucid after a few updates.

---

### Post by solitaire on 2010-03-20
Slightly off topic but....

What do you do about memory leaks?

I'm running TweetDeck and either that or Adobe AIR leaks memory like sieve! 
Killing TweetDeck does not get back all the memory it's used. (Swap file is easy to clen out, swapoff then swapon. but RAM is harder to clear out without a reboot!!)

I've only got 1Gb RAM (+ 1Gb Swap) on this Laptop.

---

### Post by NightwishFan on 2010-03-21
Kill the process. Cache and Buffer RAM is replaced automatically.

---

### Post by solitaire on 2010-03-21
> **NightwishFan said:**
> Kill the process. Cache and Buffer RAM is replaced automatically.

I do that but not all of the RAM / Swap used by it is released That's why I have to turn the swap off and on again. I'm looking for a way to clear /clean the RAM as well..

---

### Post by NightwishFan on 2010-03-21
If the process is no longer active, then all the ram is released. Some of it might be in the buffer/cache like I said above. That is automatically replaced when necessary. Swap as well, unless you really need it to clear, just leave it used. It is no detriment unless it is *actively* swapping at the moment. Having the process in swap is better than not, since swap is memory mapped. (Except on laptops, which may not want to use the disk in any case)

---

