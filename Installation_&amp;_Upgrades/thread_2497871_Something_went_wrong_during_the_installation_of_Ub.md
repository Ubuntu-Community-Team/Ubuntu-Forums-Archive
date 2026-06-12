---
title: "Something went wrong during the installation of Ubuntu 24.04"
date: 2024-05-21
forum: Installation &amp; Upgrades
---

### Post by semedilino073 on 2024-05-21
Hello, I’m really new to Ubuntu. I was trying to install the version 24.04 desktop and I got the message “Something went wrong during the installation”. I had the installation file on a 16 GB flash drive and I would to install it on a 2TB separated disk. 
What can I do?

---

### Post by tea for one on 2024-05-21
Power off the PC
Boot your installation flash drive into a "Try Ubuntu" live session
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Hopefully, the response is UEFI
Next, enter this (so that we can see your disk structure)
```
sudo parted -l
```
In your reply, please use code tags to legibly display the terminal output.
(Code tags accessible via Adv Reply > # icon > Wrap [CODE] tags round selected text)

---

### Post by semedilino073 on 2024-05-21
The first response is UEFI
Here's the second response:
```
Error: /dev/sda: unrecognised disk label
Model: WD P40 Game Drive (scsi)                                           
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: Generic Flash Disk (scsi)
Disk /dev/sdc: 31.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      32.8kB  6109MB  6109MB               ISO9660    hidden, msftdata
 2      6109MB  6114MB  5192kB               Appended2  boot, esp
 3      6114MB  6115MB  307kB                Gap1       hidden, msftdata
 4      6115MB  31.5GB  25.3GB  ext4


Model: APPLE SSD AP0256N (nvme)
Disk /dev/nvme0n1: 251GB
Sector size (logical/physical): 4096B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      24.6kB  315MB  315MB  fat32        EFI System Partition  boot, esp
 2      315MB   251GB  251GB

```

---

### Post by tea for one on 2024-05-21
```
Error: /dev/sda: unrecognised disk label
Model: WD P40 Game Drive (scsi)                                           
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 
```
Is this your target disk?
You need to create a partition table so that it is visible to the Ubuntu installer.
In a live session, open Gparted > Device > Create Partition Table > Select GPT
Then, I would expect the installer to find it.

By the way, it is a good idea to remove/isolate other disks to avoid errors.
Only the installer USB and target disk should be active.

---

### Post by semedilino073 on 2024-05-21
Unfortunately, I still get this log:
```
May 21 20:53:59 ubuntu subiquity_log.3817[7237]:         Exit code: 1
May 21 20:53:59 ubuntu subiquity_log.3817[7237]:         Reason: -
May 21 20:53:59 ubuntu subiquity_log.3817[7237]:         Stdout: ''
May 21 20:53:59 ubuntu subiquity_log.3817[7237]:         Stderr: ''
May 21 20:53:59 ubuntu subiquity_log.3817[7237]:         
May 21 20:53:59 ubuntu subiquity_log.3817[7237]: Stderr: ''
May 21 20:53:59 ubuntu subiquity_event.3817[3817]:  executing curtin install partitioning step
May 21 20:53:59 ubuntu subiquity_event.3817[3817]: installing system
May 21 20:53:59 ubuntu subiquity_event.3817[3817]: 
May 21 20:53:59 ubuntu subiquity_event.3817[3817]:   curtin command install
```

---

### Post by tea for one on 2024-05-21
Not making much progress yet, but never mind, let's see where we are?
During the installation process, when do you see "Something went wrong" message?

Also, in a "Try Ubuntu" session, can you show the current output from:-
```
sudo parted -l
```

---

