---
title: "Ubuntu Doesn't Come Up"
date: 2020-02-08
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2020-02-08
My 10 year old desktop computer failed, so I obtained a refurbished Dell Optiplex 9020, installed Ubuntu 19.10 in parallel with Windoze X. When I booted it up I was, of course, informed that there were updates so I permitted the application of the updates and restarted the computer.  It did not restart.  I am sitting looking at a plain purple screen.  I looked at the debug kernel page but I do not see any of the relevant options in the grub script when I follow the instructions.  When I try to edit the grub menu the text is only displayed for a few second before the screen goes black, so I couldn't edit it even if I could see the options I am instructed to modify. Furthermore prior to applying the updates the system always booted to the grub menu because that is only reasonable to permit me to choose between Ubuntu 19.10 and Windoze X each time. After the upgrades I must hold down the right shift to see the grub menu. Could someone please direct me to current documentation of how to resolve this problem?

---

### Post by yancek on 2020-02-08
The official Ubuntu documentation on dual booting with windows 10 is at the link below.    I would suggest you read through it and compare the instructions to what you did.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by 7-webmaster on 2020-02-08
Thank you.  I cannot even get into the BIOS now.  I powered off the computer, unplugged it, plugged it back in and powered it up while pressing the key (F12) that previously worked to get me into the BIOS as I had to do to boot from the USB to install Ubuntu.  Again I remind you that dual boot worked UNTIL I restarted Ubuntu to apply post-installation fixes.  Now I have an expensive doorstop.  If I power the computer on with no key pressed it boots into Ubuntu and then sits in a perpetual loop displaying the logo and the five dots that change color between white and red.  If I power the computer on while holding down F12 it goes to a black screen.  If I power the computer on with right shift held the red light on the USB stick blinks a few times, then the Ubuntu boot starts but it immediately goes to a plain purple screen.  The existing documentation on boot problems only mentions 18.04 and references removing lines that I did not see in the grub menu the few times I have got that far.  Even when I could see the grub menu it was only displayed for a few seconds, not long enough to edit.  Which is why I have been trying to boot from the USB stick.

---

### Post by 7-webmaster on 2020-02-08
I removed the USB stick and got into the BIOS Setup.  I rearranged the boot sequence to put USB first, where it should be anyways.  The BIOS was already set for Legacy rather than UEFI boot so I left that.  I then rebooted into the USB, so I can see the Windoze and the Ubuntu partitions on the disk.  But I am running the USB in trial mode.  How do I copy information out of the Ubuntu partition so I can attach it to a problem report?  I cannot open or copy the boot log because of bad permissions.

---

### Post by 7-webmaster on 2020-02-09
I would really appreciate instructions on how to collect the documentation to find out why I cannot boot Ubuntu on this system. I have gone back, reformatted the entire disk and installed Ubuntu as the only operating system.  When I reboot after installation the logo comes, the screen goes to blank purple, the light indicating disk activity flickers for a few minutes then everything stops.  I can see the contents of the file system when I boot from the installation USB but I do not know what to look for to find out why Ubuntu will not boot.

---

