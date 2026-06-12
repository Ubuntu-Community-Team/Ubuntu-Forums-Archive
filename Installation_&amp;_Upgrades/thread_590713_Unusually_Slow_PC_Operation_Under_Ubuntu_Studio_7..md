---
title: "Unusually Slow PC Operation Under Ubuntu Studio 7.10"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by ozboomer on 2007-10-25
Hi..

I've installed Ubuntu Studio 7.10 using the 'alternate' CD ISO on one of my PCs that has the following configuration:

2.4 GHz Intel Celeron
3x IDE-HDD (80 GB, 40 GB, 20 GB)
256 MB RAM
CD-RW/DVD

This PC also has installations of Zenwalk Linux, Puppy Linux and Windows XP and I use LILO as the boot loader.

The installation onto one of the hard disk partitions went through Ok, taking maybe an hour all-up, and installing all of the options, that is, sound, video, etc.

The only problem is that the PC is horribly slow running Ubuntu Studio.  For example, when using Zenwalk Linux, after entering my username/password into the window manager dialog, the XFCE desktop is displayed within 10 seconds or so.  However, under Ubuntu Studio, it takes maybe 90 seconds for the desktop to be displayed after entering my username/password.

More examples: Starting Hydrogen takes about 50 seconds, starting RoseGarden takes nearly 2 minutes.

In short, the system is practically unusable.

I have vague memories of some fancy 'eye candy' being enabled in this realease of Ubuntu... and I was wondering if that might be loading-up the PC.

I would appreciate some pointers to where I might find some clues on what's going wrong here.

Thanks.

---

### Post by PointyWombat on 2007-10-25
Well, the first step is trying to identify if something is using system resources.  What do the following commands produce:

# sar -u 2 5

# top

# iostat -d 2 5

# vmstat 2 5

---

### Post by ozboomer on 2007-10-25
Hi, again...

Before I respond with my findings to the suggestions, a couple of other relevant points:

* When I first login on the window manager, there is some message about having trouble contacting the Gnome Settings Daemon, so I don't know what impact that will have.

* When I select to restart the computer, the only message that is displayed is "Restarting the system..." or something similar.  Unlike most other Linux variants I've used, there are no shutdown messages nor any shutdown (splash) screen.  Is this normal?  In all(?) other respects, it seems like it goes through an orderly system shutdown.

* Does it make sense for the system to fsck (the Unix partitions) and dosfsk (the WinXP partitions) at every system startup?  This is what happens at the moment and is contributing to the 5+ minute startup time of the system.  I would have thought that fsck is only called if the mount count has been exceeded or there was a problem on shutdown?

* This computer has NO internet connectivity.

* I have done a completely 'vanilla' installation and have added no further modules, applications, etc.  The ISO I wrote to a DVD was called ubuntustudio-7.10-alternate-i386.iso.


Now, to the results of the suggested tests:

$ sar -u 2 5
The program 'sar' can be found in the following packages:
 * sysstat
 * atsar
Try: sudo apt-get install <selected package>
bash: sar: command not found


$ top

[FONT="Courier New"]top - 16:49:04 up 7 min,  2 users,  load average: 1.17, 0.58, 0.22
Tasks:  97 total,   1 running,  96 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.8%us,  6.7%sy,  0.1%ni, 24.3%id, 12.4%wa, 41.7%hi,  0.0%si,  0.0%st
Mem:    221956k total,   215940k used,     6016k free,     7324k buffers
Swap:  2096472k total,    34980k used,  2061492k free,    96404k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5093 root      20   0  402m  13m 6188 S  3.7  6.0   0:07.82 Xorg               
 5454 john      20   0  2364 1052  800 R  1.9  0.5   0:00.03 top                
    1 root      20   0  2952 1852  532 S  0.0  0.8   0:01.59 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 posix_cpu_timer    
    5 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-high/0     
    6 root     -51  -5     0    0    0 S  0.0  0.0   0:01.97 softirq-timer/0    
    7 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-net-tx/    
    8 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-net-rx/    
    9 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-block/0    
   10 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-tasklet    
   11 root     -51  -5     0    0    0 S  0.0  0.0   0:00.01 softirq-sched/0    
   12 root     -51  -5     0    0    0 S  0.0  0.0   0:00.03 softirq-hrtimer    
   13 root     -51  -5     0    0    0 S  0.0  0.0   0:00.21 softirq-rcu/0      
   14 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
   15 root      10 -10     0    0    0 S  0.0  0.0   0:00.02 desched/0          
[/FONT]

