---
title: "HELP !!!  Zombie attack ... (kworker)"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by jfl on 2011-07-16
Been running Ubuntu since Dapper on 4 office machines.
Did all the upgrades with few problems over the years.
Upgraded a week ago from 10.4 to 11.04 with no problems (I thought !)  - Wrong !

This Lenovo R61 Laptop has one of the 2 cores going to 100% regularly every
3-4 seconds; makes the keyboard extremely laggy and the mouse jumpy. 2.6.38.xx
A process named **kworker/x:x** (multiple instances) is hogging the CPUs.
If I try to kill it, it comes right back with his brothers ;-)  There can be up to 5 or 10 instances running. 

Dual boot with win XP. Running Kernel 2.6.38.10 generic

I spent half of last night with my friend "Google" and found many threads in many forums reporting this problem; seems to be a bug in Kernel 2.6.38.xx.
The most common recommended cure was to upgrade to Kernel 2.6.39.xx.
However, trying to do that, found like a few others that now, the PPA is "empty".
I ran "powertop" to no effect.

This laptop is so laggy that it is practically useless.  Most of the applications that do not require typing work fine.

I have long time with Ubuntu as a user, I am not afraid of the command line, but my knowledge of the system is limited.

I would hate to go back to Maverick, but if there is no other way ...

Help will be greatly appreciated !

---

### Post by conradin on 2011-07-16
will kworker take the -nh option (no hang) if run via a terminal?
I think the kill command youre using is not strong enough
try ```
kill -9 <PID>
```
on zombie processes.

---

### Post by jfl on 2011-07-16
> **conradin said:**
> will kworker take the -nh option (no hang) if run via a terminal?
I think the kill command youre using is not strong enough
try ```
kill -9 <PID>
```
on zombie processes.

Just tried  ```
sudo kill -9 2666
``` 
Yeah, one of the kworker PID is 2666 :o
The process disappears and another one  arrives !

I have 10 of them running right now; they alternatively grab 40-80 % of the CPU for a few seconds then release the CPU for 2-3 seconds then another one grabs it, and so on !

---

### Post by Canezila on 2011-07-16
Same here.  I notice it starting when the computer is left to idle.  Now I have to reboot my computer because it has practically stopped.

---

### Post by jfl on 2011-07-16
Found something !

Ran "Powertop" again (as root).

