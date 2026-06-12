---
title: "No options for &quot;How do you want to install Ubuntu Studio?&quot;"
date: 2024-11-14
forum: Installation &amp; Upgrades
---

### Post by adraskoy on 2024-11-14
Installing 24.04 LTS on a Lenovo ThinkPad T14 Gen 3 with Ryzen 7. Initially my disk had Windows and plain Ubuntu on it. Tried removing the linux partitions with cfdisk, and then finally all of them and running wipefs -a on it for good measure. Same thing each time: "How do you want to install Ubuntu Studio?" with no options.

Anyone know what the installer is actually trying to do here?

---

### Post by adraskoy on 2024-11-14
I found this in /var/log/installer/ubuntu_bootstrap.log:
 
```
[FONT=monospace][COLOR=#000000]2024-11-15 00:31:24.513239 DEBUG subiquity_client: ==> getStorageV2() {"status": "FAILED", "error_report": {"state": "DONE", "base": "173163051[/COLOR]6.435717583.disk_probe_fail", "kind": "DISK_PROBE_FAIL", "seen": false, "oops_id": null}, "disks": [], "need_root": null, "need_boot": null, "install_minimum_size": null} 
2024-11-15 00:31:24.513333 DEBUG storage: Update storage: StorageResponseV2(status: ProbeStatus.FAILED, errorReport: ErrorReportRef(state: ErrorReportState.DONE, base: 1731630516.435717583.disk_probe_fail, kind: ErrorReportKind.DISK_PROBE_FAIL, seen: false, oopsId: null), disks: [], needRoot: null, needBoot: null, installMinimumSize: null) 
2024-11-15 00:31:24.513416 DEBUG subiquity_client: GET [http://localhost/storage/v2?wait=true](http://localhost/storage/v2?wait=true) 
2024-11-15 00:31:24.514048 DEBUG subiquity_client: ==> getStorageV2() {"status": "FAILED", "error_report": {"state": "DONE", "base": "1731630516.435717583.disk_probe_fail", "kind": "DISK_PROBE_FAIL", "seen": false, "oops_id": null}, "disks": [], "need_root": null, "need_boot": null, "install_minimum_size": null} 
2024-11-15 00:31:24.514109 DEBUG storage: Update storage: StorageResponseV2(status: ProbeStatus.FAILED, errorReport: ErrorReportRef(state: ErrorReportState.DONE, base: 1731630516.435717583.disk_probe_fail, kind: ErrorReportKind.DISK_PROBE_FAIL, seen: false, oopsId: null), disks: [], ne
edRoot: null, needBoot: null, installMinimumSize: null) 
2024-11-15 00:31:24.514135 DEBUG subiquity_client: GET [http://localhost/storage/v2/guided?wait=true](http://localhost/storage/v2/guided?wait=true) 
2024-11-15 00:31:24.514727 DEBUG subiquity_client: ==> getGuidedStorageV2(true) {"status": "FAILED", "error_report": {"state": "DONE", "base": 
"1731630516.435717583.disk_probe_fail", "kind": "DISK_PROBE_FAIL", "seen": false, "oops_id": null}, "configured": null, "targets": []} 
2024-11-15 00:31:24.514780 DEBUG storage: select guided capability: null
[/FONT]
```
[FONT=monospace]This disk is at [/FONT][FONT=monospace][COLOR=#000000]/dev/nvme0n1

[/COLOR][/FONT][FONT=monospace][COLOR=#000000]lsblk -a |grep disk [/COLOR]
sda       8:0    1  14.4G  0 [COLOR=#ff5454]**disk**[/COLOR][COLOR=#000000]  [/COLOR]
nvme0n1 259:0    0 476.9G  0 [COLOR=#ff5454]**disk**[/COLOR][COLOR=#000000] [/COLOR]

[/FONT]

[FONT=monospace] 

[/FONT]

---

### Post by Rubi1200 on 2024-11-15
Just a wild guess here but I think you probably need to boot into a live session, use GParted to create a new **gpt **partition table, and then start the installer again.

If still no luck then please post the output for *parted -l*

---

### Post by adraskoy on 2024-11-15
Thanks. I tried that  - didn't work. I then added some partitions and tried again, but still no. Here's the output from parted -l

```
[FONT=monospace][COLOR=#000000]root@ubuntu-studio:/home/ubuntu-studio# parted -l [/COLOR]
Model: Kingston DataTraveler 3.0 (scsi) 
Disk /dev/sda: 15.5GB 
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 
Disk Flags:  

Number  Start   End     Size    Type     File system  Flags 
 1      4129kB  15.5GB  15.5GB  primary               lba 


Model: WD PC SN740 SDDQNQD-512G-1201 (nvme) 
Disk /dev/nvme0n1: 512GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name  Flags 
 1      1049kB  53.5MB  52.4MB  fat32        EFI   boot, esp 
 2      53.5MB  68.8GB  68.7GB               ROOT 
 3      68.8GB  512GB   443GB                HOME 




[/FONT]
```

---

### Post by adraskoy on 2024-11-15
I gave up and reinstalled regular ubuntu and then got and ran the ubuntustudio-installer. I like gnome better anyway, but will miss the categorised menu of all the Ubuntu Studio features.

---

