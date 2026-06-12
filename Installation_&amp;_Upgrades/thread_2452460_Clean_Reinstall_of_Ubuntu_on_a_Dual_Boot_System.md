---
title: "Clean Reinstall of Ubuntu on a Dual Boot System"
date: 2020-10-22
forum: Installation &amp; Upgrades
---

### Post by lambs2 on 2020-10-22
Hi,

So few months ago I built a PC and successfully installed a dual boot system: Windows 10 Education and Linux Ubuntu 18.04 (computer turns on, sends me to a menu with Ubuntu, Windows boot etc. Ubuntu being default if no other option is selected).
Everything seemed to be working great. Fast performance, quiet fans etc. until recently. Here's the issues:

1. My PC fans are constantly fluctuating whether idling or not and pretty loud when trying to open up something as simple as a the terminal, files folder or webpage.
2. In attempt to configure my system for school, get my bluetooth and dual monitor working, I've had to install lots of random packages. My file system seems like a total clutter and I know longer know what I'm able to delete without messing up the entire system.

---

### Post by grahammechanical on 2020-10-22
If you have installed applications through the Software Centre, then use the Software Centre to uninstall. If you have installed applications/packages through the command line, then use the apt remove or apt purge commands.

In a terminal type

```
man apt
```

to learn about the apt command

>  Removing a package removes all packaged data, but leaves usually small (modified) user configuration files behind, in case the remove was an accident. Just issuing an installation request for the accidentally removed package will restore its function as before in that case. On the other hand you can get rid of these leftovers by calling purge even on already removed packages. Note that this does not affect any data or configuration stored in your home directory.

Regards

---

### Post by lambs2 on 2020-10-22
Hello!