### Post by yancek on 2020-02-09
Boot Ubuntu from the install usb and if you have an internet connection, go to the link below and read through the page so you have a basic understanding.  The use the 2nd option described on that page to download the ppa with boot repair and run it as instructed.  Make certain that you do NOT try to make ANY repairs but select the option to Create BootInfo Summary.  When it finishes, you should get a pastebin link you can post here which will have details on your system and someone here should be able to make a recommendation.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 7-webmaster on 2020-02-09
I cannot install boot-repair because it has a seemingly endless list of dependencies.  I am sending this message from the USB installer so I can see everything on the system, but I do not know WHAT to report, and this interface does not permit me to attach large files like those in /var/log.  What I can see in those log files looks entirely normal, but I still see nothing but a blank purple screen.  Also note that I have tried and failed to follow the instructions on [https://wiki.ubuntu.com/DebuggingKernelBoot](https://wiki.ubuntu.com/DebuggingKernelBoot).  Holding right shift down does not display the grub menu, and I cannot edit the grub menu from the install USB.

---

### Post by 7-webmaster on 2020-02-10
Please. All I am asking is for assistance to debug why my system is not coming up.  Exactly what should I be looking for in the logs?  As far as I can see everything in the logs looks fine, but all I see is either the five dots blinking white and red or a plain purple screen.  I never see the Ubuntu 19.10 page from which I would get to the login.  I cannot see any relevant advice on the Wiki or elsewhere.

---

### Post by CelticWarrior on 2020-02-10
Boot Repair suggested above is to be installed to and run from a live session ("Try Ubuntu").

Also, when the splash screen seems stuck you can press ESC to see the last messages. This should give some clue about why it is stuck. Very likely an issue with the graphics mode.

---

### Post by 7-webmaster on 2020-02-11
I cannot install boot-repair

sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: [https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)
 More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Ign:1 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Hit:2 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease [97.5 kB]      
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease [255 kB]                 
Get:6 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan InRelease [15.4 kB]
Get:7 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan/main amd64 Packages [1,704 B]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main amd64 Packages [137 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease [97.5 kB]        
Get:10 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan/main Translation-en [1,576 B]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main amd64 Packages [969 kB]      
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main Translation-en [51.5 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main amd64 DEP-11 Metadata [204 B]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main DEP-11 48x48 Icons [29 B]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main DEP-11 64x64 Icons [29 B]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main amd64 c-n-f Metadata [1,940 B]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/restricted amd64 Packages [8,904 B]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/restricted Translation-en [1,516 B]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main amd64 DEP-11 Metadata [510 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main DEP-11 48x48 Icons [95.4 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main DEP-11 64x64 Icons [173 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main amd64 c-n-f Metadata [29.7 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main amd64 Packages [204 kB]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main Translation-en [77.5 kB]
Get:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main amd64 DEP-11 Metadata [73.0 kB]
Get:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main DEP-11 48x48 Icons [9,948 B]
Get:27 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main DEP-11 64x64 Icons [15.1 kB]
Get:28 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main amd64 c-n-f Metadata [2,932 B]
Get:29 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/restricted amd64 Packages [8,904 B]
Get:30 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/restricted Translation-en [1,516 B]
Fetched 2,840 kB in 2s (1,339 kB/s)                      
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Hit:2 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease                          
Hit:6 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan InRelease
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease
Reading package lists... Done

ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install -y boot-save
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-save
ubuntu@ubuntu:~$ sudo apt-get install -y boot-sav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-sav : Depends: glade2script (>= 3) but it is not going to be installed or
                     glade2script-gtk2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install -y glade2script-gtk2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 glade2script-gtk2 : Depends: python but it is not installable
                     Depends: python-gtk2 but it is not installable
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python' has no installation candidate
ubuntu@ubuntu:~$ sudo apt-get install python-gtk2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-gtk2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-gtk2' has no installation candidate
ubuntu@ubuntu:~$

python --version

Command 'python' not found, but can be installed with:

sudo apt install python3

You also have python3 installed, you can run 'python3' instead.

ubuntu@ubuntu:~$ sudo apt install python3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3 is already the newest version (3.7.5-1).
python3 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 252 not upgraded.



If python is already installed why is the installation of boot-repair not finding it?

---

### Post by 7-webmaster on 2020-02-13
Boot repair is obviously fundamentally screwed on 19.10.  Furthermore initialization is getting as far as the graphical screen which exists solely to substitute for the console output from the Linux startup. So I do not believe that there is anything wrong with the boot that boot-repair will find.  The problem is clearly in Ubuntu 19.10, not the boot.  I am not expecting anyone in this forum to tell me what the problem is.  I just want somebody to tell me what to look for in the logs created by Ubuntu 19.10 startup thatwill permit ME to figure out what is wrong.

HELP!

---

### Post by 7-webmaster on 2020-02-14
All I am looking for on this thread is advice on how to determine why Ubuntu 19.10 does not complete initialization on my system.  I am firmly of the belief that the actual boot is completing, and therefore boot-repair will not find anything to fix.  I was willing to install boot-repair and follow the advice but boot-repair will not install on this system without heroic effort which I will not do.  The problem is that Ubuntu 19.10 boots from the SSD but then never gets around to displaying the 19.10 logo page from which I could get to the login.  It is perpetually displaying the page with the five blinking dots that remind me of the main display on ST:TOS.  I am running the hardware at present from the Ubuntu 19-10 install USB and everything is working fine.  I am posting this from the system.  I can see the contents of /var/logs but I do not have permission to access some of the files, in particular boot.log.

I am looking for advice on how to figure out why Ubuntu is not reaching the point where I can log in to the system.  

The last portion of syslog from the startup is:

Feb  9 19:04:43 jcobban-OptiPlex-9020 NetworkManager[607]: <info>  [1581293083.0470] dhcp6 (eno1): activation: beginning transaction (timeout in 45 seconds)
Feb  9 19:04:43 jcobban-OptiPlex-9020 set-cpufreq[593]: Setting powersave scheduler for all CPUs
Feb  9 19:04:43 jcobban-OptiPlex-9020 systemd[1]: ondemand.service: Succeeded.
Feb  9 19:04:49 jcobban-OptiPlex-9020 systemd[1]: dmesg.service: Succeeded.
Feb  9 19:04:49 jcobban-OptiPlex-9020 systemd-resolved[521]: Using degraded feature set (UDP) for DNS server 192.168.1.1.
Feb  9 19:04:50 jcobban-OptiPlex-9020 systemd[1]: NetworkManager-dispatcher.service: Succeeded.
Feb  9 19:05:08 jcobban-OptiPlex-9020 systemd-timesyncd[520]: Synchronized to time server for the first time 91.189.94.4:123 (ntp.ubuntu.com).
Feb  9 19:05:12 jcobban-OptiPlex-9020 systemd[1]: fprintd.service: Succeeded.
Feb  9 19:05:12 jcobban-OptiPlex-9020 systemd[1]: systemd-hostnamed.service: Succeeded.
Feb  9 19:05:12 jcobban-OptiPlex-9020 systemd[1]: systemd-localed.service: Succeeded.
Feb  9 19:05:28 jcobban-OptiPlex-9020 NetworkManager[607]: <warn>  [1581293128.3545] dhcp6 (eno1): request timed out
Feb  9 19:05:28 jcobban-OptiPlex-9020 NetworkManager[607]: <info>  [1581293128.3546] dhcp6 (eno1): state changed unknown -> timeout
Feb  9 19:05:28 jcobban-OptiPlex-9020 NetworkManager[607]: <info>  [1581293128.3547] dhcp6 (eno1): canceled DHCP transaction
Feb  9 19:05:28 jcobban-OptiPlex-9020 NetworkManager[607]: <info>  [1581293128.3547] dhcp6 (eno1): state changed timeout -> done
Feb  9 19:05:42 jcobban-OptiPlex-9020 geoclue[1065]: Service not used for 60 seconds. Shutting down..
Feb  9 19:05:42 jcobban-OptiPlex-9020 systemd[1]: geoclue.service: Main process exited, code=killed, status=15/TERM
Feb  9 19:05:42 jcobban-OptiPlex-9020 systemd[1]: geoclue.service: Succeeded.
Feb  9 19:06:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Session is stable (running for >2 minutes).
Feb  9 19:09:47 jcobban-OptiPlex-9020 PackageKit: daemon quit
Feb  9 19:09:47 jcobban-OptiPlex-9020 systemd[1]: packagekit.service: Main process exited, code=killed, status=15/TERM
Feb  9 19:09:47 jcobban-OptiPlex-9020 systemd[1]: packagekit.service: Succeeded.
Feb  9 19:09:51 jcobban-OptiPlex-9020 gnome-shell[1015]: Failed to DPMS: Failed to set connector 67 property 2: Permission denied
Feb  9 19:17:01 jcobban-OptiPlex-9020 CRON[1325]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  9 19:19:35 jcobban-OptiPlex-9020 systemd[1]: Starting Cleanup of Temporary Directories...
Feb  9 19:19:35 jcobban-OptiPlex-9020 systemd-tmpfiles[1330]: [/usr/lib/tmpfiles.d/speech-dispatcher.conf:1] Line references path below legacy directory /var/run/, updating /var/run/speech-dispatcher &#8594; /run/speech-dispatcher; please update the tmpfiles.d/ drop-in file accordingly.
Feb  9 19:19:35 jcobban-OptiPlex-9020 systemd-tmpfiles[1330]: [/usr/lib/tmpfiles.d/speech-dispatcher.conf:2] Line references path below legacy directory /var/run/, updating /var/run/speech-dispatcher/.cache &#8594; /run/speech-dispatcher/.cache; please update the tmpfiles.d/ drop-in file accordingly.
Feb  9 19:19:35 jcobban-OptiPlex-9020 systemd-tmpfiles[1330]: [/usr/lib/tmpfiles.d/speech-dispatcher.conf:3] Line references path below legacy directory /var/run/, updating /var/run/speech-dispatcher/.speech-dispatcher &#8594; /run/speech-dispatcher/.speech-dispatcher; please update the tmpfiles.d/ drop-in file accordingly.
Feb  9 19:19:35 jcobban-OptiPlex-9020 systemd-tmpfiles[1330]: [/usr/lib/tmpfiles.d/speech-dispatcher.conf:4] Line references path below legacy directory /var/run/, updating /var/run/speech-dispatcher/.cache/speech-dispatcher &#8594; /run/speech-dispatcher/.cache/speech-dispatcher; please update the tmpfiles.d/ drop-in file accordingly.
Feb  9 19:19:35 jcobban-OptiPlex-9020 systemd-tmpfiles[1330]: [/usr/lib/tmpfiles.d/speech-dispatcher.conf:5] Line references path below legacy directory /var/run/, updating /var/run/speech-dispatcher/log &#8594; /run/speech-dispatcher/log; please update the tmpfiles.d/ drop-in file accordingly.
Feb  9 19:19:35 jcobban-OptiPlex-9020 systemd[1]: systemd-tmpfiles-clean.service: Succeeded.
Feb  9 19:19:35 jcobban-OptiPlex-9020 systemd[1]: Started Cleanup of Temporary Directories.
Feb  9 19:19:40 jcobban-OptiPlex-9020 systemd-resolved[521]: Grace period over, resuming full feature set (UDP+EDNS0) for DNS server 192.168.1.1.
Feb  9 19:23:10 jcobban-OptiPlex-9020 systemd-resolved[521]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Feb  9 19:30:01 jcobban-OptiPlex-9020 CRON[1362]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)



The system is a reconditioned Dell Optiplex 9020.  The boot mode is currently set to BIOS and the boot order to USB first.

Processor Intel(R) Core(TM) i5-4590 CPU @ 3.30GHz

cat /proc/meminfo
MemTotal:       16301872 kB
MemFree:        11210548 kB
MemAvailable:   13929716 kB
Buffers:          777092 kB
Cached:          2983748 kB
SwapCached:            0 kB
Active:          2738280 kB
Inactive:        1677652 kB
Active(anon):    1053804 kB
Inactive(anon):   499076 kB
Active(file):    1684476 kB
Inactive(file):  1178576 kB
Unevictable:      283972 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        939068 kB
Mapped:           373820 kB
Shmem:            897800 kB
KReclaimable:     192100 kB
Slab:             284616 kB
SReclaimable:     192100 kB
SUnreclaim:        92516 kB
KernelStack:        9680 kB
PageTables:        15164 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     8150936 kB
Committed_AS:    4944568 kB
VmallocTotal:   34359738367 kB
VmallocUsed:       59232 kB
VmallocChunk:          0 kB
Percpu:             3376 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
Hugetlb:               0 kB
DirectMap4k:      204816 kB
DirectMap2M:     7038976 kB
DirectMap1G:    10485760 kB





the output of lspci is:

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (r
ev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Cor
e Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor H
D Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family US
B xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset
 Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 8 Series/C220 Series Chipset Family
 KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 
04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family US
B EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Defini
tion Audio Controller (rev 04)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family US
B EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Q87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6
-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Contr
oller (rev 04)

---

### Post by 7-webmaster on 2020-02-15
Please. I do not know what documentation I need to gather to determine why I cannot run Ubuntu 19.10 from the SSD of my computer when it runs from the USB.  I just need advice.

---

### Post by 7-webmaster on 2020-02-15
Here is a longer chunk of the syslog:

Feb  9 19:04:41 jcobban-OptiPlex-9020 systemd[886]: Started GNOME RFKill handling.
Feb  9 19:04:41 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME RFKill handling.
Feb  9 19:04:41 jcobban-OptiPlex-9020 systemd[886]: Started GNOME Sound sample caching handling.
Feb  9 19:04:41 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Sound sample caching handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Started GNOME Smartcard handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Smartcard handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Started GNOME WWan management.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME WWan management.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Started GNOME Printer notifications.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Printer notifications.
Feb  9 19:04:42 jcobban-OptiPlex-9020 gnome-session-binary[1004]: Entering running state
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Started GNOME Accessibility settings.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Accessibility settings.
Feb  9 19:04:42 jcobban-OptiPlex-9020 xbrlapi.desktop[1187]: openConnection: connect: No such file or directory
Feb  9 19:04:42 jcobban-OptiPlex-9020 xbrlapi.desktop[1187]: cannot connect to braille devices daemon brltty at :0
Feb  9 19:04:42 jcobban-OptiPlex-9020 gnome-shell[1015]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Started GNOME XSettings.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME XSettings.
Feb  9 19:04:42 jcobban-OptiPlex-9020 gnome-shell[1015]: JS WARNING: [resource:///org/gnome/shell/ui/windowManager.js 1640]: reference to undefined property "MetaWindowXwayland"
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Started GNOME Color management.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Color management.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Started GNOME Media keys handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Media keys handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 dbus-daemon[597]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service' requested by ':1.116' (uid=124 pid=1128 comm="/usr/lib/gnome-settings-daemon/gsd-color " label="unconfined")
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[1]: Starting Manage, Install and Generate Color Profiles...
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Started GNOME Power management handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Power management handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 gsd-media-keys[1124]: Unable to inhibit keypresses: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Permission denied
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Started GNOME Keyboard handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Keyboard handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 gsd-media-keys[1124]: Failed to grab accelerator for keybinding settings:playback-random
Feb  9 19:04:42 jcobban-OptiPlex-9020 gsd-media-keys[1124]: Failed to grab accelerator for keybinding settings:rfkill
Feb  9 19:04:42 jcobban-OptiPlex-9020 gsd-media-keys[1124]: Failed to grab accelerator for keybinding settings:playback-repeat
Feb  9 19:04:42 jcobban-OptiPlex-9020 gsd-media-keys[1124]: Failed to grab accelerator for keybinding settings:screen-brightness-cycle
Feb  9 19:04:42 jcobban-OptiPlex-9020 gsd-media-keys[1124]: Failed to grab accelerator for keybinding settings:hibernate
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Started GNOME Wacom handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Wacom handling.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Session.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target Current graphical user session.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Wayland Session (session: gnome-login).
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Condition check resulted in GNOME Welcome Tour being skipped.
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[886]: Startup finished in 2.258s.
Feb  9 19:04:42 jcobban-OptiPlex-9020 gnome-shell[1015]: Failed to DPMS: Failed to set connector 67 property 2: Permission denied
Feb  9 19:04:42 jcobban-OptiPlex-9020 dbus-daemon[597]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Feb  9 19:04:42 jcobban-OptiPlex-9020 systemd[1]: Started Manage, Install and Generate Color Profiles.
Feb  9 19:04:42 jcobban-OptiPlex-9020 gsd-color[1128]: failed to create device: failed to obtain org.freedesktop.color-manager.create-device auth
Feb  9 19:04:42 jcobban-OptiPlex-9020 gsd-color[1128]: failed to create device: failed to obtain org.freedesktop.color-manager.create-device auth
Feb  9 19:04:42 jcobban-OptiPlex-9020 gnome-shell[1015]: Registering session with GDM
Feb  9 19:04:42 jcobban-OptiPlex-9020 whoopsie[901]: [19:04:42] online
Feb  9 19:04:43 jcobban-OptiPlex-9020 systemd[1]: systemd-rfkill.service: Succeeded.
Feb  9 19:04:43 jcobban-OptiPlex-9020 NetworkManager[607]: <info>  [1581293083.0470] dhcp6 (eno1): activation: beginning transaction (timeout in 45 seconds)
Feb  9 19:04:43 jcobban-OptiPlex-9020 set-cpufreq[593]: Setting powersave scheduler for all CPUs
Feb  9 19:04:43 jcobban-OptiPlex-9020 systemd[1]: ondemand.service: Succeeded.
Feb  9 19:04:49 jcobban-OptiPlex-9020 systemd[1]: dmesg.service: Succeeded.
Feb  9 19:04:49 jcobban-OptiPlex-9020 systemd-resolved[521]: Using degraded feature set (UDP) for DNS server 192.168.1.1.
Feb  9 19:04:50 jcobban-OptiPlex-9020 systemd[1]: NetworkManager-dispatcher.service: Succeeded.
Feb  9 19:05:08 jcobban-OptiPlex-9020 systemd-timesyncd[520]: Synchronized to time server for the first time 91.189.94.4:123 (ntp.ubuntu.com).
Feb  9 19:05:12 jcobban-OptiPlex-9020 systemd[1]: fprintd.service: Succeeded.
Feb  9 19:05:12 jcobban-OptiPlex-9020 systemd[1]: systemd-hostnamed.service: Succeeded.
Feb  9 19:05:12 jcobban-OptiPlex-9020 systemd[1]: systemd-localed.service: Succeeded.
Feb  9 19:05:28 jcobban-OptiPlex-9020 NetworkManager[607]: <warn>  [1581293128.3545] dhcp6 (eno1): request timed out
Feb  9 19:05:28 jcobban-OptiPlex-9020 NetworkManager[607]: <info>  [1581293128.3546] dhcp6 (eno1): state changed unknown -> timeout
Feb  9 19:05:28 jcobban-OptiPlex-9020 NetworkManager[607]: <info>  [1581293128.3547] dhcp6 (eno1): canceled DHCP transaction
Feb  9 19:05:28 jcobban-OptiPlex-9020 NetworkManager[607]: <info>  [1581293128.3547] dhcp6 (eno1): state changed timeout -> done
Feb  9 19:05:42 jcobban-OptiPlex-9020 geoclue[1065]: Service not used for 60 seconds. Shutting down..
Feb  9 19:05:42 jcobban-OptiPlex-9020 systemd[1]: geoclue.service: Main process exited, code=killed, status=15/TERM
Feb  9 19:05:42 jcobban-OptiPlex-9020 systemd[1]: geoclue.service: Succeeded.
Feb  9 19:06:42 jcobban-OptiPlex-9020 systemd[886]: Reached target GNOME Session is stable (running for >2 minutes).
Feb  9 19:09:47 jcobban-OptiPlex-9020 PackageKit: daemon quit
Feb  9 19:09:47 jcobban-OptiPlex-9020 systemd[1]: packagekit.service: Main process exited, code=killed, status=15/TERM
Feb  9 19:09:47 jcobban-OptiPlex-9020 systemd[1]: packagekit.service: Succeeded.
Feb  9 19:09:51 jcobban-OptiPlex-9020 gnome-shell[1015]: Failed to DPMS: Failed to set connector 67 property 2: Permission denied

This may be related to [https://ubuntuforums.org/showthread.php?t=2432688](https://ubuntuforums.org/showthread.php?t=2432688) but I do not see an applicable resolution in that thread either.  Since I lack an intimate gnowledge of Gnome the error message is completely meaningless to me.  

PLEASE give me some advice as to how to get this system to run.

---

### Post by 7-webmaster on 2020-02-16
I have finally got boot-repair installed and its report is at [https://paste.ubuntu.com/p/jSkF7YcXW5/](https://paste.ubuntu.com/p/jSkF7YcXW5/)  I do not see anything obvious in this report that would suggest why GNOME does not complete initialization on this system.

---

### Post by 7-webmaster on 2020-02-17
Please!  There must be somebody out there who can explain why Gnome is not coming up on this system.

---

