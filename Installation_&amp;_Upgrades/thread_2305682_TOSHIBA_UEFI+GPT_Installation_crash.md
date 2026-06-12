---
title: "TOSHIBA UEFI+GPT Installation crash"
date: 2015-12-08
forum: Installation &amp; Upgrades
---

### Post by patryk8 on 2015-12-08
[COLOR=#000000]I wrote the same theard in General help.

 In the beginning, I want to apologize for my bad english [/COLOR]:smile:
[COLOR=#000000]Ubuntu[14.04.3 - 14.10 - 15.04 - 15.10][/COLOR]
[COLOR=#000000]I have problem with installation Ubuntu on my new laptop as dual boot with Windows 10, i will try to explain every step which I did.[/COLOR]
[COLOR=#000000]I bought new laptop Toshiba Satellite L50D-B-151 PSKULE, which have a UEFI firmware and GPT Partition Table. I upgraded system to Windows 10. When i want to install Ubuntu system via USB drive, I created a Ubuntu USB drive, i shrink my C drive, i turn off FAST START option in Windows and Boot Security in UEFI. [/COLOR]
[COLOR=#000000]I boot my pendrive as UEFI, firstly i tried to install Ubuntu 14.04, but when i was on step "Installation type" i choose something else and here problem started. Ubuntu installer (GParted) doesn't see my partitions, just see my disc 1TB as free space. So next what i did it was research for a solutions.[/COLOR]
[COLOR=#000000]I found a few topics but anyone helped. [/COLOR]
[COLOR=#000000]I tried 'sudo gdisk -l /dev/sda' but my disk for sure has GTP Partition Table, and everything was ok. I tried to create partitions EXT3 via AOMEI Partition Assistant, but it still doesn't worked. [/COLOR]
[COLOR=#000000]Next I was trying to install Ubuntu 14.10, 15.04 and 15.10. In this versions, after running GParted I can see every partitions what i have. But when I tried to install Ubuntu and when i Click 'Next' button on third step 'Preparing to install Ubuntu' installation couldn't go to Installation Type, and error have shown as: "?? ????" - Yes there are question marks [/COLOR]:mad:
[COLOR=#000000]Installation stopped after shown error, and I can't start installation, it happened on 14.10, 15.04, 15.10 and i can check my partitions just in Gparted. But when i tried install 14.04, Gparted shown me nothing... just free space 1TB, but on 14.04 i could go to next step and select 'Something else' on instalation type, in contrast to 14.10, 15.04, 15.10, where before this step installation shown me error and it stopped.[/COLOR]
[COLOR=#000000]--[/COLOR]
[COLOR=#000000]ProblemType: Crash[/COLOR]


[COLOR=#000000]Architecture: amd64[/COLOR]


[COLOR=#000000]Date: Sat Dec 5 14:51:11 2015[/COLOR]


[COLOR=#000000]DistroRelease: Ubuntu 15.10[/COLOR]


[COLOR=#000000]ExecutablePath: /bin/parted_server[/COLOR]


[COLOR=#000000]ExecutableTimestamp: 1445362669[/COLOR]


[COLOR=#000000]ProcCmdline: parted_server[/COLOR]


[COLOR=#000000]ProcCwd: /root[/COLOR]
[COLOR=#000000]ProcEnviron:[/COLOR]
[COLOR=#000000]LC_COLLATE=C[/COLOR]
[COLOR=#000000]PATH=(custom, no user)[/COLOR]
[COLOR=#000000]LANG=en_US.UTF-8[/COLOR]
[COLOR=#000000]SHELL=/bin/bash[/COLOR]
[COLOR=#000000]-- [/COLOR]

---

### Post by oldfred on 2015-12-08
Better to use gparted from live installer to create partitions in advance and use ext4 for / & /home.
Did you verify that your download of the 64 bit 15.10 was correct with md5sum?
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

 
Post this from terminal in live installer:
 sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda

Is Windows fast start up or always on hibernation off?

You can review details of many instructions in link in my signature, but not sure what may apply, yet.

Other Toshiba issues, but they were after install & needed files in the install's ESP moved/copied to work.
 Toshiba L50-A-1EH laptop - used bcd edit
[http://ubuntuforums.org/showthread.php?t=2295628](http://ubuntuforums.org/showthread.php?t=2295628)
Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)

---

### Post by grahammechanical on 2015-12-08
> [COLOR=#000000]I wrote the same theard in General help.[/COLOR]

Please do not post the same problem more than once. 

[http://ubuntuforums.org/showthread.php?t=2305380](http://ubuntuforums.org/showthread.php?t=2305380)

Have you read and followed this advice? Although Windows 10 is not mentioned, it does also apply to Windows 10

> [h=2]Case when Ubuntu must be installed in UEFI mode[/h] Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]



[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Oh, by the way, Ubuntu 14.10 has reached end of life and Ubuntu 15.04  will reach end of life at the end of January 2016. So, do not try with  either of those versions.

Regards

---

### Post by patryk8 on 2015-12-08
Thank You for response.
Yes, md5sum is correct, i tried 14.10, 15.4 and 15.10, and in all of them i have crash 'server_parted'.

Windows start up is off. I boot every times my pendrive with ubuntu in UEFI mode

> **oldfred said:**
> 
 sudo parted /dev/sda unit s print

```
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start        End          Size        File system  Name                  Flags
 1      2048s        2099199s     2097152s    ntfs         Basic data partition  hidden, diag
 2      2099200s     2303999s     204800s     fat32        Basic data partition  boot, esp
 3      2304000s     2566143s     262144s     ntfs         Basic data partition  msftres
 4      2566144s     967346175s   964780032s  ntfs         Basic data partition  msftdata
 5      967346176s   1386776575s  419430400s  ntfs         Basic data partition  msftdata
 6      1929822208s  1930743807s  921600s     ntfs                               hidden, diag
 7      1930743808s  1953525164s  22781357s   ntfs         Basic data partition  hidden, diag

```> **oldfred said:**
> 
sudo gdisk -l /dev/sda

```
GPT fdisk (gdisk) version 1.0.0

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.


Warning! Secondary partition table overlaps the last partition by
30 blocks!
Try reducing the partition table size by 120 entries.
(Use the 's' item on the experts' menu.)
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9C5FEF40-3B4E-11E4-9F83-F7C615DF01B9
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 543047646 sectors (258.9 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         2099199   1024.0 MiB  2700  Basic data partition
   2         2099200         2303999   100.0 MiB   EF00  Basic data partition
   3         2304000         2566143   128.0 MiB   0C01  Basic data partition
   4         2566144       967346175   460.0 GiB   0700  Basic data partition
   5       967346176      1386776575   200.0 GiB   0700  Basic data partition
   6      1929822208      1930743807   450.0 MiB   2700  
   7      1930743808      1953525164   10.9 GiB    2700  Basic data partition



```

---

### Post by oldfred on 2015-12-08
I think gdisk may have identified the issue of overlap.
You should be able to just delete & recreate the last partition slightly - 20 sectors smaller.
Backup partition table as shown in links on gdisk repair and backup all your data particularly in last partition.

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)
Check start & end, delete and recreate without overlap. Backup vital just in case.

Then use Windows own tools to shrink Windows, turn off secure boot, turn off fast startup in Windows, turn off fast boot (if you have it) in UEFI. Reboot Windows and make sure it has run chkdsk.

---

### Post by patryk8 on 2015-12-09
Thank You, IT WORK!

---

### Post by oldfred on 2015-12-09
Glad that worked.
You can change status to solved.

---