$ iostat -d 2 5
The program 'iostat' is currently not installed.  You can install it by typing:
sudo apt-get install sysstat
bash: iostat: command not found


$ vmstat 2 5
[FONT="Courier New"]procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 3  1  34980   3168  37776  71992    0   53   852   103 1934 4588 13 39 32 17
 0  1  34980   3204  38704  71024    0    0   478    60  975 2178  3 21  0 77
 0  1  34980   3648  39544  69572    0    0   428   306 1387 2872  2 25  0 74
 0  1  34980   3372  40116  68568    0    0   290     0  528 1323  1 12  0 87
 1  1  34980   3676  40732  67692    0    0   308     0  559 1448  2 12  0 86
$
[/FONT]
Obviously, some modules/applications/libraries/etc are missing.  What do I need to download and install so that I can get these tests to work as required? ...or is there enough info here already?

Thanks.

---

### Post by PointyWombat on 2007-10-25
> **ozboomer said:**
> Hi, again...

Before I respond with my findings to the suggestions, a couple of other relevant points:

* When I first login on the window manager, there is some message about having trouble contacting the Gnome Settings Daemon, so I don't know what impact that will have.

* When I select to restart the computer, the only message that is displayed is "Restarting the system..." or something similar.  Unlike most other Linux variants I've used, there are no shutdown messages nor any shutdown (splash) screen.  Is this normal?  In all(?) other respects, it seems like it goes through an orderly system shutdown.

* Does it make sense for the system to fsck (the Unix partitions) and dosfsk (the WinXP partitions) at every system startup?  This is what happens at the moment and is contributing to the 5+ minute startup time of the system.  I would have thought that fsck is only called if the mount count has been exceeded or there was a problem on shutdown?

* This computer has NO internet connectivity.

* I have done a completely 'vanilla' installation and have added no further modules, applications, etc.  The ISO I wrote to a DVD was called ubuntustudio-7.10-alternate-i386.iso.


Now, to the results of the suggested tests:

...

Obviously, some modules/applications/libraries/etc are missing.  What do I need to download and install so that I can get these tests to work as required? ...or is there enough info here already?

Thanks.

You could install the missing programs by installing sysstat, but it seem that more is going on here than initially thought. I would think that nothing will be revealed by my suggested commands and the problem really lies with either a faulty installation, bad disk, or otherwise.  How many times have you installed it? Is this a first attempt?

And no. It should not fsck your disks on every boot (every 30 mounts, or on demand), so I'd be curious to see that if you booted into console mode, ie: no desktop, and run "sudo init 6", do you see a normal reboot occur? It may be doing an fsck everytime becuase of a dirty file system caused by an abrupt shutdown.

---

### Post by ozboomer on 2007-10-26
> **PointyWombat said:**
> ...the problem really lies with either a faulty installation, bad disk, or otherwise.  How many times have you installed it? Is this a first attempt?

Yes, 1st attempt.

...but I've now gone through the installation a couple of more times...  and there's been no joy.  The first reinstallation, I tried installing to Ext2 file system, but the installation script didn't like that, failing on 'selecting software to install' or something.

Re-installing onto 'normal' Ext3 FS seems to be Ok... but the computer still runs very slowly, although the themes problem appeared only on the first boot and subsequent boots showed a black taskbar/panel top and bottom and there were no error messages.

I tried running JackCtl and it had continual xruns (135ms) just sitting, 'idling'.  When I started RoseGarden, with everything idling, there were continual xruns (250ms)... When I tried to load a file into RoseGarden, and play just MIDI, it all sounded 'choppy', so I re-set Jack to have the highest (whatever it's called) value - so the latency was as large as it could be.. ..and it still sounded choppy (after restaring everything of course).

Then, upon loading one of the 'audio content' Rosegarden demo files, the application gave up with a message about 'ran out of computing power' and couldn't manage the audio file.

So, in short, it still seems unworkable.  Oh... the fsck things run on every boot as well, even though the shutdowns go through normally..

Any further thoughts?

---

### Post by PointyWombat on 2007-10-29
Something just doesn't seem right. I suppose it is possible that you're simply short on memory with only 256MB. When you run rosegarden or your other painfull apps, can you see if you're swapping? Use top and see what you have for memory free when running these.  I'm also still suspicious about the fsck issue as well. That's just not right either. Is there a possibility that there was some mucking around in the BIOS in the past and the drives are not configured optimally? Can you reset BIOS to default (if you think there's no risk in doing so). Can you temporarily remove the drives you're not needing/mounting?

---

