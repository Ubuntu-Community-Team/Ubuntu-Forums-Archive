---
title: "xfdesktop forks like crazy ! xubuntu 9.04 alpha"
date: 2009-03-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lol24h on 2009-03-06
Since few upgrades before, If i'm correct about xfdesktop 4.5.99.1, on startup xfdesktop process multiplies itself like crazy ! 
Newest updates doesn't helped at all, already xfce environment is 4.6.0 and still behaves the same way, on start, I have to kill all xfdesktop processes before it take all my RAM and get Out Of Memory, system freezes like dead one.
After that I run manually by 'xfdesktop &' and everything works fine. I'm sick of this. I know it's software under development, but it should work somelike, but it doesn't at all.

I've deleted all configs, reinstalled xfce completely, still nothing.
It looks like that, I'm killing these processes with my not so very sophisticated.
```

10308 ?        00:00:00 xfdesktop <defunct>
10309 ?        00:00:00 xfdesktop <defunct>
10312 ?        00:00:00 xfdesktop <defunct>
10314 ?        00:00:00 xfdesktop <defunct>
10316 ?        00:00:00 xfdesktop <defunct>
10318 ?        00:00:00 xfdesktop <defunct>
10320 ?        00:00:00 xfdesktop <defunct>
10321 ?        00:00:00 xfdesktop <defunct>
10322 ?        00:00:00 xfdesktop <defunct>
10325 ?        00:00:00 xfdesktop <defunct>
10327 ?        00:00:00 xfdesktop <defunct>
10329 ?        00:00:00 xfdesktop <defunct>
10331 ?        00:00:00 xfdesktop <defunct>
10332 ?        00:00:00 xfdesktop <defunct>
10335 ?        00:00:00 xfdesktop <defunct>
10337 ?        00:00:00 xfdesktop <defunct>
10338 ?        00:00:00 xfdesktop <defunct>
10341 ?        00:00:00 xfdesktop <defunct>
10343 ?        00:00:00 xfdesktop <defunct>
10344 ?        00:00:00 xfdesktop <defunct>
10345 ?        00:00:00 xfdesktop <defunct>
10348 ?        00:00:00 xfdesktop <defunct>
10349 ?        00:00:00 xfdesktop <defunct>
10352 ?        00:00:00 xfdesktop <defunct>
10354 ?        00:00:00 xfdesktop <defunct>
10356 ?        00:00:00 xfdesktop <defunct>
10357 ?        00:00:00 xfdesktop <defunct>
10361 ?        00:00:00 xfdesktop <defunct>

etc.

```
the not sophisticated script ;-)
```

#!/bin/bash

while [ 1 ]; do
    killall -9 xfdesktop
done

```
 
I thought about installing fresh new system, but it appeared the xubuntu installer's partman since Alpha 4 doesn't recognize partition on my harddrive, like there were none. Damn it !
I suppose it could be the problem below, but it never been before :
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          17      136048+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          17        1873    14908320    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            1874        3747    15044873   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4            3748       12161    67585424    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            3748        3998     2008093+  82  Linux swap / Solaris
/dev/sda6            3998        5243    10008463+  83  Linux
/dev/sda7            5244        5973     5863693+  83  Linux
/dev/sda8            5974       12161    49705078+  83  Linux

```

waiting impatiently for your reply...


EDIT:
graphics driver  : nvidia-glx-180 ( 180.35-0ubuntu1 )
xorg-server      : 7.4~5ubuntu13

---

### Post by overdrank on 2009-03-06
Moved to  Jaunty Jackalope Testing and Discussion

---

### Post by Tux Aubrey on 2009-03-06
I'm not getting any unusual processes using Xubuntu in a VBox machine with 512Mb of RAM

```
aubrey@jaunty-xubuntu:~$ top

top - 12:10:40 up 5 min,  2 users,  load average: 0.59, 0.49, 0.24
Tasks: 103 total,   2 running, 101 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.3%us, 18.3%sy,  0.0%ni, 74.1%id,  3.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    509512k total,   375808k used,   133704k free,    12992k buffers
Swap:   409616k total,        0k used,   409616k free,   144652k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2704 root      20   0 66792  19m 7100 S 12.0  3.8   0:28.86 Xorg               
 3236 aubrey    20   0 34836  20m 8304 R  5.0  4.1   0:02.48 xfce4-terminal     
 3258 aubrey    20   0  150m  69m  21m S  4.7 14.0   0:20.22 firefox            
 3201 aubrey    20   0  7260 1720 1296 S  1.3  0.3   0:02.00 VBoxClient         
 3257 aubrey    20   0  2448 1172  912 R  0.3  0.2   0:00.67 top                
    1 root      20   0  3084 1888  564 S  0.0  0.4   0:01.50 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.03 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.28 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.07 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 khelper            
   10 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
  144 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
  146 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0          
  148 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
  149 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  181 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue           
```

---

### Post by lol24h on 2009-03-07
I've got 2GB, and I've forgotten to add, it's 32bit edition of Xubuntu.

---

### Post by mr_pouit on 2009-03-07
Did you try the workaround explained [here](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616)?

---

### Post by lol24h on 2009-03-09
> 
WORKAROUND:
You may have to reset some custom configuration items, such as panels, if you apply this.
  1. open a terminal to do these commands
  2. rm -rf ~/.cache/sessions
        This will delete the Xfce4 saved sessions files for your user
  3. rm -rf ~/.config/xfce4/desktop
        This will delete the Xfce4 saved desktop files for your user
  4. restart the system, without saving the session when you hit Quit/restart


the 2. did the trick for me ! thx, man ! It was veeeery annoying.

---

