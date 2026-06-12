---
title: "Performance hits rock bottom during disk activity."
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MaX on 2008-09-19
If I (for example) run synaptic and update a few packages (say 30).
During that time the performance of the computer goes rock bottom.

If I compare this to Windows (XP or Vista) the system is still usable if I have lots of disk activity.

I guess this is an ext3 problem? and the same problem that makes/made firefox unusable too.

So how do I fix it? Am I the only one?

---

### Post by prshah on 2008-09-19
> **MaX said:**
> 
During that time the performance of the computer goes rock bottom.


a) What HDD do you have? If it is IDE, you need to check if DMA is enabled```
sudo hdparm -i /dev/sda| grep -i dma
``` if dma is enabled, there will be a "*" next to the mode being used. Quote from man:> Using DMA nearly always gives the best per&#8208;
              formance, with fast I/O throughput and low CPU usage.

b) what memory? If memory is low, then disk-trashing will be taking place due to swapping.```
free -m
```

c) What processor? If processor is low, installing packages takes time, and the fact that HDD is active at that time is only co-incidence.

d) Check HDD performance (when system is idle)```
sudo hdparm -tT /dev/sda
``` For reference:> ```
laptop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   780 MB in  2.00 seconds = 389.48 MB/sec
 Timing buffered disk reads:   72 MB in  3.05 seconds =  23.58 MB/sec

```

e) Could you have bad sectors? Non destructive / read only (but long) test (To be done from live CD, after unmounting relevant HDD)```
sudo badblocks /dev/sda
```

f) Is swap available / active?```
swapon -s
```

All above commands to be given in the terminal (Applications-Accessories-Terminal). Replace "/dev/sda" with the actual partition name.

---

### Post by Nullack on 2008-09-19
Youll need to be monitoring top = especially the %wa.

---

### Post by DavidONE on 2008-09-19
Same problem here.  Firefox locked up multiple times and screen darkened while Songbird was scanning / building library.

```
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 

```

```

 /dev/sdb:
 Timing cached reads:   8178 MB in  2.00 seconds = 4093.33 MB/sec
 Timing buffered disk reads:  250 MB in  3.01 seconds =  83.14 MB/sec

```

```
Filename				Type		Size	Used	Priority
/dev/sdb1                               partition	979924	2144	-1

```

Nothing else was running and I doubt it's lack of memory / performance (see sig).  Running the same scan on XP does not cause a lockup.

Any suggestions?

---

### Post by Nullack on 2008-09-19
I havent seen any data that shows the problem. Wheres the traces? Wheres the details from "top"?

---

### Post by MaX on 2008-09-19
I have SATA(1) disks, about 9Gb's Free in linux, 1Gb Swap 2GB of RAM, AMD64 X2 3200+

ext3 formated disks.

---

### Post by TerminX on 2008-09-19
Same problem here.  I blame X:

2900 root      20   0 1643m 1.1g 9608 S  3.0 73.6 125:32.94 X 

Pretty sad for 2 days uptime.  Looks like it's hemorrhaging memory.

---

### Post by prshah on 2008-09-19
> **DavidONE said:**
> Same problem here.  Firefox locked up multiple times and screen darkened while Songbird was scanning / building library.


> **TerminX said:**
> Same problem here.  I blame X:
2900 root      20   0 1643m 1.1g 9608 S  3.0 73.6 125:32.94 X 


Can both of you run the following command from the terminal (Applications-Accessories-Terminal) and post the output here?```
dmesg | grep -i drdy
cat /var/log/messages | grep -i drdy

```

---

### Post by Embedded Linux Guy on 2008-09-19
Hi, I am getting very high CPU wait % and load since upgrading to 8.10 today.  wa% is often 40-90% with load 2-4, just running Firefox.  I believe that saving files to disk is a factor.  In addition my laptop LCD is updating very badly -- I keep seeing vertical black lines flickering in different parts of the screen (I have an nVidia NV34M with "nvidia" driver).  Finally I notice that my swap is under-utilized.  Under 8.04 it would tend to fill up, but now only 3MB are used even though RAM is completely full.

```

# swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda2                               partition       2931852 3228    -1

#top
top - 16:25:32 up  1:17,  1 user,  load average: 1.64, 1.95, 2.21
Tasks: 162 total,   1 running, 161 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.9%us, 10.4%sy, 25.8%ni,  3.1%id, 46.3%wa,  0.5%hi,  1.0%si,  0.0%st
Mem:   1033272k total,   998292k used,    34980k free,    12460k buffers
Swap:  2931852k total,     2916k used,  2928936k free,   344708k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6742 root      20   0  175m 116m 7940 S  9.4 11.6   3:21.97 Xorg
24728 jesse     20   0  2412 1084  792 R  3.8  0.1   0:00.02 top
    1 root      20   0  3052 1876  552 S  0.0  0.2   0:01.34 init

```

---

### Post by Nullack on 2008-09-19
Good post embedded, finally some real data

---

### Post by prshah on 2008-09-20
> **Embedded Linux Guy said:**
> 
Finally I notice that my swap is under-utilized.  Under 8.04 it would tend to fill up, but now only 3MB are used even though RAM is completely full.


Have you changed the "swapiness" settings? ```
Sat Sep 20 01:04:27 ~:$ cat /proc/sys/vm/swappiness 
40

```

---

### Post by DavidONE on 2008-09-20
> **prshah said:**
> Can both of you run the following command...

That produced no output for me.

Re. swappiness - mine is set at 10.  I checked memory usage when the machine was hanging - it was less than 1GB of the 2GB installed.

---

### Post by Miguel on 2008-09-20
Known bug since... Gutsy! It's [bug 131094](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094). IMHO, this is the most windows-like bug (and one of the worst) we've had since I switched to linux in 2004. Unresponsive system under high load? I though I left that on my ntfs partition. It's funny however that system responsiveness under high CPU load is still as brilliant as ever.

---

### Post by forger on 2008-09-20
No-one mentioned which packages, some packages include a lot of files, hence disk activity..

I think you have change the niceness of the apt?
sudo nice -n 15 apt-get update
sudo nice -n 15 apt-get upgrade

---

### Post by Miguel on 2008-09-20
More than nice, people should probably experiment with **ionice**, the equivalent of nice but for I/O scheduling.

---

### Post by meborc on 2008-09-20
just to give my experiences with this problem...

when copying a large file (600 M) from one partition to another (ext2 -> ext3) and hitting the firefox icon, it does not open until the file copying has finished...

this has never happened to me in ubuntu before... not in hardy and not even in breezy for that matter

---

