---
title: "Moving from HDD to SSD"
date: 2015-12-12
forum: Installation &amp; Upgrades
---

### Post by koma77 on 2015-12-12
Today I have one small SSD containing my Ubuntu installation, except the /home directory. I also have a big HDD containing /home, but also a windows 10 installation.

I think it is time to go full SSD and I would like to migrate to 2 SSDs of 1TB each. One SSD for Ubuntu and one for windows (for gaming...).

My Ubuntu installation (well /home at least) is backed up with Deja Dup.

I wonder what the best way is to do the migration and hope that someone here have good insights and suggestions.

Is it a good idea to re-install Ubuntu from scratch and use Deja Dup to recover my files?
If so, is there a good way to install or at least see which packets I have manually installed from the Ubuntu repository?
What about configuration files that I may have edited.. It's a long time since I installed my Ubuntu system. Can I see which config files that differ from the default installation files somehow?

And, a bit of topic perhaps, but is there any way to migrate a windows 10 installation to a new drive?

---

### Post by TheFu on 2015-12-12
Perform all work from a live-boot Linux.  If you used LVM, things will be a little more complicated.
Under Linux, if the directories all get mounted so an **ls** shows them to be in the correct place, then everything will be fine. Of course, grub/boot and swap will need to be handled outside that. Manual edits to **sudoedit /etc/fstab** will be needed, as will **grub-install** and **update-grub**. Again, if the directories are in the correct place, Linux won't care how they are mounted.

