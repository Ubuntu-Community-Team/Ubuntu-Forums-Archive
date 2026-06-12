---
title: "Packages held back - but not due to phasing apparently?"
date: 2023-01-28
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2023-01-28
I tend to update/upgrade once a week and noticed the relatively new behavior of packages held back due to phasing
... which I actually like to avoid broken packages. But these usually resolve in a few days (or by next weeks update).

Lately, however, I noticed nvidia-525 driver and related packages (22 of them) being held back and not resolving for weeks.
I did a few checks shown below and at the end, I am asking for advice on whether I should perform a 'aptitude safe-upgrade' and force the issue:


I checked the log on phase status and there is none (no phasing underway):
> 
sudo apt-cache policy libnvidia-cfg1-525 libnvidia-compute-525 libnvidia-compute-525:i386
libnvidia-cfg1-525:
  Installed: 525.60.11-0ubuntu0.22.04.1
  Candidate: 525.78.01-0ubuntu0.22.04.1
  Version table:
     525.78.01-0ubuntu0.22.04.1 500
        500 [http://mirror.team-cymru.com/ubuntu](http://mirror.team-cymru.com/ubuntu) jammy-updates/restricted amd64 Packages
        500 [http://mirror.team-cymru.com/ubuntu](http://mirror.team-cymru.com/ubuntu) jammy-security/restricted amd64 Packages
 *** 525.60.11-0ubuntu0.22.04.1 100
        100 /var/lib/dpkg/status
libnvidia-compute-525:
  Installed: 525.60.11-0ubuntu0.22.04.1
  Candidate: 525.78.01-0ubuntu0.22.04.1
  Version table:
     525.78.01-0ubuntu0.22.04.1 500
        500 [http://mirror.team-cymru.com/ubuntu](http://mirror.team-cymru.com/ubuntu) jammy-updates/restricted amd64 Packages
        500 [http://mirror.team-cymru.com/ubuntu](http://mirror.team-cymru.com/ubuntu) jammy-security/restricted amd64 Packages
 *** 525.60.11-0ubuntu0.22.04.1 100
        100 /var/lib/dpkg/status
libnvidia-compute-525:i386:
  Installed: 525.60.11-0ubuntu0.22.04.1
  Candidate: 525.78.01-0ubuntu0.22.04.1
  Version table:
     525.78.01-0ubuntu0.22.04.1 500
        500 [http://mirror.team-cymru.com/ubuntu](http://mirror.team-cymru.com/ubuntu) jammy-updates/restricted i386 Packages
        500 [http://mirror.team-cymru.com/ubuntu](http://mirror.team-cymru.com/ubuntu) jammy-security/restricted i386 Packages
 *** 525.60.11-0ubuntu0.22.04.1 100
        100 /var/lib/dpkg/status

I thought I already had nvidia driver 525 installed?

> 
vidia-smi 
Sat Jan 28 07:03:46 2023       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.60.11    Driver Version: 525.60.11    CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0 Off |                  N/A |
| 34%   28C    P8    N/A /  30W |     73MiB /  2048MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      7311      G   /usr/lib/xorg/Xorg                 55MiB |
|    0   N/A  N/A      7442      G   /usr/bin/gnome-shell               15MiB |
+-----------------------------------------------------------------------------+


So I checked the log on unattended upgrades and noticed:

> 2023-01-28 06:42:36,633 INFO Package nvidia-compute-utils-525 is kept back because a related package is kept back or due to local apt_preferences(5).
2023-01-28 06:42:36,635 INFO Package nvidia-driver-525 is kept back because a related package is kept back or due to local apt_preferences(5).
2023-01-28 06:42:36,637 INFO Package nvidia-kernel-common-525 is kept back because a related package is kept back or due to local apt_preferences(5).
2023-01-28 06:42:36,639 INFO Package nvidia-kernel-source-525 is kept back because a related package is kept back or due to local apt_preferences(5).
2023-01-28 06:42:36,641 INFO Package nvidia-utils-525 is kept back because a related package is kept back or due to local apt_preferences(5).
2023-01-28 06:42:36,682 INFO Package xserver-xorg-video-nvidia-525 is kept back because a related package is kept back or due to local apt_preferences(5).

Finally, I tried aptitude safe-upgrade .....

> sudo aptitude safe-upgrade --full-resolver
The following packages will be upgraded: 

  libnvidia-cfg1-525 libnvidia-compute-525 libnvidia-compute-525:i386 libnvidia-decode-525 libnvidia-decode-525:i386 libnvidia-encode-525 
  libnvidia-encode-525:i386 libnvidia-extra-525 libnvidia-fbc1-525 libnvidia-fbc1-525:i386 libnvidia-gl-525 libnvidia-gl-525:i386 
  linux-modules-nvidia-525-5.15.0-58-generic linux-modules-nvidia-525-generic-hwe-22.04 linux-objects-nvidia-525-5.15.0-58-generic 
  linux-signatures-nvidia-5.15.0-58-generic nvidia-compute-utils-525 nvidia-driver-525 nvidia-kernel-common-525 nvidia-kernel-source-525 nvidia-utils-525 
  xserver-xorg-video-nvidia-525 
22 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 435 MB/492 MB of archives. After unpacking 2,858 kB will be used.
The following packages have unmet dependencies:
 linux-modules-nvidia-525-5.15.0-57-generic : Depends: nvidia-kernel-common-525 (<= 525.60.11-1) but 525.78.01-0ubuntu0.22.04.1 is to be installed
The following actions will resolve these dependencies:

     Remove the following packages:                                                                    
1)     linux-modules-nvidia-525-5.15.0-57-generic [5.15.0-57.63+1 (jammy-security, jammy-updates, now)]

Accept this solution? [Y/n/q/?] 

But before I click 'yes' - am I likely to cause more problems than I solve? It does seem something got lost along the way during my routine upgrade process.
Advice very welcome on this! Thanks

---

### Post by imagerodeo on 2023-04-30
I have the same problem. Any insight?

---

### Post by ubfan1 on 2023-04-30
What kernel are you running?  Looks like a 5.15, but I see some hwe packages for 22.04, so that should have a 5.19 kernel installed. I'm running a 5.19 kernel on 22.04, and the associated 515 driver is 525.105.17.  I did get rid of the old 5.15 kernels after getting the 5.19s.  If you have both, may the old one is causing problems?

---

