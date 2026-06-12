---
title: "Swap Disk not being used"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by juliansemerene on 2011-03-25
Hi everybody, I am new to Ubuntu and am using 10.10 maverick and after installing ubuntu on an 8gig sd card the swap partition (1.55 gigs) is not being used, i am not sure what to do, any help is greatly appreciated.

---

### Post by gnicko on 2011-03-25
Two things come to mind: One, how do you know it isn't being used? and Two, if it truly isn't being used, is it because it isn't "needed"--do you have enough memory that the system doesn't need to swap anything?

---

### Post by garvinrick4 on 2011-03-25
You can use System Monitor which will show you how much Ram and swap and what is being used.
```
Package: gnome-system-monitor            
State: installed
Automatically installed: no
Version: 2.28.2-0ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 1,167 k
Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libgcc1 (>= 1:4.1.1), libgconf2-4
         (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libglib2.0-0 (>= 2.16.0),
         libglibmm-2.4-1c2a (>= 2.25.4), libgtk2.0-0 (>= 2.20.0),
         libgtkmm-2.4-1c2a (>= 1:2.20.0), libgtop2-7 (>= 2.23.2),
         liblaunchpad-integration1 (>= 0.1.17), librsvg2-2 (>= 2.26.0),
         libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6 (>= 4.5), libwnck22 (>=
         1:2.22), libxml2 (>= 2.7.4), gconf2 (>= 2.28.1-2)
Recommends: libgksu2-0, gvfs
Description: Process viewer and system resource monitor for GNOME
 This package allows you to graphically view and manipulate the running
 processes on your system.  It also provides an overview of available resources
 such as CPU and memory.
```
Should be installed if not:
sudo apt-get install gnome-system-monitor

---

### Post by juliansemerene on 2011-03-26
> **gnicko said:**
> Two things come to mind: One, how do you know it isn't being used? and Two, if it truly isn't being used, is it because it isn't "needed"--do you have enough memory that the system doesn't need to swap anything?
I frequently run the free command as ubuntu is very slow thes are what it says
```
jules@Sem-Fos:~$ free
             total       used       free     shared    buffers     cached
Mem:       1013868     599236     414632          0      32488     357720
-/+ buffers/cache:     209028     804840
Swap:      1628156          0    1628156

``` 
though at the moment ram is fine there have been times where less than 10000 of ram were left at the time and swap still wasnt used which also answers if it is needed or not.

---

### Post by juliansemerene on 2011-03-26
other useful commands 
```
jules@Sem-Fos:~$ sudo fdisk -l
[sudo] password for jules: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd1a40721

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1045     8388608   12  Compaq diagnostics
/dev/sda2   *        1045       19458   147899392    7  HPFS/NTFS

Disk /dev/sdb: 7960 MB, 7960788992 bytes
245 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15190 * 512 = 7777280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b6c59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         810     6144000   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(765, 5, 8) logical=(809, 21, 36)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             810        1024     1629184    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(765, 5, 9) logical=(809, 21, 37)
Partition 2 has different physical/logical endings:
     phys=(967, 215, 16) logical=(1023, 145, 56)
Partition 2 does not end on cylinder boundary.
/dev/sdb5             810        1024     1628160   82  Linux swap / Solaris

```

```
jules@Sem-Fos:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jules/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jules)

```

```
jules@Sem-Fos:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=7d31f4ee-71af-425f-90a6-fa17966fa346 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=27c21e24-60f8-466d-a973-b11d423a477b none            swap    sw              0       0

```
that might help...

---

### Post by MrEgg on 2011-03-26
If it's slow you should try the 'top' command and see what's going on with cpu usage.

---

