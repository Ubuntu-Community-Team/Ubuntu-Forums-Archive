---
title: "Disk knocking, High CPU usage at startup"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-10-14
My disk is still knocking right now. Anyone else ? I saw a lot of udev processes spawned in system monitor and here is a snap of my top:
```


top - 19:42:20 up 7 min,  2 users,  load average: 0.92, 1.12, 0.63
Tasks: 140 total,   3 running, 136 sleeping,   0 stopped,   1 zombie
Cpu(s): 14.4%us, 30.9%sy,  0.0%ni, 35.0%id, 10.9%wa,  0.8%hi,  7.9%si,  0.0%st
Mem:   1925972k total,   654800k used,  1271172k free,   146280k buffers
Swap:        0k total,        0k used,        0k free,   189016k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 7923 root      20   0  256m  28m 7732 R   11  1.5   0:29.79 Xorg                                                                                                                
 8906 rhiken    20   0  132m 3572 2724 S    8  0.2   0:16.47 gvfs-gdu-volume                                                                                                     
 8918 root      20   0 42840 3484 2480 S    4  0.2   0:06.82 devkit-disks-da                                                                                                     
 7669 messageb  20   0 24172 1676  820 S    2  0.1   0:05.14 dbus-daemon                                                                                                         
17124 rhiken    20   0  314m  17m  11m S    2  0.9   0:00.81 gnome-terminal                                                                                                      
  663 root      18  -2 50064 5740  452 S    2  0.3   0:10.16 udevd                                                                                                               
    1 root      20   0 19304 1620 1136 S    1  0.1   0:03.62 init                                                                                                                
  467 root      20   0 21248 1276  948 S    1  0.1   0:03.54 mountall                                                                                                            
  485 root      16  -4 17384 1276  296 S    1  0.1   0:02.59 udevd                                                                                                               
 9019 rhiken    20   0  223m  10m 8348 S    1  0.6   0:02.49 multiload-apple                                                                                                     
   23 root      15  -5     0    0    0 S    0  0.0   0:00.07 ata/1                                                                                                               
   50 root      15  -5     0    0    0 S    0  0.0   0:00.22 scsi_eh_3                                                                                                           
  482 root      20   0 12636  772  556 S    0  0.0   0:01.60 upstart-udev-br                                                                                                     
 8081 root      20   0 22180 1236 1036 S    0  0.1   0:00.08 hald-addon-stor                                                                                                     
 8501 rhiken    20   0  272m  10m 3468 S    0  0.6   0:00.83 pulseaudio                                                                                                          
 8844 rhiken    20   0  406m  19m  13m S    0  1.0   0:01.03 nautilus                                                                                                            
 8919 root      20   0 42180  832  524 S    0  0.0   0:00.99 devkit-disks-da                                                                                                     
12984 rhiken    20   0  401m  59m  24m S    0  3.2   0:09.01 chromium-browse                                                                                                     
17243 rhiken    20   0 19132 1344  980 R    0  0.1   0:00.09 top                                                                                                                 
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                            
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                         
    4 root      15  -5     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0                                                                                                         
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                          
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/1                                                                                                         
    7 root      15  -5     0    0    0 S    0  0.0   0:00.05 ksoftirqd/1             

```

---

### Post by stinger30au on 2009-10-14
if the hdd is making a clicking noise, replace it

its on its last legs

i have had a run of hdds like this for the past few months

---

### Post by Regenweald on 2009-10-14
I doubt it's that. All report healthy, only started after the last set of disk related  services updates. Will leave it a couple of days and wait for some updates. If i knew exactly what it was i could report it.

---

### Post by novafluxx on 2009-10-14
> **Regenweald said:**
> I doubt it's that. All report healthy, only started after the last set of disk related  services updates. Will leave it a couple of days and wait for some updates. If i knew exactly what it was i could report it.

If the hard drive is REALLY making a distinct 'clicking' sound, its dying, its gonna fail hard too, as in you'll probably need a cleanroom to open it to salvage any data from it. Usually the clicking is mechanical failure.

If you doubt it, then by all means, continue to run like this, but PLEASE backup your important data ASAP.

Also, try to verify it IS the hard drive clicking, and not speakers popping or something else.

Try to identify all potential mechanical devices inside your machine, and attempt to rule them out as potentially causing the issue.

---

### Post by ranch hand on 2009-10-15
> **novafluxx said:**
> if the hard drive is really making a distinct 'clicking' sound, its dying, its gonna fail hard too, as in you'll probably need a cleanroom to open it to salvage any data from it. Usually the clicking is mechanical failure.

If you doubt it, then by all means, continue to run like this, but please backup your important data asap.

Also, try to verify it is the hard drive clicking, and not speakers popping or something else.

Try to identify all potential mechanical devices inside your machine, and attempt to rule them out as potentially causing the issue.
+1

---

### Post by Regenweald on 2009-10-15
> **novafluxx said:**
> If the hard drive is REALLY making a distinct 'clicking' sound, its dying, its gonna fail hard too, as in you'll probably need a cleanroom to open it to salvage any data from it. Usually the clicking is mechanical failure.

If you doubt it, then by all means, continue to run like this, but PLEASE backup your important data ASAP.

Also, try to verify it IS the hard drive clicking, and not speakers popping or something else.

Try to identify all potential mechanical devices inside your machine, and attempt to rule them out as potentially causing the issue.

Will do.

---

### Post by P4man on 2009-10-15
Please read this:
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html)

And this:
>  Originally Posted by MacUntu  View Post
To shut the thing up temporarily comment out the last line of /etc/modprobe.d/alsa-base.conf (something like "options snd-hda-intel power_save=10 ...").

If the latter removes the issue, file a bug report as requested in the first link.

---

### Post by Regenweald on 2009-10-15
> **P4man said:**
> Please read this:
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html)

And this:


If the latter removes the issue, file a bug report as requested in the first link.

Thanks, will check for updates first. Then attempt fix.

---

### Post by Regenweald on 2009-10-15
It would seem that it was udev. I used Boot-up-Manager to start then stop the service and the knocking sound as well as high cpu usage immediately halted. 
many thanks to all suggestions.

---

