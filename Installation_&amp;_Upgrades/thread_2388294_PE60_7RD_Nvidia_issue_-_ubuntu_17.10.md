---
title: "PE60 7RD Nvidia issue - ubuntu 17.10"
date: 2018-03-31
forum: Installation &amp; Upgrades
---

### Post by vijayk-kannan on 2018-03-31
Hello Geeks,

I am from Bangalore , with the intention of learning ML and AL I have bought  my MSI PE60 7RD with extended support of 250GB SSD.

I have installed ubuntu 17.10 after various issues , now I am facing given below doubts or issues

1. There was no bios option to default setting of display device , currently if i set prime-select profile to Intel then only I was able to login into the system if I change that to nvidia its looping at booting
2. There was no prime profiles listing in nvidia settings GUI, the only option i have left was prime-select on command prompt
3. Battery drying out easily
4. When I run multiple tensorflow gpu test codes in nvidia-smi only once core was utilized why other cores wasnt utilized?
5. How do i make sure that I have installed or configured nvidia / cuda correctly? and make sure the GPU utilization achieved
6. Yesterday twice my laptop got automatically rebooted I am still trying to figure out how that happened?
7. When I use chrome and scroll down the site I am seeing there was a wave effect is that normal on MSI with my configuration ?

What I have so far
Ubuntu 17.10 , Kernel version - 4.13.0-37-generic
#WaylandEnable=false ==> on gdm custom.conf

nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2016 NVIDIA Corporation
Built on Tue_Jan_10_13:22:03_CST_2017
Cuda compilation tools, release 8.0, V8.0.61
nvidia-smi
Sat Mar 31 12:09:49 2018       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.48                 Driver Version: 390.48                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1050    Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   45C    P0    N/A /  N/A |      0MiB /  4042MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

cat /proc/driver/nvidia/version 
NVRM version: NVIDIA UNIX x86_64 Kernel Module  390.48  Thu Mar 22 00:42:57 PDT 2018
GCC version:  gcc version 7.2.0 (Ubuntu 7.2.0-8ubuntu3.2) 

If anyone from bangalore here and successfully done nvidia installation along with ubutun pls ping me I would like to show my issues in person and learn / sharing experience 

Highly appreciated if someone can explain / help on this

---

### Post by ubfan1 on 2018-04-03
1) login loop may be a result of the dot files (files beginning with a ".") in your home directory.  Can you login to guest?  If so that's probably the problem, so move them to a directory (in case you need to get something like mail from one of them), and let them be recreated.  See the askubuntu.com site for "login loop" questions.
2)-4)??
5) Install the Nvidia drivers first, from the Ubuntu repositories and get login working, then install the cuda deb file downloaded from Intel, then the cudnn downloads.  Then the cuda package from Ubuntu, then Tensorflow after cuda is working.  I've not actually installed Tensorflow on my system.  Your output is missing some critical parts of the nvidia-smi,like the capability, but I think the 1050 is 6.1, (from [https://developer.nvidia.com/cuda-gpus](https://developer.nvidia.com/cuda-gpus)) which should be sufficient for cuda 9.1.
6)Install the lm-sensors package and with the sensors command, check the temperature.  Heavy GPU useage tends to overheat laptops.  Additional cooling may be needed.
7)Sadly, the "wave" is normal, since the synchronization between the Intel GPU and Nvidia tends to not be perfect.  Some solutions may be possible from the askubuntu.com site, but the ones I've tried have not solved my issue.
Hope some of the above helps.

---

### Post by vijayk-kannan on 2018-04-03
Thanks for taking your time and explaining it, yes it helps.

I have tried that . files renaming and rebooting on tty but still if I choose prime-select option as Nvidia and reboot system just hangs at boot showing ubuntu logo and dots
Regarding questions 2 - its about switching between prime profiles on intel / nvidia through nvidia settings GUI there I couldn't able to see the profiles 
3 - saw that battery dries out quickly if I run tensorflow and  simple tensorflow -mnist example of hand written digits code hangs after 2000th record
4 - I have GTX 1050 which was considered as single GPU ? i.e. if I run multiple models getting memory out error and all process ends up on 0th core , little confused here
5 - I have able to see the process on nividia-smi when i run tensorflow mnist example 
7 - Its too bad that both intel and nvidia not working in tandem :-(

attached some of the screenshots

---