### Post by juliansemerene on 2011-03-26
> **MrEgg said:**
> If it's slow you should try the 'top' command and see what's going on with cpu usage.
```
jules@Sem-Fos:~$ top

top - 08:23:17 up 27 min,  2 users,  load average: 3.20, 2.46, 1.78
Tasks: 153 total,   2 running, 151 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.1%us,  4.0%sy,  0.0%ni, 23.6%id, 65.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1013868k total,   614552k used,   399316k free,    34004k buffers
Swap:  1628156k total,        0k used,  1628156k free,   363392k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 1176 root      20   0 37988  13m 7152 S   10  1.4   1:08.00 Xorg              
 1757 jules     20   0 91628  13m  10m S    6  1.4   0:08.62 gnome-terminal    
 1670 jules     20   0  371m  77m  28m S    4  7.8   2:44.72 firefox-bin       
 1469 jules     20   0 59764  24m 9396 S    3  2.5   0:15.74 compiz            
 1827 jules     20   0  2624 1128  840 R    1  0.1   0:00.33 top               
  316 root      20   0     0    0    0 D    0  0.0   0:00.14 jbd2/sdb1-8       
 1259 root      20   0  8464 3380 2756 D    0  0.3   0:00.90 upowerd           
 1437 jules     20   0 99396  11m 8888 S    0  1.2   0:02.33 gnome-settings-   
 1546 jules     20   0 28540 9932 7784 S    0  1.0   0:01.02 gtk-window-deco   
    1 root      20   0  2892 1680 1224 S    0  0.2   0:00.86 init              
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S    0  0.0   0:00.93 ksoftirqd/0       
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0       
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1       
    7 root      20   0     0    0    0 S    0  0.0   0:00.11 ksoftirqd/1       
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1        

``` those are the results

---

### Post by juliansemerene on 2011-03-26
> **juliansemerene said:**
> other useful commands 
```
jules@Sem-Fos:~$ sudo fdisk -l
[sudo] password for jules: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd1a40721

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1045     8388608   12  Compaq diagnostics
/dev/sda2   *        1045       19458   147899392    7  HPFS/NTFS

Disk /dev/sdb: 7960 MB, 7960788992 bytes
245 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15190 * 512 = 7777280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b6c59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         810     6144000   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(765, 5, 8) logical=(809, 21, 36)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             810        1024     1629184    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(765, 5, 9) logical=(809, 21, 37)
Partition 2 has different physical/logical endings:
     phys=(967, 215, 16) logical=(1023, 145, 56)
Partition 2 does not end on cylinder boundary.
/dev/sdb5             810        1024     1628160   82  Linux swap / Solaris

``````
jules@Sem-Fos:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jules/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jules)

``````
jules@Sem-Fos:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=7d31f4ee-71af-425f-90a6-fa17966fa346 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=27c21e24-60f8-466d-a973-b11d423a477b none            swap    sw              0       0

```that might help...
*NOTE ubuntu is installed to /dev/sdb1 the swap is /dev/sdb5

---

### Post by NightwishFan on 2011-03-26
This line shows that swap is available. It likely just is not needed at the moment.
```
Swap:      1628156          0    1628156
```

For example, on my machine:
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2982       2569        412          0        204       1511
-/+ buffers/cache:        854       2128
Swap:         2859          0       2859

```

If I open a huge image in GIMP:
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2982       2957         25          0          0        223
-/+ buffers/cache:       2733        249
Swap:         2859        799       2060
```

---

### Post by MrEgg on 2011-03-26
Just a thought.

You said you had / on an sd card. Aren't these slow read and write-wise to begin with? If you want to use an sd, shouldn't you deactivate journaling? Using ext2 could be a better choice than ext4 under those circumstances.

---

### Post by Dutch70 on 2011-03-26
Have you tried to open Gparted to see if Swap-on is enabled?

---

### Post by juliansemerene on 2011-03-26
> **MrEgg said:**
> Just a thought.

You said you had / on an sd card. Aren't these slow read and write-wise to begin with? If you want to use an sd, shouldn't you deactivate journaling? Using ext2 could be a better choice than ext4 under those circumstances.
interesting may i ask why journaling is bad for slow rw? not that i dont believe you its just interesting

---

### Post by juliansemerene on 2011-03-26
> **Dutch70 said:**
> Have you tried to open Gparted to see if Swap-on is enabled?
yes i have also tried the command

---

### Post by juliansemerene on 2011-03-26
> **NightwishFan said:**
> This line shows that swap is available. It likely just is not needed at the moment.
```
Swap:      1628156          0    1628156
```For example, on my machine:
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2982       2569        412          0        204       1511
-/+ buffers/cache:        854       2128
Swap:         2859          0       2859

```If I open a huge image in GIMP:
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2982       2957         25          0          0        223
-/+ buffers/cache:       2733        249
Swap:         2859        799       2060
```

If i open a huge file in gimp:

