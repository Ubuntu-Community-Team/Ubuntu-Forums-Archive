---
title: "'No buffer space' - Ubuntu VERY slow... help!"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by fony on 2008-08-07
Im new to Linux and I've recently installed Ubuntu 8.04.1 on a second hard drive .. The install went smoothly as far as I could tell until I restarted to boot for the first time into Ubuntu which took at least 10 minutes to reach the log in screen.

So I found that it will boot after a long time and I've had the following error come up:

*Loading hardware drivers...
     error receiving uevent message:
     No buffer space available
     (303.087893) intel-rng: FWH not detected

Despite that, I can log in and use everything within Ubuntu no problems... except that everything is a million times slower than it should be. CPU is consistently around 80% just running one tab in firefox and system monitor and it seems that the process using the majority of the CPU is called 'gnome-system-monitor'.

my system specs:

P4 3.06GHz
1 Gig of RAM
MSI mainboard (845GE Max)
Onboard graphics

ANY help or suggestions greatly appreciated. Thanks in advance, fony.

EDIT: I forgot to mention... I checked the md5 on the ISO once I downloaded it and burned at 2.5 speed so I don't think the problem is being caused by a bad burn.

---

### Post by ilrudie on 2008-08-07
Please post the output from the following commands run from the terminal:
free -m
top
df -kh

*top will update over and over again so just use <ctrl>+<c> to stop it and copy the output over.

---

### Post by fony on 2008-08-07
```
 free -m
             total       used       free     shared    buffers     cached
Mem:          1010        938         71          0        245        327
-/+ buffers/cache:        364        645
Swap:         2376          0       2376

```

```

 top

top - 21:30:14 up  2:09,  2 users,  load average: 0.64, 0.29, 0.20
Tasks: 104 total,   1 running, 103 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.5%us,  0.0%sy,  0.0%ni, 88.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1034348k total,   961176k used,    73172k free,   251820k buffers
Swap:  2433808k total,      220k used,  2433588k free,   335752k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9301 tom       20   0  2308 1108  852 R  4.4  0.1   0:00.42 top                
 9263 tom       20   0 74280  20m  10m S  3.2  2.0   0:08.82 gnome-terminal     
 6773 root      20   0  245m  28m 9356 S  1.9  2.8   4:30.19 Xorg               
 7366 tom       20   0  171m  79m  23m S  1.9  7.9   6:13.83 firefox            
 7141 tom       20   0 15376 4736 3764 S  0.6  0.5   0:27.62 gnome-screensav    
 7117 tom       20   0 28476 5956 3408 S  0.3  0.6   0:20.44 pulseaudio         
    1 root      20   0  2844 1692  544 S  0.0  0.2   0:03.56 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            

```

 
```
 df -kh
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              54G  2.3G   49G   5% /
varrun                506M  100K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  344K  505M   1% /dev
devshm                506M  180K  505M   1% /dev/shm
lrm                   506M   38M  468M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       54G  2.3G   49G   5% /home/tom/.gvfs

```

thanks for the fast reply man.

---

### Post by ilrudie on 2008-08-07
Your memory usage looks unusually high but your processor looks ok.  Is this a default install.  Have you added any other applications?  Try sorting the system monitor output by memory and see what is using up all your memory.

---

