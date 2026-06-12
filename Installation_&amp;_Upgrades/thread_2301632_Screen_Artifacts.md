---
title: "Screen Artifacts"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by chris426 on 2015-11-03
Somewhere along the line of distribution and package upgrades, something seems to have broke and now I have these annoying square artifacts on my desktop.

I have seen these old threads regarding the square artifacts and they look exactly like the same problem I have:
[Thread 1]("http://ubuntuforums.org/showthread.php?t=1962493")
[Thread 2]("http://www.overclockers.com/forums/showthread.php/705452-Small-squares-of-random-pixels-static-artifact-on-video-card")

I figure I would post in here first as I'm not convinced it's hardware as some people might initially conclude.  I'm convinced it's a driver problem but would appreciate if someone had other ideas on how to fix this.


My background:
I have been using Ubuntu since 5.04 (Hoary Hedgehog)
I know my way around Linux fairly well.
I don't post a lot.  I've had to create a new account because of OpenId.  I usually find an answer if I'm patient enough but I've broken down! haha :D  I've had this issue sometime during 14.04, I'm on 15.10 now.

My current system
```
root@box-ubuntu:~# uname -a
Linux box-ubuntu 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
root@box-ubuntu:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu 15.10"
```
```
root@box-ubuntu:/media/share1/Linux# nvidia-smi
Tue Nov  3 18:05:39 2015
+------------------------------------------------------+
| NVIDIA-SMI 355.11     Driver Version: 355.11         |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTS 450     Off  | 0000:01:00.0     N/A |                  N/A |
| 40%   37C    P0    N/A /  N/A |      3MiB /  1022MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+


+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0                  Not Supported                                         |
+-----------------------------------------------------------------------------+
```
```

root@box-ubuntu:~# lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 60
Model name:            Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
Stepping:              3
CPU MHz:               4400.000
CPU max MHz:           4400.0000
CPU min MHz:           800.0000
BogoMIPS:              8000.08
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              8192K
NUMA node0 CPU(s):     0-7
root@box-ubuntu:~#
```
```
root@box-ubuntu:~# free -m
             total       used       free     shared    buffers     cached
Mem:         32036      31805        230         94        246      28267
-/+ buffers/cache:       3291      28744
Swap:         9998          0       9998
```

What I've done so far:
[LIST]
[*]I've run [memtestCL]("https://github.com/ihaque/memtestCL") and have not been able to generate a single error yet.
[*]I've tried all the following but all produce the same results:
[LIST]
[*]NVIDIA-Linux-x86_64-304.128.run
[*]NVIDIA-Linux-x86_64-340.93.run
[*]NVIDIA-Linux-x86_64-352.55.run
[*]NVIDIA-Linux-x86_64-355.11.run (currently installed)
[/LIST]

[*]I noticed is that if I run the Folding@Home Client and do Full Folding (to include the GPU)... these artifacts seem to go away, but this obviously can't be the solution :-/
[/LIST]

My latest [FONT=courier new]/var/log/nvidia-installer.log
[/FONT]```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Nov  3 18:04:56 2015
installer version: 355.11


PATH: /usr/StorMan/pegasus/bin:/usr/StorMan/ssl/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


nvidia-installer command line:
    ./nvidia-installer


Using: nvidia-installer ncurses user interface
-> Detected 8 CPUs online; setting concurrency level to 8.
-> License accepted.
-> Installing NVIDIA driver version 355.11.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Are you sure you want to continue? (Answer: Continue installation)
-> Would you like to register the kernel module sources with DKMS? This will allow DKMS to automatically build a new module, if you install a different kernel later. (Answer: Yes)
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility libraries? (Answer: No)
-> Skipping installation of the libvdpau wrapper library.
-> Searching for conflicting files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (355.11):
   executing: '/sbin/ldconfig'...
-> done.
-> Driver file installation is complete.
-> Installing DKMS kernel module:
-> done.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update your X configuration file so that the NVIDIA X driver will be used when you restart X?  Any pre-existing X configuration file will be backed up. (Answer: Yes)
-> Your X configuration file has been successfully updated.  Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86_64 (version: 355.11) is now complete.

```

I am suspecting its a driver problem, but I suspect it's going to be a hard process to find which nvidia branch and version should I be using.  In the threads I mentioned above, it sounds like a bug was introduced but seems in the latest releases, the bug is still present or was reintroduced again.

Here's a short clip of what it appears.  Sorry it might be hard to see but there are blue squares that show up on the black background.  Usually if I leave it long enough there are multiple colors.
[http://i.imgur.com/YSLYmTZ.gifv](http://i.imgur.com/YSLYmTZ.gifv)

edit: here's a better picture
[IMG]http://i.imgur.com/ROwi0g8.png[/IMG]

---

### Post by chris426 on 2015-11-03
edit: moved info to above comment

---

### Post by chris387 on 2016-08-30
I have tried many things but cannot sort out this issue.  Am I really the only one with this problem?  I've tried Ubuntu Live and don't notice the issue but I haven't isolated whether this is a result of using nouveau vs. nvidia drivers.  Anyone?

---

### Post by chris387 on 2016-09-06
What is interesting is when I run FAHClient (and use the GPU), the issue does not appear to occur, however, the desktop is quite unusable in the sense that it is very slow to respond.

---

### Post by chris387 on 2016-09-08
I decided to revert to using the NOUVEAU driver and things seems to be working fine.  No artifacts at all

---

