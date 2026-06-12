---
title: "Ubuntu 10.10 Slow"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by iCeD00D on 2010-12-26
Good evening. I just loaded the latest release on my box and noticed after configuring my vid card, that Ubuntu is slow running. When I click something as simple as Ubuntu Software Manager it takes almost 30s-1m for the application to come up. If this was one of my old boxes I could understand this but this is a fairly new box. Any help to 'tweek' the box would be great. Below are my system specs. Thanks much ... 
 
MB - SiS 661FX w/latest bios
CPU - P4 3.2Ghz w/1G L2 cache
Memory - 2GB unbuffered
Hard Drive - SATA Seagate 1.5TB 7200RPM drive
CDROM/DVD - Lighton SATA
Videocard - ATI HD 3600 (yes I've installed the drivers according to the Maverick Wiki)

---

### Post by sikander3786 on 2010-12-27
Welcome to the forums :-)

From Applications > Accessories > Terminal, check the CPU and memory usage.

```
top
```

Post the output here so we can have a look as well.

In addition, post the output of these commands.

```
lspci | grep VGA
```

```
glxinfo | grep vendor
```

This is desktop or netbook editiion? And, is compiz enabled?

---

### Post by necrocyber on 2010-12-27
I have almost the same problem, in my notebook Ubuntu 10.10 presents slow. I already try make tests in other computers but the slow happened the same form.
Other problem I've had is with my keyboard when i type the computers costs recognize what is typed.


If someone know what's happening i would appreciate.  



Obs: I already install the video drivers.

---

### Post by iCeD00D on 2010-12-28
> **sikander3786 said:**
> Welcome to the forums :-)

From Applications > Accessories > Terminal, check the CPU and memory usage.

```
top
```Post the output here so we can have a look as well.

In addition, post the output of these commands.

```
lspci | grep VGA
``````
glxinfo | grep vendor
```This is desktop or netbook editiion? And, is compiz enabled?

=====================
Thanks for the reply.. below is the info you requested

```

root@iCe-UbunTU:~# top
top - 16:58:09 up 1 day, 17:18,  3 users,  load average: 3.11, 2.78, 2.61
Tasks: 163 total,   3 running, 158 sleeping,   0 stopped,   2 zombie
Cpu(s): 22.6%us,  5.1%sy,  0.0%ni, 67.5%id,  4.6%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2060872k total,  1908096k used,   152776k free,   235352k buffers
Swap:  3069948k total,        8k used,  3069940k free,   917392k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
11535 root      20   0  260m  94m  49m R   23  4.7 473:54.18 Xorg               
13327 ice       20   0 86896  19m  11m S   17  1.0 364:22.18 gnome-system-mo    
11682 ice       20   0  276m  74m  21m S    4  3.7  94:53.30 cairo-dock         
13382 ice       20   0  445m  79m  29m R    3  3.9 160:29.20 firefox-bin        
 8422 ice       20   0 91980  13m  10m S    3  0.7   0:00.84 gnome-terminal     
11686 ice       20   0 39728  21m 7184 S    3  1.1  53:04.57 compiz             
13416 ice       20   0  164m  38m  16m S    1  1.9  35:54.78 plugin-containe    
29155 ice       20   0  208m  53m  22m S    1  2.7  16:05.61 skype              
26651 ice       20   0  224m 105m  20m S    1  5.3  26:10.35 software-center    
 8533 root      20   0  2620 1124  832 R    0  0.1   0:00.06 top                
11667 ice       20   0 99392  11m 8516 S    0  0.6   0:30.32 gnome-settings-    
11689 ice       20   0  219m  76m  20m S    0  3.8   5:00.15 nautilus           
14248 ice       20   0  118m  38m  23m S    0  1.9  17:30.90 qbittorrent        
    1 root      20   0  2888 1640 1172 S    0  0.1   0:00.85 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:18.52 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:01.04 migration/0        

```

```
root@iCe-UbunTU:~# lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series

```

```
root@iCe-UbunTU:~# glxinfo | grep vendor
server glx vendor string: ATI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.

```

Compiz - Enabled 

Ubuntu 10.10 - Desktop Edition 

Thanks much ...

---

### Post by Clive McCarthy on 2010-12-28
I had a _very_ similar problem. I gave up and did a fresh install of 10.10 and things are OK. It seems that many other folks, upgrading to 10.10, have similar problems with the system becoming almost unresponsive.

One thing I did notice was that a very large amount of memory was being used even when nothing but the terminal was running. A similar thing is happening in icedood's *top* listing:
[INDENT][COLOR="Red"]Mem:   2060872k total,  1908096k used [/COLOR][/INDENT]
this shows 92% memory used but only ~30% is showing up in running applications!

Looks like the kernel has somehow hogged memory (a kernel core leak?)
After a _fresh_ install of 10.10 things are behaving normally with much less memory in use.

Installing 10.10 fresh from a CD is a drag. After it is installed there is still 200MB of update to download! Not to mention the need to install sharing... :rolleyes:

---

### Post by iCeD00D on 2010-12-28
Funny thing Clive is that this is my 2nd CD install :( .... the first one was on an old 500GB SATA drive and this current one above is on a 1.5TB SATA drive.... I noticed that the memory was also being used up and still can not figure out why..... So for now im going to load Xfce to see if that solves the problem... With my puter stats Ubuntu should be zooooooming .. not acting like Windows 3.1 ... :( :(

---

### Post by Clive McCarthy on 2010-12-28
I somehow doubt that it is a problem with Gnome. 

The machine I have that became unusable is a very feeble Celeron 430 1.8Ghz with 2GB ram and a 400GB Maxtor SATA drive and plain Intel G45 graphics. I have installed 10.10 on several other machines without trouble. It has been irritating because the machine is just used to port/recompile my code for several Ubuntu client machines. It is just a trash box I made out of bits that were lying around. It is still _very_ slow when simply copying files to my client machines using Samba mount in a shell script.

I have had trouble with the Ubuntu upgrade process in the past. What we are experiencing is not unique.

---