**First, a little background info:**
So few months ago I built a PC and successfully installed a dual boot system: Windows 10 Education and Linux Ubuntu 18.04 (computer turns on, pops up a menu with Ubuntu, Windows boot etc. options, Ubuntu being default if no other option is selected). Everything seemed to be working great. Fast performance, quiet fans etc. until recently. 
[U][B][COLOR=#a52a2a]
[/COLOR][/B][/U]**[COLOR=#a52a2a]Here's the issues:[/COLOR]**[U][B][COLOR=#a52a2a]
[/COLOR][/B][/U]*Note: *I have provided Basic system info, disk partitioning details, some command line results below, just in case.*
[B]
1. My PC fans are constantly fluctuating whether idling or not and pretty loud when trying to open up something as simple as a the terminal, files folder or webpage.[/B]
- Someone suggested it might be my GPU. When running checks/tests through terminal, I noticed that my GPU fans are running at 300MHz (on idle). Tried to run some programs/videos in the background and the results remained the same.
- lm-sensors doesn't show the amount of information that other people are describing. It can't properly detect my GPU.
[B]
2. In attempt to configure my system for school online etc. I've had to install a lot of different packages. I have no idea know what I'm able to delete without messing up the entire system.[/B]
- I've tried clearing up space using basic terminal commands for cleaning, purging, cache etc. but surprisingly, I haven't used a ton of storage on my disk.

**3. I'm not sure if there's any way of resetting my Ubuntu system to "factory" state (deleting all manually installed applications etc.) or if there's a way to  clean reinstall Ubuntu onto my system without messing with the Windows dual boot **(I only activation key one for the education version) or the grub menu setup. I'm not concerned about backing anything up on the Linux to be honest as I have nearly zero personal files on my system (I use Linux strictly for programming most of which is pushed onto Gitlab).

Now I know that some of the information seems vague (happy to share more details/results if needed), issues may be unrelated and some of the information may be completely irrelevant but thought I'd try and show the "big picture". I've tried a lot of things and the vast amounts of different information  can get quite confusing for someone whose fairly new to Ubuntu. 

If somebody could please provide me with some solid information on what the issue with the fans could be, whether option 3 is necessary and if so, how to do it, that would be MUCH appreciated. 
Like I said, I've ran quite a few check commands on my terminal and have saved the results in a text file for future reference if needed.


[B]Basic System Information:
[/B]Memory: 15.6 GiB
Processor: AMD Ryzen 3600
Graphics: NVIDIA [GeForce GTX 1660 SUPER]
Disk Capacity 1.5 TB (shows total capacity including SSD)

OS Name: Ubuntu 20.04.1 LTS
OS Type: 64-bit
GNOME Version: 3.36.3
Windowing System: X11
Kernel Release: 5.4.0-52-generic
[B]

Disk Partioning:
[/B]1TB Hard Disk (Linux)
/deb/sdb1 (30GB) - 22GB Free  (26.6% full) | Partition Type: Linux Filesystem | Contents: Ext4 (v 1.0)  - Mounted at Filesystem root
/dev/sdb2 (25GB) | Partition Type: Linux Swap (v1) - Active
/dev/sdb3 (650MB) | Partition Type: EFI System | Contents: FAT(32-bit-version) - Not mounted
/dev/sdb4 (945GB) - 927GV Free (1.8% full) | Partition Type: Linux Filesystem) | Contents: Ext4 (v 1.0) - Mounted at /home

500GB SSD (Windows)
/dev/sda1  (555MB) | Partition Type: Microsoft Windows Recovery Environment  (System, No Automount) | Contents: NTFS - not mounted 
/dev/sda2 (104MB) - 65 MB Free (37.0% full) | Partition Type: EFI System | Contents: FAT(32-bit-version) - Mounted at /boot/efi
/dev/sda3 (17MB) | Partition Type: Microsoft Reserved (No Automount) | Contents: Unknown
/dev/sda4 (499GB) | Partition Type: Basic Data | Contents: NTFS - Not Mounted
/dev/sda (1.1MB) | Contents: Unallocated Space


**GPU detailed results via. terminal command:**
command > **nvidia-smi**
+--------------------------------------------------------------------------------------------------------------+
| NVIDIA-SMI 450.80.02    Driver Version: 450.80.02          CUDA Version: 11.0         |
|----------------------------------------------+--------------------------------+------------------------------+
| GPU  Name        Persistence-M    | Bus-Id             Disp.A    | Volatile   Uncorr. ECC  |
| Fan  Temp  Perf  Pwr:Usage/Cap |              Memory-Usage | GPU-Util  Compute M. |
|                                                       |                                       |                         MIG M  |
|==========================+==================+==================|
|   0  GeForce GTX 166...  Off         | 00000000:08:00.0  On   |                              N/A |
|  0%   37C    P8    10W / 130W      |    380MiB /     5936MiB   |      1%             Default |
|                                                       |                                        |                              N/A |
+---------------------------------------------+---------------------------------+-----------------------------+                                                                          
+--------------------------------------------------------------------------------------------------------------+
| Processes:                                                                                                                   |
|  GPU GI   CI        PID   Type   Process name                                       GPU Memory |
|           ID   ID                                                                                                Usage      |
|================================================================|
|    0   N/A  N/A       913       G   /usr/lib/xorg/Xorg                                              35MiB  |
|    0   N/A  N/A      1761      G   /usr/lib/xorg/Xorg                                             164MiB |
|    0   N/A  N/A      1889      G   /usr/bin/gnome-shell                                        155MiB |
|    0   N/A  N/A      2374      G   /usr/lib/firefox/firefox                                         2MiB    |
|    0   N/A  N/A      3183      G   /usr/lib/firefox/firefox                                         2MiB    |
|    0   N/A  N/A      3392      G   /usr/lib/firefox/firefox                                         2MiB    |
|    0   N/A  N/A      5329      G   /usr/lib/firefox/firefox                                         2MiB    |
+---------------------------------------------------------------------------------------------------------------+

command > [B]nvidia-smi -q -d CLOCK
[/B]==============NVSMI LOG==============

Timestamp                                      : Thu Oct 22 11:23:58 2020
Driver Version                                 : 450.80.02
CUDA Version                                 : 11.0

Attached GPUs                                : 1
GPU 00000000:08:00.0
    Clocks
        Graphics                                  : 360 MHz
        SM                                           : 360 MHz
        Memory                                    : 405 MHz
        Video                                        : 540 MHz
    Applications Clocks
        Graphics                                   : N/A
        Memory                                    : N/A
    Default Applications Clocks
        Graphics                                   : N/A
        Memory                                    : N/A
    Max Clocks
        Graphics                                   : 2145 MHz
        SM                                            : 2145 MHz
        Memory                                    : 7001 MHz
        Video                                        : 1950 MHz
    Max Customer Boost Clocks
        Graphics                                   : N/A
    SM Clock Samples
        Duration                                   : Not Found
        Number of Samples                 : Not Found
        Max                                          : Not Found
        Min                                           : Not Found
        Avg                                           : Not Found
    Memory Clock Samples
        Duration                                   : Not Found
        Number of Samples                 : Not Found
        Max                                          : Not Found
        Min                                           : Not Found
        Avg                                           : Not Found
    Clock Policy
        Auto Boost                               : N/A
        Auto Boost Default                   : N/A

---

### Post by QIII on 2020-10-22
Threads merged.

Please do not start duplicate threads.  That waters down the community's efforts to help you since your answers maybe seen by different people, answered differently and cause duplication of effort.

If you have more information to provide, please do so in the original thread.

Thanks.

---