So ... let's start by gathering some information. Run this script and post the created URL back here: 
[http://blog.jdpfu.com/files/quick-sys-info.sh](http://blog.jdpfu.com/files/quick-sys-info.sh)

It gathers a little more data than needed, but for surgery like this, best to share more than less.

BTW, if you've never tested DejaDup restore, you don't actually have a backup. You have "hope."

Cannot help at all with Windows.  In the old days, it was always required (best?), to install Windows first, since that OS maker never looked for Linux and still wipes the boot sector without regard for any other OS. Maybe it is better with UEFI? I dunno.

I appreciate all these people testing out new storage tech for me. Thank you.

---

### Post by koma77 on 2015-12-12
Here is the output of the script:



```

INFO === Running: lsb_release -a

LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


INFO === Running: grep name /proc/cpuinfo

model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
model name	: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz


INFO === Running: lscpu

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                12
On-line CPU(s) list:   0-11
Tråd(ar) per kärna:  2
Core(s) per socket:    6
Socket(s):             1
NUMA-nod(er):          1
Tillverkar-id:         GenuineIntel
Processorfamilj:       6
Modell:                63
Model name:            Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
Stepping:              2
Processorns MHz:       2095.628
CPU max MHz:           3600,0000
CPU min MHz:           1200,0000
BogoMIPS:              6596.11
Virtualisering:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              15360K
NUMA node0 CPU(s):     0-11


INFO === Running: free -m

             total       used       free     shared    buffers     cached
Mem:         15821       5208      10612         74        644       1585
-/+ buffers/cache:       2978      12842
Swap:         3153          0       3153


INFO === Running: sudo lshw -sanitize -C video -C network

  *-display
       beskrivning: VGA compatible controller
       produkt: GM204 [GeForce GTX 970]
       tillverkare: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       bredd: 64 bits
       klocka: 33MHz
       förmågor: pm msi pciexpress vga_controller bus_master cap_list rom
       konfiguration: driver=nvidia latency=0
       resurser: irq:47 memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(storlek=128) memory:fb000000-fb07ffff
  *-network
       beskrivning: Ethernet interface
       produkt: Ethernet Connection (2) I218-V
       tillverkare: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logiskt namn: eth3
       version: 05
       serienummer: [REMOVED]
       storlek: 1Gbit/s
       kapacitet: 1Gbit/s
       bredd: 32 bits
       klocka: 33MHz
       förmågor: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       konfiguration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k duplex=full firmware=0.1-4 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resurser: irq:43 memory:fb200000-fb21ffff memory:fb239000-fb239fff ioport:f020(storlek=32)
  *-network
       beskrivning: Trådlöst gränssnitt
       physical id: 1
       bus info: usb@1:7
       logiskt namn: wlan2
       serienummer: [REMOVED]
       förmågor: ethernet physical wireless
       konfiguration: broadcast=yes driver=ath9k_htc driverversion=4.2.0-19-generic firmware=1.3 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bgn


INFO === Running: route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         routern         0.0.0.0         UG    100    0        0 eth3
link-local      *               255.255.0.0     U     1000   0        0 eth3
192.168.1.0     *               255.255.255.0   U     100    0        0 eth3
192.168.2.0     *               255.255.255.0   U     600    0        0 wlan2


INFO === Running: ifconfig

eth3      Link encap:Ethernet  HWaddr ac:9e:17:b3:d6:d5  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae9e:17ff:feb3:d6d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79849460 (79.8 MB)  TX bytes:5716687 (5.7 MB)
          Interrupt:20 Minne:fb200000-fb220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3439 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:469071 (469.0 KB)  TX bytes:469071 (469.0 KB)

wlan2     Link encap:Ethernet  HWaddr f8:1a:67:1d:29:77  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::fa1a:67ff:fe1d:2977/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1280  Metric:1
          RX packets:2726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1030166 (1.0 MB)  TX bytes:136536 (136.5 KB)



INFO === Running: iwconfig

wlan2     IEEE 802.11bgn  ESSID:"e4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:0F:E6:33:42   
          Bit Rate=2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=25/70  Signal level=-85 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:22  Invalid misc:574   Missed beacon:0



INFO === Running: rfkill list

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


INFO === Running: lsblk

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  74,5G  0 disk 
&#9500;&#9472;sda1   8:1    0  71,5G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   3,1G  0 part [SWAP]
sdb      8:16   0   1,4T  0 disk 
&#9500;&#9472;sdb1   8:17   0   616G  0 part 
&#9492;&#9472;sdb2   8:18   0 781,3G  0 part /home
sr0     11:0    1  1024M  0 rom  


INFO === Running: df -h

Filsystem                          Storlek Använt Ledigt Anv% Monterat på
udev                                  7,8G      0   7,8G   0% /dev
tmpfs                                 1,6G    11M   1,6G   1% /run
/dev/sda1                              71G    30G    37G  45% /
tmpfs                                 7,8G    39M   7,7G   1% /dev/shm
tmpfs                                 5,0M   4,0K   5,0M   1% /run/lock
tmpfs                                 7,8G      0   7,8G   0% /sys/fs/cgroup
tmpfs                                 7,8G   1,1M   7,8G   1% /tmp
/dev/sdb2                             769G   573G   158G  79% /home
SynologyNAS1.local:/volume1/Faust1    3,6T   938G   2,7T  26% /nas
tmpfs                                 1,6G    52K   1,6G   1% /run/user/1000
/home/faust1/.Private                 769G   573G   158G  79% /home/faust1/Private


INFO === Running: sudo parted -l

Modell: ATA INTEL SSDSA2M080 (scsi)
Disk /dev/sda: 80,0GB
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: msdos
Disk Flags: 

Nummer  Början  ****    Storlek  Typ       Filsystem       Flaggor
 1      32,3kB  76,7GB  76,7GB   primary   ext4            startbar
 2      76,7GB  80,0GB  3307MB   extended
 5      76,7GB  80,0GB  3307MB   logical   linux-swap(v1)


Modell: ATA WDC WD15EADS-00P (scsi)
Disk /dev/sdb: 1500GB
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: msdos
Disk Flags: 

Nummer  Början  ****    Storlek  Typ      Filsystem  Flaggor
 1      32,3kB  661GB   661GB    primary  ntfs       startbar
 2      661GB   1500GB  839GB    primary  ext4


```

---

### Post by oldfred on 2015-12-12
You are showing a new Intel chip, lots of RAM, but MBR partitioning.
And Windows only boots in BIOS mode from MBR partitioning.  And Windows only boots in UEFI mode from gpt. And how you boot install media is how it installs.
Almost all new systems like yours use UEFI with gpt partitioning. But you would not be able to copy Windows from a BIOS/MBR install to UEFI/gpt install.

So you either stay with the well known but 35 year old BIOS/MBR configuration or reinstall from scratch. Not sure if Windows will even let you do that without a new license.

I would reinstall Ubuntu whether new UEFI/gpt or BIOS/MBR. I just installed 16.04 in a test partition in 10 minutes.  And new install gives you the opportunity to change to gpt on the Ubuntu drive as Ubuntu can boot in BIOS or UEFI from gpt. And make first partition an ESP - efi system partition and second partition a bios_grub partition. Then you can install in either UEFI or BIOS or later change without totally repartitioning drive. If BIOS you must use MBR on Windows drive though.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

   UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[URL="http://askubuntu.com/questions/446968/legacy-vs-uefi-help"]http://askubuntu.com/questions/446968/legacy-vs-uefi-help

      [/URL]
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

    [URL="http://askubuntu.com/questions/446968/legacy-vs-uefi-help"]
[/URL]

---

### Post by koma77 on 2015-12-12
Thank you for your detailed response!

I will need to read up on UEFI a bit and digest the information you kindly supplied before I spring to action.

---

### Post by Bucky Ball on 2015-12-12
I used [this method]("https://frankfzw.wordpress.com/2014/12/23/migrate-ubuntu-14-04-from-hdd-to-ssd/") just today and am currently posting from the new install on my SSD which is identical to the install on my hard drive (except quicker!).

I did the rsync from the running HDD install of Ubuntu I wanted to clone to the SSD. Don't see it would be much/any different if you used the same procedure from ssd to ssd. :)

---

### Post by oldfred on 2015-12-12
@Bucky Ball & OP

Example fstab entry is not the preferred now. If configured to run fstrim, you do not want discard and nodiratime is redundant as noatime includes it.

There potentially are some other entries in system that may be tied to original drive. A full uninstall/reinstall of grub or changing default drive should be done.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 


 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Check these also:

 more /var/cache/debconf/config.dat  | grep /dev/disk
UUID in grub, fstab &
more /etc/initramfs-tools/conf.d/resume
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by TheFu on 2015-12-12
Can't add anything related to booting, but I do see HOME directory encryption.  In performance testing, that is the slowest method available with whole drive encryption via LUKS being the fastest.  There are pros/cons to each method, the main CON against HOME directory encryption is that system backup tools only see the encrypted data, unless the userid is logged in.  That can be a plus for some situations.  LUKS whole disk encryption will be faster and increase total system security, but if you need to reboot unattended, that normally won't work, since all partitions except /boot/ will be encrypted until a person enters the passphrase or pushes a button on a smartCARD/Yubikey to provide it.

How you move the data over doesn't really matter to Linux.  tar, rsync, fsarchiver, DejaDup, rdiff-backup, whatever, doesn't matter, provided there is a Linux partition (or LVM LV) with a Linux file system to receive the data, then that partition (or LVM LV) is mounted via the fstab to the correct place.

GPT or MBR.  If you must dual-boot Windows, then let Windows decide, but Windows only supports GPT on UEFI boot, 64-bit, systems. Linux doesn't really care.  There are strong reasons to prefer GPT for all systems.  At the same time, there are strong reasons to prefer UEFI with SecureBoot too.  The Linux Foundation Workstation security recommendations include both UEFI and SecureBoot.  I do neither today (I'm so ashamed!), but most of my hardware doesn't support UEFI boot.  

