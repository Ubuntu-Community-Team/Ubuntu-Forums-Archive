---
title: "New Install of v7.10 - System pretty slow with 1 gig RAM"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by mskadu on 2007-10-28
Hi,

I recently managed to get a new v7.10 install running after a few initial problems ([previous thread]("http://ubuntuforums.org/showthread.php?t=594694")). But the overall system seems very slow. This is despite the fact that I have 1 gig RAM. My copy of Windows XP (dual booting with this new install) is running several faster!

How can I cure this? Whats a good place to start. The system log doesnt show anything out of the ordinary.

---

### Post by taurus on 2007-10-28
Do you have compiz or beryl running?  I assume you are running Gnome window manager?

Post the outputs of these commands from a terminal?

```
free
top
```

---

### Post by mskadu on 2007-10-28
Yes, I am. Here's the requested output:

free
>              
total       used       free     shared    buffers     cached
Mem:       1035120    1018876      16244          0      45840     711148
-/+ buffers/cache:     261888     773232
Swap:      1309256          0    1309256


top
> 
top - 18:02:07 up  1:16,  3 users,  load average: 4.08, 3.84, 2.77
Tasks: 114 total,   4 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s): 79.4%us, 16.3%sy,  3.3%ni,  0.0%id,  0.0%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:   1035120k total,  1020612k used,    14508k free,    44820k buffers
Swap:  1309256k total,       72k used,  1309184k free,   706620k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
13800 root      25   0  6900 4164  456 R 32.8  0.4   0:01.00 dpkg-deb          
 4939 root      15   0  168m  18m 8428 S 15.1  1.9   6:11.79 Xorg              
 5579 mskadu    15   0  166m  53m  22m S 13.1  5.3   3:04.72 firefox-bin       
 5155 mskadu    15   0 18516  10m 7908 S  9.2  1.1   1:13.43 metacity          
13212 root      18   0 25780  22m 1120 S  8.9  2.2   0:51.90 dpkg              
 6028 mskadu    15   0  116m  25m  14m S  7.2  2.5   0:49.37 gnome-terminal    
 5196 mskadu    15   0 16780 2720 1756 S  3.0  0.3   0:28.09 gnome-screensav   
13465 mskadu    39  19 32852  29m 2636 R  3.0  2.9   0:15.88 apt-check         
13785 mskadu    15   0  2364 1156  876 R  1.3  0.1   0:00.57 top               
13798 root      21   0  3252  736  624 S  1.0  0.1   0:00.03 dpkg-deb          
13799 root      18   0  3380  540  396 S  1.0  0.1   0:00.03 dpkg-deb          
 5190 mskadu    15   0 56912  17m  12m S  0.7  1.7   0:27.02 nm-applet         
 2394 root      10  -5     0    0    0 S  0.3  0.0   0:05.81 kjournald         
 4686 haldaemo  15   0  3268 1228 1076 S  0.3  0.1   0:03.30 hald-addon-stor   
 5197 mskadu    15   0 38736  11m 8520 S  0.3  1.2   0:03.49 gnome-power-man   
11120 root      15   0 18244  14m  11m S  0.3  1.4   0:13.07 apt-get           
    1 root      15   0  2948 1852  532 S  0.0  0.2   0:01.04 init    


---

### Post by taurus on 2007-10-28
Are you either upgrading or installing something when the system is slow?  I see that you have apt-get running.  Does it always slow?

What's the spec of your machine besides 1GB of RAM?

---

### Post by mskadu on 2007-10-28
Yes, I was installing a couple of packages at the moment. My system specs are:

Intel P4 Mobile 3.06 GHz
and 1 gig RAM.
Video ATI Radeon 9200 (not sure about video ram)

The update manager was able to download the package information very fast, but took a full four minutes to show the list. I have switched off the desktop special effects  from the effects tab of the appearance dialog box.

---