The first option it gives after it runs for a few seconds about "power save" (just can't remember exactly) **worked**.
It didn't kill the kworker but at least they are harmless now.
My CPU idle load is 5-15%.

I got my keyboard back :P:P:P

I will probably have to do it at the next reboot and I'll write down what I do.
Will post it here.

---

### Post by 1clue on 2011-07-16
Are these things actually showing up as zombie processes?  If so it could be a symptom of a bigger problem.

A zombie is a process that has stopped executing but which init (pid 1) has not cleaned up yet.  Usually that means that the parent process didn't wait for the child to die, which is bad programming.

It also could mean that init is busy somewhere with a long-running task (should never happen) and just hasn't gotten around to cleaning up yet.  I had that happen before, when I was trying to set something up to run at boot.  All init tasks should be short tasks to either spawn a new task (which could be lengthy but is not run at such a high priority) or clean up an old one, both of which should be fractions of a second.

You should almost never see a zombie process in any list.

Here's a pretty good description:
[http://www.brighthub.com/computing/linux/articles/79186.aspx](http://www.brighthub.com/computing/linux/articles/79186.aspx)

---

### Post by jfl on 2011-07-16
> **1clue said:**
> Are these things actually showing up as zombie processes?  If so it could be a symptom of a bigger problem.

A zombie is a process that has stopped executing but which init (pid 1) has not cleaned up yet.  Usually that means that the parent process didn't wait for the child to die, which is bad programming.

It also could mean that init is busy somewhere with a long-running task (should never happen) and just hasn't gotten around to cleaning up yet.  I had that happen before, when I was trying to set something up to run at boot.  All init tasks should be short tasks to either spawn a new task (which could be lengthy but is not run at such a high priority) or clean up an old one, both of which should be fractions of a second.

You should almost never see a zombie process in any list.

Here's a pretty good description:
[http://www.brighthub.com/computing/linux/articles/79186.aspx](http://www.brighthub.com/computing/linux/articles/79186.aspx)

NO, NO !!!

They are not "zombie processes" in the strict sense.
I referred to the "kworker" as zombies as a "joke" because they are hard to kill and keep coming back. :D
Sorry for the confusion !

---

### Post by 1clue on 2011-07-16
No biggie, I kind of figured that's what you meant.

On the other hand, if you had a real "zombie" attack you might need a completely different solution.

Just trying to make sure you had all your angles covered.

Good luck and have fun.

---

### Post by jfl on 2011-07-16
> **Good luck** and have fun. Thanks, I'll need it !!!

However, I still have 8-10 "kworker" in the process list; they don't use any resources but they are there.  My other Lenovo which run pretty much the same configuration doesn't have them.

It bugs me, as there are numbers of threads and launchpad items, not to mention an email exchange from Linus T. himself, on this subject for the last 3 months, and I didn't find a resolution anywhere.

Oh, well !

---

### Post by snmcdonald on 2011-07-16
You can also use

```
pgrep process name (or partial)
```

and 

```
pkill process name (or partial, but be careful with partial)
```

---

### Post by 1clue on 2011-07-16
I just checked my system.  I have 20 of them.  Sleeping, zero cpu, zero memory, really zero problem until they start getting obnoxious in some way.

---

### Post by conradin on 2011-07-18
Im interested to know if these are actual zombie processes. 
some kill commands such as SIGHUP will respawn the process
when it hangs, SIGKILL sends the process to /dev/null essentialy deleting it. Can we get before and after snapshots of the command 
```
ps -elf 
```

Also, what is your hardware? 
Its looking to me like a bug. Theres a command Im trying to think of which tells you the parent process to whatever process you're looking at. I dont think kworker is respwning itself, rather someother process is telling it send out more processes. That could be either a driver issue, or an early sign to hardware failure. 

Id like to see a stream of output from vmstat 20 or more, to see if you have a high number of context switches, while this zombie apocalypse is going down.
```
vmstat 1 20
```

Kernel developers are looking into it...
[https://lkml.org/lkml/2011/3/30/836](https://lkml.org/lkml/2011/3/30/836)

---

### Post by conradin on 2011-07-18
Im also currious, what happens if you turn off ACPI?
to see how...
[http://ubuntuforums.org/showthread.php?t=1654540](http://ubuntuforums.org/showthread.php?t=1654540)

---

### Post by jfl on 2011-07-21
OK, I can reproduce the problem easily: if I reboot the cpu's have normal load; if I plug my cell phone in the USB port, the kworker's grab 100% of cpu every 2-4 seconds for 2-3 seconds (looks like a bad EKG).
The first time it happens after a reboot, it can be fixed by running "powertop" and hitting "P" when prompted.
However, on successive occurrence of the problem, "powertop" doesn't do anything.
If I suspend the machine and wake it up, it behaves ... until I use the USB port.
Very aggravating because it creates a huge lag in the keyboard, and the mouse is jerky.

Here is the output of vmstat:


```
jf@lenovo:~$ vmstat 1 20
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 4  0      0 957692 229804 1183964    0    0    34    27  538  573 14 17 69  1
 0  0      0 957772 229804 1184044    0    0     0    36  707  632 11  1 88  0
 1  0      0 957520 229804 1184056    0    0     0     0  605  680 11  9 81  0
 2  0      0 957600 229804 1184056    0    0     0     0  675  782 13 52 36  0
 0  0      0 957192 229804 1184056    0    0     0     0  661  731 12 45 42  0
 0  0      0 957312 229804 1184056    0    0     0     0  633  585 10  2 89  0
 1  0      0 957376 229812 1184056    0    0     0    80  548  609 10  7 82  0
 1  0      0 957448 229812 1184056    0    0     0     0  670  776 12 52 36  0
 0  0      0 957412 229812 1184056    0    0     0     0  641  753 12 45 43  0
 1  0      0 957508 229812 1184056    0    0     0     0  697  581 10  2 88  0
 1  0      0 957132 229812 1184056    0    0     0     0  771  593 10  6 84  0
 1  0      0 957244 229812 1184056    0    0     0     0  687  771 12 53 35  0
 0  0      0 957268 229820 1184048    0    0     0    24  686  710 12 45 42  0
 1  0      0 957380 229820 1184032    0    0     0     0  747  580 12  1 88  0
 2  0      0 957492 229820 1184056    0    0     0     0  696  566 11  8 81  0
 1  0      0 956108 229820 1185336    0    0     0     0  698  955 17 53 30  0
 0  0      0 956236 229820 1185336    0    0     0     0  676  778 13 45 42  0
 1  0      0 957200 229820 1184056    0    0     0     0  849  714 10  2 87  0
 1  0      0 954276 229832 1185540    0    0   156    24  626  768 13  7 76  5
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  0      0 953908 229832 1185484    0    0     0     0  674  794 12 52 36  0
jf@lenovo:~$ 

```

and here is the output of "ps -elf

```
jf@lenovo:~$ ps -elf
F S UID        PID  PPID  C PRI  NI ADDR SZ WCHAN  STIME TTY          TIME CMD
4 S root         1     0  0  80   0 -   763 poll_s 17:35 ?        00:00:00 /sbin
1 S root         2     0  0  80   0 -     0 kthrea 17:35 ?        00:00:00 [kth]
1 S root         3     2  0  80   0 -     0 run_ks 17:35 ?        00:00:02 [kso]
1 S root         6     2  0 -40   - -     0 cpu_st 17:35 ?        00:00:00 [mig]
1 S root        11     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [cpu]
1 S root        12     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [khe]
1 S root        13     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [net]
1 S root        15     2  0  80   0 -     0 bdi_sy 17:35 ?        00:00:00 [syn]
1 S root        16     2  0  80   0 -     0 bdi_fo 17:35 ?        00:00:00 [bdi]
1 S root        17     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [kin]
1 S root        18     2  0  60 -20 -     0 rescue 17:35 ?        00:00:01 [kbl]
1 S root        19     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [kac]
1 S root        20     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [kac]
1 S root        21     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [kac]
1 S root        22     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [ata]
5 S root        23     2  0  80   0 -     0 hub_th 17:35 ?        00:00:00 [khu]
1 S root        24     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [md]
1 S root        26     2  0  80   0 -     0 watchd 17:35 ?        00:00:00 [khu]
1 S root        27     2  0  80   0 -     0 kswapd 17:35 ?        00:00:00 [ksw]
1 S root        28     2  0  85   5 -     0 ksm_sc 17:35 ?        00:00:00 [ksm]
1 S root        29     2  0  80   0 -     0 fsnoti 17:35 ?        00:00:00 [fsn]
1 S root        30     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [aio]
1 S root        31     2  0  80   0 -     0 ecrypt 17:35 ?        00:00:00 [ecr]
1 S root        32     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [cry]
1 S root        36     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [kth]
1 S root        44     2  0  80   0 -     0 scsi_e 17:35 ?        00:00:02 [scs]
1 S root        45     2  0  80   0 -     0 scsi_e 17:35 ?        00:00:00 [scs]
1 S root        53     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [kmp]
1 S root        54     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [kmp]
1 S root        55     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [kon]
1 S root        56     2  0  60 -20 -     0 rescue 17:35 ?        00:00:00 [kco]
1 S root       218     2  0  80   0 -     0 scsi_e 17:35 ?        00:00:00 [scs]
1 S root       219     2  0  80   0 -     0 scsi_e 17:35 ?        00:00:00 [scs]
1 S root       220     2  0  80   0 -     0 scsi_e 17:35 ?        00:00:00 [scs]
1 S root       254     2  0  80   0 -     0 kjourn 17:35 ?        00:00:00 [kjo]
1 S root       305     1  0  80   0 -   603 poll_s 17:36 ?        00:00:00 upsta
5 S root       382     1  0  76  -4 -   750 poll_s 17:36 ?        00:00:00 udevd
1 S root       630     1  0  80   0 -   603 poll_s 17:36 ?        00:00:00 upsta
1 S root       721     2  0  60 -20 -     0 rescue 17:36 ?        00:00:00 [cfg]
1 S root       732     2  0  60 -20 -     0 rescue 17:36 ?        00:00:00 [kps]
1 S root       736     2  0  60 -20 -     0 rescue 17:36 ?        00:00:00 [iwl]
1 S root       749     2  0  80   0 -     0 pccard 17:36 ?        00:00:00 [pcc]
1 S root       777     2  0  60 -20 -     0 rescue 17:36 ?        00:00:00 [ktp]
1 S root       780     2  0  60 -20 -     0 rescue 17:36 ?        00:00:00 [hd-]
1 S root       845     2  0  80   0 -     0 kjourn 17:36 ?        00:00:00 [kjo]
1 S root       850     2  0  80   0 -     0 kjourn 17:36 ?        00:00:02 [kjo]
1 S root       853     2  0  80   0 -     0 bdi_wr 17:36 ?        00:00:00 [flu]
4 S root       867     1  0  80   0 -  4150 poll_s 17:36 ?        00:00:00 smbd
5 S syslog     874     1  0  80   0 -  7124 poll_s 17:36 ?        00:00:00 rsysl
5 S 102        895     1  0  80   0 -   958 poll_s 17:36 ?        00:00:03 dbus-
4 S root       905     1  0  80   0 -  4506 poll_s 17:36 ?        00:00:00 gdm-b
5 S avahi      909     1  0  80   0 -   786 poll_s 17:36 ?        00:00:00 avahi
5 S root       910     1  0  80   0 -  6392 poll_s 17:36 ?        00:00:02 Netwo
1 S avahi      911   909  0  80   0 -   754 unix_s 17:36 ?        00:00:00 avahi
4 S root       913     1  0  80   0 -  1165 poll_s 17:36 ?        00:00:00 /usr/
4 S root       915     1  0  80   0 -  6857 poll_s 17:36 ?        00:00:00 /usr/
4 S root       982     1  0  80   0 -  6355 poll_s 17:36 ?        00:00:00 /usr/
1 S root       989   867  0  80   0 -  4150 poll_s 17:36 ?        00:00:00 smbd
4 S root      1005     1  0  80   0 -  1795 poll_s 17:36 ?        00:00:01 /usr/
0 S root      1063     1  0  80   0 -   468 n_tty_ 17:36 tty4     00:00:00 /sbin
0 S root      1066     1  0  80   0 -   468 n_tty_ 17:36 tty5     00:00:00 /sbin
0 S root      1073     1  0  80   0 -   468 n_tty_ 17:36 tty2     00:00:00 /sbin
0 S root      1074     1  0  80   0 -   468 n_tty_ 17:36 tty3     00:00:00 /sbin
0 S root      1076     1  0  80   0 -   468 n_tty_ 17:36 tty6     00:00:00 /sbin
1 S root      1090     1  0  80   0 -   532 poll_s 17:36 ?        00:00:00 acpid
1 S root      1095     1  0  80   0 -   567 hrtime 17:36 ?        00:00:00 cron
1 S daemon    1096     1  0  80   0 -   533 hrtime 17:36 ?        00:00:00 atd
1 S root      1111     1  0  80   0 -  2040 wait_f 17:36 ?        00:00:00 pytho
4 S root      1137     1  0  80   0 -  1293 poll_s 17:36 ?        00:00:00 /sbin
1 S root      1168     1  0  80   0 -  3343 poll_s 17:36 ?        00:00:00 /usr/
1 S root      1171  1168  0  80   0 -  3368 poll_s 17:36 ?        00:00:00 /usr/
1 S root      1254     2  0  60 -20 -     0 rescue 17:36 ?        00:00:00 [l2c]
5 S root      1351     2  0  70 -10 -     0 rfcomm 17:36 ?        00:00:00 [krf]
0 S root      1419     1  0  80   0 -   468 n_tty_ 17:36 tty1     00:00:00 /sbin
4 S rtkit     1439     1  2  81   1 -  4978 poll_s 17:36 ?        00:09:04 /usr/
4 S root      1458     1  0  80   0 -  5915 poll_s 17:36 ?        00:00:00 /usr/
1 S root      1459  1458  0  80   0 -  1424 poll_s 17:36 ?        00:00:01 udisk
4 S root      1504     1  0  80   0 -  4174 poll_s 17:36 ?        00:00:00 /usr/
1 S root      1808  1168  0  80   0 -  3384 poll_s 17:36 ?        00:00:00 /usr/
5 S root      1877     1  0  80   0 -  2357 poll_s 17:36 ?        00:00:00 nmbd
4 S root      2619     1  0  80   0 -  3682 poll_s 17:52 ?        00:00:00 /usr/
4 S root      5865     1  0  80   0 -  9882 poll_s 19:22 ?        00:00:03 /usr/
4 S root      6485   905  0  80   0 -  4963 poll_s 21:51 ?        00:00:00 /usr/
4 S root      6489  6485  7  80   0 - 13844 poll_s 21:51 tty8     00:05:13 /usr/
4 S root      6536  6485  0  80   0 -  6253 poll_s 21:51 ?        00:00:00 /usr/
1 S jf        6558     1  0  80   0 - 15147 poll_s 21:51 ?        00:00:01 /usr/
4 S jf        6577  6536  0  80   0 -  9061 poll_s 21:51 ?        00:00:00 gnome
1 S jf        6614  6577  0  80   0 -   842 poll_s 21:51 ?        00:00:00 /usr/
1 S jf        6617     1  0  80   0 -   864 poll_s 21:51 ?        00:00:00 /usr/
1 S jf        6618     1  0  80   0 -  1331 poll_s 21:51 ?        00:00:04 //bin
0 S jf        6623     1  0  80   0 -  2512 poll_s 21:51 ?        00:00:01 /usr/
1 S jf        6634     1  0  80   0 - 27581 poll_s 21:51 ?        00:00:01 /usr/
0 S jf        6638     1  0  80   0 -  1908 poll_s 21:51 ?        00:00:00 /usr/
1 S jf        6643     1  0  80   0 -  8000 futex_ 21:51 ?        00:00:00 /usr/
0 S jf        6647  6577  0  80   0 - 21884 poll_s 21:51 ?        00:00:03 metac
0 S jf        6658     1  0  80   0 -  8419 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6660  6577  0  80   0 - 30457 poll_s 21:51 ?        00:00:03 gnome
0 S jf        6662     1  0  80   0 -  4551 poll_s 21:51 ?        00:00:01 /usr/
0 S jf        6665     1  0  80   0 -  2128 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6667  6577  0  80   0 - 48873 poll_s 21:51 ?        00:00:06 nauti
0 S jf        6668  6577  0  80   0 - 12471 poll_s 21:51 ?        00:00:00 zeitg
0 S jf        6670     1  0  80   0 - 10845 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6671  6577  0  80   0 - 13726 poll_s 21:51 ?        00:00:02 /usr/
0 S jf        6678  6577  0  80   0 - 33100 poll_s 21:51 ?        00:00:02 nm-ap
0 S jf        6682  6577  0  80   0 -  6525 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6688     1  0  80   0 -  8662 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6691  6577  0  80   0 - 24609 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6694  6577  0  80   0 - 24892 poll_s 21:51 ?        00:00:00 gnome
0 S jf        6699  6688  0  80   0 -   978 unix_s 21:51 ?        00:00:00 /bin/
0 Z jf        6702  6688  0  80   0 -     0 exit   21:51 ?        00:00:00 0
0 S jf        6710     1  0  80   0 - 21986 poll_s 21:51 ?        00:00:04 /usr/
0 S jf        6712     1  0  80   0 - 20197 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6719     1  0  80   0 - 19937 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6722     1  0  80   0 - 23034 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6724     1  0  80   0 -  7828 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6727     1  0  80   0 - 29274 poll_s 21:51 ?        00:00:02 /usr/
0 S jf        6728     1  0  80   0 - 36779 poll_s 21:51 ?        00:00:05 /usr/
0 S jf        6734     1  0  80   0 -  2028 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6739     1  0  80   0 - 19375 poll_s 21:51 ?        00:00:02 /usr/
0 S jf        6740     1  0  80   0 - 47482 poll_s 21:51 ?        00:00:06 /home
0 S jf        6784     1  0  80   0 -  4923 poll_s 21:51 ?        00:00:01 /usr/
0 S jf        6804     1  0  80   0 -  1966 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6810     1  0  80   0 - 15018 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6812     1  0  80   0 - 12951 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6840     1  0  80   0 -  1941 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6847     1  0  80   0 - 30358 poll_s 21:51 ?        00:00:02 /usr/
0 S jf        6850     1  0  80   0 - 12173 poll_s 21:51 ?        00:00:01 /usr/
0 S jf        6853     1  0  80   0 - 14572 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6887     1  0  80   0 -  1934 poll_s 21:51 ?        00:00:00 /usr/
1 S jf        6912     1  0  80   0 -  6777 poll_s 21:51 ?        00:00:00 gnome
0 S jf        6914     1  0  80   0 -  1963 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        6925  6577  0  80   0 -  4852 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        7003     1 16  80   0 - 26610 poll_s 21:51 ?        00:10:52 gnome
0 S jf        7005     1  0  80   0 - 16340 poll_s 21:51 ?        00:00:01 /usr/
0 S jf        7010  6577  0  80   0 -  8358 poll_s 21:51 ?        00:00:00 /usr/
0 S jf        7096  6577  0  80   0 - 21099 poll_s 21:52 ?        00:00:01 updat
0 S jf        7153     1  0  80   0 -  1251 wait   21:54 ?        00:00:00 /bin/
0 S jf        7156  7153  0  80   0 - 33908 wait   21:54 ?        00:00:23 pytho
0 S jf        7159  7156  0  80   0 - 21882 pipe_w 21:54 ?        00:00:01 gksu
4 S root      7165  7159  0  80   0 -  3304 poll_s 21:54 ?        00:00:00 /usr/
4 S root      7167  7165  0  80   0 -  2626 pipe_w 21:54 ?        00:00:00 /usr/
0 S jf        7545     1  0  80   0 - 20918 poll_s 21:57 ?        00:00:00 /usr/
0 Z jf        7589  7545  0  80   0 -     0 exit   21:57 ?        00:00:00 0
5 S root      7666     1  0  80   0 -   864 poll_s 22:02 ?        00:00:00 dbus-
5 S root      7667     1  0  80   0 -   695 poll_s 22:02 ?        00:00:00 //bin
1 S jf        8583  7156  0  80   0 - 33908 wait   22:10 ?        00:00:00 pytho
0 S jf        8588  8583  0  80   0 -   478 wait   22:10 ?        00:00:00 /bin/
0 S jf        8589  8588  4  80   0 - 138472 poll_s 22:10 ?       00:02:04 /usr/
0 S jf        8620  8589  0  80   0 - 26546 poll_s 22:11 ?        00:00:02 /usr/
0 S jf        8767     1  0  80   0 - 24489 poll_s 22:23 ?        00:00:01 gnome
0 S jf        8771  8767  0  80   0 -   517 unix_s 22:23 ?        00:00:00 gnome
0 S jf        8772  8767  0  80   0 -  1353 n_tty_ 22:23 pts/0    00:00:00 bash
1 S root      9073     2  0 -40   - -     0 cpu_st 22:25 ?        00:00:00 [mig]
1 S root      9075     2  0  80   0 -     0 run_ks 22:25 ?        00:00:00 [kso]
1 R root      9076     2 20  80   0 -     0 ?      22:25 ?        00:06:19 [kwo]
5 S root      9116   382  0  78  -2 -   749 poll_s 22:25 ?        00:00:00 udevd
5 S root      9117   382  0  78  -2 -   749 poll_s 22:25 ?        00:00:00 udevd
4 S root      9274   910  0  80   0 -   638 poll_s 22:25 ?        00:00:00 /sbin
0 S jf        9356     1  2  80   0 - 103905 poll_s 22:25 ?       00:00:51 /opt/
1 S jf        9362  9356  0  80   0 - 17707 poll_s 22:25 ?        00:00:00 /opt/
4 S jf        9364     1  0  80   0 - 23108 wait_f 22:25 ?        00:00:00 /opt/
1 S jf        9387  9364  0  85   5 - 40690 futex_ 22:25 ?        00:00:04 /opt/
1 S jf        9393  9364  0  80   0 - 41490 futex_ 22:25 ?        00:00:02 /opt/
1 S jf        9400  9364  0  80   0 - 34659 futex_ 22:25 ?        00:00:00 /opt/
1 S jf        9404  9364  0  80   0 - 35131 futex_ 22:25 ?        00:00:00 /opt/
0 S jf        9423  9356  0  80   0 - 34121 poll_s 22:25 ?        00:00:17 /opt/
0 S jf        9443     1  0  80   0 - 15652 poll_s 22:26 ?        00:00:04 /usr/
0 S jf        9449     1  0  80   0 -  5372 poll_s 22:26 ?        00:00:00 /usr/
1 S root      9497     2  0  80   0 -     0 worker 22:30 ?        00:00:02 [kwo]
1 S jf        9635  9364  1  80   0 - 38631 futex_ 22:39 ?        00:00:15 /opt/
1 S root      9659     2  0  80   0 -     0 worker 22:41 ?        00:00:00 [kwo]
0 S jf        9675  8767  0  80   0 -  1353 wait   22:42 pts/1    00:00:00 bash
1 S root      9711     2  0  80   0 -     0 worker 22:45 ?        00:00:03 [kwo]
1 S root      9752     2  0  80   0 -     0 worker 22:50 ?        00:00:00 [kwo]
1 S root      9753     2  0  80   0 -     0 worker 22:51 ?        00:00:01 [kwo]
1 S root      9759     2  0  80   0 -     0 worker 22:55 ?        00:00:00 [kwo]
1 S root      9760     2  0  80   0 -     0 worker 22:56 ?        00:00:00 [kwo]
0 R jf        9761  9675  0  80   0 -  1177 -      22:56 pts/1    00:00:00 ps -e
jf@lenovo:~$ 
```

Going to look more in ACPI

Thanks for your help !!!

---

### Post by jfl on 2011-07-22
Found something that might be interesting:
- if I boot with Kernel 2.6.38-8, I have no problems.
- if I boot with 2.6.38-10, the zombies attack the CPU.

So I am staying with Kernel 2.6.38-8, until there is a newer one ...

I hope this might help another "kworker victim".

---