Anyway, the first team has arrived and is providing excellent advice. I'll step away and see what I can learn from those nice folks.

BTW, any comments on the **system-info** script?  Pretty simple, right?  For this purpose today, it would have been nice if the /etc/fstab were included. Besides that, any complaints for a general purpose, simple, sysinfo tool?

---

### Post by Bucky Ball on 2015-12-13
@oldfred: Thanks a heap for the tips. Yes, I am having issues booting the install, although when it boots the install itself is fine. I've got output from your commands, but rather than crashing the OP's thread, I'll post them on [the thread where I've been trying to nut this out]("http://ubuntuforums.org/showthread.php?t=2306013&page=2&p=13405760&viewfull=1#post13405760") and perhaps you can take a look.

As my SSD is in a hard drive bay which fits into the former optical drive bay on my laptop I have some strange issues.

I just dropped in here to pass on the method I'd used for the migration which, apart from not being able to boot it directly from the grub on sda, was easy, works faultlessly (when I eventually get there) and is identical to the HDD install. :)

---

### Post by koma77 on 2015-12-13
Thank you all!

If I were to install Ubuntu fresh to an SSD and just copy my /home and settings, is there any way to see which software that has been added on top of the default set of software?
A list of packages from apt-get or so would be great in this case...

---

### Post by Bucky Ball on 2015-12-13
Here's some stuff I've cobbled together while doing the pre-migrate research. I was going to clean install on the SSD and then add the packages from my HDD  install because I couldn't get the preferred outcome working, an identical copy booting on the SSD. 

