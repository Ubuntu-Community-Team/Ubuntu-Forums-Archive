---
title: "best file system"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by HappyAsHellas on 2015-11-11
At present I am running Ubuntu 14.04lts, dual booting with windows 10. I have now decided to wipe out windows, upgrade to the latest version of Ubuntu and re-partition the hard drive. I seem to remember reading that the native file system will run faster as opposed to the dual system at present. Performance wise, which is the best system to use?
Oh, and is it possible to do this via an upgrade, or am I better just wiping everything out and starting from scratch again.

---

### Post by TheFu on 2015-11-11
14.04.1   is the recommended  version  for people who need more than a year of support.
Review this page [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) carefully before making any decision. Note the end of support dates.

An important consideration is that 16.04 will be an LTS. If you can wait, there is a direct upgrade path from 14.04.x to 16.04.
The upgrade to 15.10 will be
14.04 --> 14.10 --> 15.04 --> 15.10 --> 16.04

Ok.... the file system question .... short answer is use ext4.

There are many considerations when selecting a file system. Speed cannot be the only consideration, because there are always trade-offs.  If you have 20+TB of data in a single file system, then you'll want to look at XFS.   If you want built-in snapshots, look at BTRFS and ZFS.  ZFS performance can be impressive, but only if the selected HW and storage design follow the sometimes-heavy requirements. ZFS can have bad performance. BTRFS is very impressive, with some caveats.  They may or may not be important to you.

Not every Linux file system can be used as the boot partition. That could be important too.
Planning to use LVM?  Yes?  No?

What do you mean by "dual system?" The easiest thing you could do to get better help is to run a small script and post the URL it provides with system info.
Get  it here:  [http://blog.jdpfu.com/files/quick-sys-info.sh](http://blog.jdpfu.com/files/quick-sys-info.sh)
save it to /tmp/ and
run it with bash /tmp/quick-sys-info.sh

It will ask for a sudo password,  in your situation, the data we need requires it.  Take a look at the script. Lookup any commands for clarification.

---

### Post by HappyAsHellas on 2015-11-11
I ran the script, do I need to copy and paste it here or did it upload somewhere?

---

### Post by TheFu on 2015-11-11
There should have been a URL posted at the end of the run. Just post that.
Or you can copy/paste the output here - please, please, please, use ***_code-tags_*** so everything lines up. Otherwise I won't look at it

---

### Post by HappyAsHellas on 2015-11-11
```

INFO === Running: lsb_release -a

LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


INFO === Running: grep name /proc/cpuinfo

model name    : Intel(R) Pentium(R) CPU B970 @ 2.30GHz
model name    : Intel(R) Pentium(R) CPU B970 @ 2.30GHz


INFO === Running: lscpu

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 42
Stepping:              7
CPU MHz:               800.000
BogoMIPS:              4589.70
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              2048K
NUMA node0 CPU(s):     0,1


INFO === Running: free -m

             total       used       free     shared    buffers     cached
Mem:          7890       1616       6274        281        112        832
-/+ buffers/cache:        671       7219
Swap:            0          0          0


INFO === Running: sudo lshw -sanitize -C video -C network

[sudo] password for george: 
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:41 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: [REMOVED]
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.13.0-68-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:e000(size=256) memory:f7d00000-f7d03fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: [REMOVED]
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 memory:f7c20000-f7c23fff ioport:d100(size=128) ioport:d000(size=256) memory:f7c10000-f7c1ffff memory:f7c00000-f7c0ffff


INFO === Running: route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     9      0        0 wlan0


INFO === Running: ifconfig

eth0      Link encap:Ethernet  HWaddr 00:90:f5:c9:47:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89869 (89.8 KB)  TX bytes:89869 (89.8 KB)

wlan0     Link encap:Ethernet  HWaddr e0:b9:a5:dc:dc:e3  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e2b9:a5ff:fedc:dce3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1754761 (1.7 MB)  TX bytes:774855 (774.8 KB)



INFO === Running: iwconfig

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"virginmedia8696733"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 74:44:01:69:73:9D   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:127   Missed beacon:0



INFO === Running: rfkill list

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


INFO === Running: lsblk

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   100M  0 part 
&#9500;&#9472;sda2   8:2    0 203.2G  0 part 
&#9500;&#9472;sda3   8:3    0 131.9G  0 part 
&#9500;&#9472;sda4   8:4    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0  66.1G  0 part 
&#9500;&#9472;sda6   8:6    0   7.9G  0 part 
&#9492;&#9472;sda7   8:7    0  56.7G  0 part /


INFO === Running: df -h

Filesystem             Size  Used Avail Use% Mounted on
/dev/sda7               56G   36G   18G  68% /
none                   4.0K     0  4.0K   0% /sys/fs/cgroup
udev                   3.9G  4.0K  3.9G   1% /dev
tmpfs                  790M  1.3M  788M   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                   3.9G  372K  3.9G   1% /run/shm
none                   100M   48K  100M   1% /run/user
/home/george/.Private   56G   36G   18G  68% /home/george


INFO === Running: sudo parted -l

Model: ATA Hitachi HTS54755 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  106MB  105MB   primary   ntfs         boot
 2      106MB   218GB  218GB   primary   ntfs
 3      218GB   360GB  142GB   primary   ntfs
 4      360GB   500GB  140GB   extended               lba
 5      360GB   431GB  70.9GB  logical   ntfs
 7      431GB   492GB  60.9GB  logical   ext4
 6      492GB   500GB  8488MB  logical



 =======================
Log file: /tmp/sys-info-2589
Data uploaded to sprunge.us here:

http://sprunge.us/WCQb
george@george-W240HU-W250HUQ:~$ 


```

---

### Post by TheFu on 2015-11-11
Ok.  Having an encrypted home directory is a probably what is slowing down your current setup.  Encrypted HOME directories use a slower encryption technique than whole-drive dm-crypt encryption. There are reasons for both methods, it is just that dm-crypt has very little overhead.
[https://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1) has tests comparing different encryption types.

BTW, there isn't any swap partition. If this is a desktop, 4G of swap is recommended provided you don't intend to hibernate. Hibernation requires a swap larger than the amount of RAM.

The Pentium B970 CPU does not have AES encryption extensions, so all disk encryption using AES will be slower. Selecting another cypher would be recommended.

I always encrypt my portable devices and use LVM on physical machines (including laptops). With all encryption, having excellent backups is mandatory, as you know.

Anyway, I hope this information helps you decide.  We can provide partitioning suggestions.

For whole drive encryption, using LVM makes that easier.  /boot will need to be outside the LVM and encryption, but /, /home, and swap can be inside. A simplistic overview of LVM is that it allows flexible partition management, without having to reboot.  For some file systems, resizing an LV (basically equiv to a partition) can be performed while the system is running. Pretty cool, right?

---

### Post by HappyAsHellas on 2015-11-12
Thank you for your help, greatly appreciated.

---

