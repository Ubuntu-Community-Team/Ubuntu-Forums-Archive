---
title: "Building RAID with 12.04"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by ClangerMan on 2012-06-07
Can anyone help me, please, with building a RAID array on a Workstation with UBUNTU 12.04? 
 
I'm using the method and process described in "http://symbolik.wordpress.com/2009/05/01/howto-kubuntu-904-raid-10-lvm2-and-xfs/", originally with Ubuntu 10.04.1, and scripted to speed the process and eliminate "finger trouble". The process generates exactly what I need and does so reliably. Recently I've been experimenting with 11.10 (briefly) and now 12.04, with a view to building a new, powerful and reliable workstation with the new LTS. In both cases the scripts to partition the drives and set-up the Physical Volumes, Volume Groups and Logical Volumes work perfectly and give identical results to the build with 10.04.1.  
 
The end results after installing Ubuntu then LILO, however, are very different. Oneiric ends up with the error 
"The disk drive for / is not ready yet or not present" 
following a list showing the successful identification of all the other mount-points. Confusingly, "/" is the only mounted drive, albeit read-only. This is easily remounted as writeable, and all the other mount-points can be connected manually. I just don't know how to move from there to a running system with GUI. Frankly, I'm happy to abandon this one and concentrate on Pangolin. 
 
With Pangolin the system reliably boots to (initramfs) every time, the visible messages being: 
 
=========================== 
Begin: Running /scripts/init-premount ... done. 
Begin: Mounting root file system ... Begin: Running /scripts.local-top ... done. 
[    2.704146] firewire_core: created device fw0: GUID 001e8c00002ff4b2, S400 
Begin: Running /scripts/local-premount ... done. 
[   32.853769] EXT4-fs (dm-3): mounted with ordered data mode. Opts: (null) 
Begin: Running /scripts/local-bottom ... done. 
done. 
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory 
done. 
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory 
Target filesystem doesn't have requested /sbin/init. 
No init found. Try passing init= bootarg. 
 
 
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash) 
Enter 'help' for a list of built-in commands. 
 
(initramfs) 
============================= 
 
None of the mountable partitions is mounted, and cannot be mounted manually because the system cannot find "/etc/fstab". (Mounting is via the /dev/mapper mechanism). 
 
With Pangolin, but not with Oneiric, I experienced difficulty with downloading bogl-bterm and lilo, and eventually traced this to the fact that /etc/resolv.conf is a link to /run/resolvconf/resolv.conf. The directory /run exists, but doesn't contain /resolvconf. By replacing the link with a file as per my current Lucid desktop, and MANUALLY adding the nameserver line(s) I could get the downloads to work correctly. Experiments revealed that anything in /run/resolvconf doesn't survive a reboot, so isn't persistent enough to be a usable configuration. 
 
With both Oneiric and Pangolin, after LILO has been imported and presents the "Configuring lilo" window and offers: 
"Since kernel using the new disk interface 'libata' you need the newer DiskID and/or UUID in your /etc/lilo.conf for the boot and root options. For the most modern systems you should use this conversion and then run '/sbin/lilo'." 
 
I accept this suggestion (with Oneiric it didn't seem to make any difference if I didn't), and run '/sbin/lilo' after the script to install LILO has concluded. 
 
I appreciate that this description will not provide enough information to determine the problem and its solution. If anyone is willing to step in and help, and tell me what information is required and where to find it, I will eagerly co-operate. 

IF I've been successful there should be an attached tarball containing the script-set and user instructions so you can see exactly how I've done it.

With Grateful Thanks in Anticipation

      Peter

Hardware on which these builds are being tested: 
 
MoBo:        ASUS M4A89TD PRO/USB3 (recommended for KVM) 
CPU:        Phenom II X4 960T (Black Edition) 
RAM:        Kingston KHX1600C9D3B1K2/8GX (2x4GB) 
Graphics:    nVidia GF8400GS 
HDD:        4x Western Digital WD500AAKS 
PSU:        CiT 600UB
OS:        amd64 version

---

### Post by rollacoaster on 2012-06-07
I'm a server newbie running 12.04 and I found this post by **bvz** very helpful "_Step by step guide to setting up Ubuntu 11.10 server for Newbies!_" especially "_Section #7 - Prepare your hard drives to be combined into a RAID 5 array_"

[HTML]http://ubuntuforums.org/showthread.php?t=1895084&highlight=cups+server+11.10[/HTML]

---

### Post by ClangerMan on 2012-06-08
Thanks, Rollacoaster, that is SOME link! I'll give it a try, although the author's report of "several hours to several days" is a significant disincentive. I note that it doesn't involve LVM, which makes me wonder if that is the root of my problems. Here goes!

---