```
jules@Sem-Fos:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           990        898         91          0         98        495
-/+ buffers/cache:        304        685
Swap:         1589          0       1589

```

---

### Post by juliansemerene on 2011-03-26
even if i have very low ram free

```
jules@Sem-Fos:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           990        977         12          0         86        542
-/+ buffers/cache:        348        641
Swap:         1589          0       1589

```

---

### Post by NightwishFan on 2011-03-26
> **juliansemerene said:**
> even if i have very low ram free

```
jules@Sem-Fos:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           990        977         12          0         86        542
-/+ buffers/cache:        348        641
Swap:         1589          0       1589

```

You are only using 348mb of RAM there.

Check out this link: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by juliansemerene on 2011-03-26
> **NightwishFan said:**
> You are only using 348mb of RAM there.

Check out this link: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
but is says i only have 12 megabytes free..

---

### Post by MrEgg on 2011-03-26
> **juliansemerene said:**
> interesting may i ask why journaling is bad for slow rw? not that i dont believe you its just interesting

With journaling, you get more writes than without journaling.

Journaling : First you write to the journal, then to the drive, then erase from journal if writes to the drive were successful. Not to mention of course that you need to accommodate room for the journal on your already small drive. 

No journaling : You write to the drive, period. No space is reserved for the journal.

So for me, journaling on small and slow drives (such as usb sticks or sd cards) are slow and waste valuable space.

---

### Post by ~Plue on 2011-03-26
> **juliansemerene said:**
> but is says i only have 12 megabytes free..
what you should watch for is the '-/+ buffers/cache:' line
read  the linux ate my ram link and you'll understand

---

### Post by juliansemerene on 2011-03-26
> **~Plue said:**
> what you should watch for is the '-/+ buffers/cache:' line
read  the linux ate my ram link and you'll understand
oh gotcha thanks for that but then why is m comp so slow.. i think its because its journaled

---

### Post by NightwishFan on 2011-03-26
Trust me it seems like your ram is fine. :)

> free -m
             total       used       free     shared    buffers     cached
Mem:          2982       1109       1872          0         16        426
[COLOR="Lime"]-/+ buffers/cache:        [COLOR="DarkOrange"]666[/COLOR]       [COLOR="Blue"]2315[/COLOR][/COLOR]
Swap:         2859        344       2515

This line is the "sensible" amount of ram that is [COLOR="DarkOrange"]used[/COLOR] and [COLOR="Blue"]free[/COLOR].

---

### Post by juliansemerene on 2011-03-26
> **NightwishFan said:**
> Trust me it seems like your ram is fine. :)



This line is the "sensible" amount of ram that is [COLOR="DarkOrange"]used[/COLOR] and [COLOR="Blue"]free[/COLOR].
i understand that but do you have any ideas on why my comp is lagging?

---

### Post by juliansemerene on 2011-03-26
> **MrEgg said:**
> Just a thought.

You said you had / on an sd card. Aren't these slow read and write-wise to begin with? If you want to use an sd, shouldn't you deactivate journaling? Using ext2 could be a better choice than ext4 under those circumstances.
thanks that seems to be why my comp is lagging thanks soo much!

---

### Post by NightwishFan on 2011-03-26
To be honest I doubt that is why. Can you describe lagging? Slow opening applications would be the only symptom of slow disk access. That is perfectly normal.

---

### Post by juliansemerene on 2011-03-26
well ubuntu randomly freezes apps like firefox keeps on stopping and apps stop working and so on

---

### Post by NightwishFan on 2011-03-26
In that case you might indeed be waiting on disk access. Do applications start quickly though? If so then you might have good speed.

---

### Post by juliansemerene on 2011-03-26
yes apps start quickly but freeze suddenly whenever

---

### Post by MrEgg on 2011-03-26
> **NightwishFan said:**
> Slow opening applications would be the only symptom of slow disk access.

Are you absolutely positive? I think slow disk access would considerably slow down the computer during the use of the GIMP or Inkscape, and not just during their opening. JMHO, of course, but based on personal experience.

---

### Post by NightwishFan on 2011-03-26
Low memory or slow access is usually the cause of "lack of responsiveness" from my experience, however if Firefox always takes around 10-20 seconds to open, it is basically confirmed to be the disk. That is all I meant.

---