Now I've almost got an identical copy working using the rsync method I linked to previously so I didn't end up using the methods below.
_____

1/ In the install you want to copy software from, run this and it will create a file in your /home directory:

```
    sudo dpkg &#8211;get-selections > installedsoftware
```

Copy that to the /home directory of the new install, open a terminal, navigate to /home and run:

```
    sudo dpkg &#8211;set-selections < installedsoftware
```
_____

Unsure of the differences between 1 and 2, but here's another way I found. 

2/ Create a backup of what packages are currently installed:

```
dpkg --get-selections > list.txt
```

On the new install:

```
dpkg --clear-selections
sudo dpkg --set-selections < list.txt

```

To get rid of stale packages

```
sudo apt-get autoremove
```

To get back to previous state (I think) (i.e. to install packages set by dpkg --set-selections)

```
sudo apt-get dselect-upgrade
```
_____

Both make a file which lists installed software. Double click it and have a read. The list.txt version supplies a list of everything that's been installed by apt I think. 

Hope that helps. Can't find links at mo but original guides shouldn't be hard to find.

---

### Post by TheFu on 2015-12-13
The dpkg --get-selections/dpkg --set-selections/apt-get dselect-upgrade method definitely works.  Been using it as part of our backup recovery methods for over 5 yrs.  Saves having to backup 2-4G for every server (plus all the file versioning).  OTOH, at 3am, restoring a bit-for-bit mirror is much easier, but creating a bit-for-bit backup requires downtime, which is unacceptable.

Using the rsync method is fine, provided the last run happens using alternate boot media. It is fine to mirror files from a running system, since that first sync could take hours, but to prevent any open-file-corruption, the last rsync needs to happen from a completely unused file system.  Not really an issue for data partitions, but for the OS partitions like /var, if you want that data moved over (and you should), don't risk having a corrupt file. Boot off any other Linux and perform the last rsync.

There are sector alignment issues between 512b and 4K sector disks. Seems like this wouldn't be an issue anymore, but it still is. 4K disks still lie about their true nature. On spinning disks any slight misalignment can mean 30+% performance is lost. Don't know what happens, if anything, on SSDs. Their raw speed probably makes it a non-issue.

The other thing that comes to mind is to remove the old disk and connect the new SSD to the same SATA port. Best to avoid the hd0 vs hd1 issues completely with grub and some BIOSes don't seem to want to boot off every SATA connector.  After everything is working on the new SSD, consider adding back any extra disks.

---

### Post by Bucky Ball on 2015-12-13
> **TheFu said:**
> The other thing that comes to mind is to remove the old disk and connect the new SSD to the same SATA port. _Best to avoid the hd0 vs hd1 issues_ completely with grub and _some BIOSes don't seem to want to boot off every SATA connector._

+1 to this. Trying to fix this is the nightmare I have been living for the last couple of days. If you can swap them over after rsync, do it. :)

---

### Post by oldfred on 2015-12-13
I do know they changed to the 4K alignment because of both new 4K drives and SSD. I think even the SSD is a lot slower as two sectors get involved, maybe only major issue with smaller files.

To OP, then if old drive first sector starts at sector 63, not 2048 you need to do new partitioning & a new install.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[URL="http://ubuntuforums.org/showthread.php?t=1685666"]http://ubuntuforums.org/showthread.php?t=1685666


[/URL]

---

### Post by ubfan1 on 2015-12-13
The other part of the problem, the Windows copy to SSD I didn't see mentioned above (but might have missed it).  I did use the latest Macrium Reflect (free as in beer) to copy a Win 8.1 hard disk to SSD, just copying the EFI and Windows partition successfully.  Used an external USB3 for the new SSD, first tried to let Macrium make the new partitions but it failed in some way, but when I made the partitions, the copy worked, and the new SSD booted just fine and was accepted by Microsoft for the Win10 upgrade.

---

