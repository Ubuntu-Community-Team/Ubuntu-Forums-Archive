---
title: "grub-efi failed to update"
date: 2019-12-08
forum: Installation &amp; Upgrades
---

### Post by lvm on 2019-12-08
This just happened during the routine package update:

Setting up grub-efi-amd64-signed (1.93.15+2.02-2ubuntu8.14) ... 
Installing for x86_64-efi platform. 
Could not delete variable: Invalid argument 
grub-install: error: efibootmgr failed to register the boot entry: Block device required. 
dpkg: error processing package grub-efi-amd64-signed (--configure): 
installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1 
Errors were encountered while processing: 
grub-efi-amd64-signed 
E: Sub-process /usr/bin/dpkg returned an error code (1)

kubuntu 18.04 Boot devices (/dev/sda1 on /boot/efi and /dev/sda2 on /) are accessible. Even though the update has failed some files in /boot where changed e.g. /boot/efi/EFI/ubuntu/grubx64.efi, and now I am afraid to reboot. Should I restore /boot to the latest working backup before rebooting?

---

### Post by VMC on 2019-12-08
Was there anything else updated. I'm unclear what got updated.

---

### Post by oldfred on 2019-12-08
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I have multiple drives with multiple installs & experiment with names to see if I can directly boot another install directly with UEFI. But if I get too many entries in UEFI, my UEFI seems to lock up or cause issues. There was an old bug where some UEFI would only use half of UEFI available memory and lock so bad that you had to return system to vendor. Originally blamed on Linux, but Windows also could cause it.

---

### Post by lvm on 2019-12-08
> **VMC said:**
> Was there anything else updated. I'm unclear what got updated.
Here is the complete update history since the last reboot

```
Commandline: apt-get autoremove
Requested-By: lvm (1000)
Remove: linux-headers-5.0.0-27:amd64 (5.0.0-27.28~18.04.1), linux-modules-5.0.0-27-generic:amd64 (5.0.0-27.28~18.04.1), linux-image-5.0.0-27-generic:amd64 (5.0.0-27.28~18.04.1), linux-modules-extra-5.0.0-27-generic:amd64 (5.0.0-27.28~18.04.1), linux-headers-5.0.0-27-generic:amd64 (5.0.0-27.28~18.04.1)
End-Date: 2019-12-02  09:43:10

Start-Date: 2019-12-03  13:53:51
Commandline: apt-get upgrade
Requested-By: lvm (1000)
Upgrade: linux-libc-dev:amd64 (4.15.0-70.79, 4.15.0-72.81), libsqlite3-0:amd64 (3.22.0-1ubuntu0.1, 3.22.0-1ubuntu0.2), linux-signed-generic-hwe-18.04:amd64 (5.0.0.36.94, 5.0.0.37.95)
End-Date: 2019-12-03  13:54:00

Start-Date: 2019-12-05  10:03:15
Commandline: apt-get upgrade
Requested-By: lvm (1000)
Upgrade: intel-microcode:amd64 (3.20191115.1ubuntu0.18.04.1, 3.20191115.1ubuntu0.18.04.2)
End-Date: 2019-12-05  10:03:53

Start-Date: 2019-12-08  11:55:54
Commandline: apt-get upgrade
Requested-By: lvm (1000)
Upgrade: grub-common:amd64 (2.02-2ubuntu8.13, 2.02-2ubuntu8.14), squid-common:amd64 (3.5.27-1ubuntu1.3, 3.5.27-1ubuntu1.4), grub2-common:amd64 (2.02-2ubuntu8.13, 2.02-2ubuntu8.14), grub-pc:amd64 (2.02-2ubuntu8.13, 2.02-2ubuntu8.14), grub-pc-bin:amd64 (2.02-2ubuntu8.13, 2.02-2ubuntu8.14), grub-efi-amd64-bin:amd64 (2.02-2ubuntu8.13, 2.02-2ubuntu8.14), mkvtoolnix:amd64 (40.0.0-0~bunkus01, 41.0.0-0~bunkus01), grub-efi-amd64-signed:amd64 (1.93.14+2.02-2ubuntu8.13, 1.93.15+2.02-2ubuntu8.14), squid:amd64 (3.5.27-1ubuntu1.3, 3.5.27-1ubuntu1.4), unattended-upgrades:amd64 (1.1ubuntu1.18.04.12, 1.1ubuntu1.18.04.13), mkvtoolnix-gui:amd64 (40.0.0-0~bunkus01, 41.0.0-0~bunkus01)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2019-12-08  11:57:30
```


> **oldfred said:**
> May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I have multiple drives with multiple installs & experiment with names to see if I can directly boot another install directly with UEFI. But if I get too many entries in UEFI, my UEFI seems to lock up or cause issues. There was an old bug where some UEFI would only use half of UEFI available memory and lock so bad that you had to return system to vendor. Originally blamed on Linux, but Windows also could cause it.

This machine runs only ubuntu and I don't experiment on it at all - it was installed, and that's it, should be just one entry. As far as I understand, now the EFI boot is gone completely:

root@server:/var/log/apt# efibootmgr
BootCurrent: 0000
Timeout: 1 seconds
No BootOrder is set; firmware will attempt recovery
Boot0001* Hard Drive
Boot0004  Built-in EFI Shell
Boot0007* Removable Drive

but the system is still running and I would dearly want to recover it in that state without using boot-time tools. My daily backups include /boot so I was thinking about restoring /boot to the last good state and restoring EFI boot with efibootmgr - I am still fuzzy about the details here, so any pointers are appreciated, and locking grub-efi updates. Or is there a better way?

---

### Post by Impavidus on 2019-12-08
Judging from a number of threads in this forum, it seems that there is indeed a problem with a recent grub update on some systems.

---

### Post by oldfred on 2019-12-08
You are not showing an "ubuntu" entry.
       sudo efibootmgr -v  
    
Try this, but I expect the same error. Some systems only boot the hard drive or fallback entry which grub does also now install. That should be at /EFI/Boot/bootx64.efi. And that file is normally a copy of shimx64.efi which boots ubuntu.

If ESP is sda1, you can use a simple entry. If not you have to add which drive & which partition as parameters. See also: man efibootmgr.
       sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi"

       sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.

---

### Post by lvm on 2019-12-08
efibootmgr -v showed more details on each of the entries, but no more entries, so yes ubuntu entry is gone, and running 

efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" 

(/boot/efi is /sda1) displays "Could not prepare Boot variable: Invalid argument" just like the grub-efi updater does. Bugger. I didn't yet rolled back grub-related changes but efibootmgr was not updated for quite a while - dated 2017, and shimx64.efi was not modified during the last update (date is new but comparing it to the same file restored from backup shows no differences).

---

### Post by oldfred on 2019-12-08
What brand/model system?
Have you updated UEFI from vendor.

       Spectre virus, repoline
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.  
Both Windows & Ubuntu have updated systems and since new versions of virus seem to get released, should regularly check that you have latest UEFI from Vendor.

---

### Post by lvm on 2019-12-08
Asrock 990FX Extreme 4 motherboard with Phenom II X4 975 - pretty old and BIOS was never updated.

---

### Post by oldfred on 2019-12-08
Did UEFI get reset?
That updating UEFI will normally reset many settings.

Other brands of motherboards with 990 chipset need IOMMU setting changed. If that reverted to default that could be an issue.
Not sure what else to suggest.

Usually motherboards have better support for Linux.

---

### Post by lvm on 2019-12-09
> **oldfred said:**
> Did UEFI get reset?

I don't know. I probably cannot check it without going into BIOS or can I? As I said, I noticed the anomaly when installing routine grub updates, currently the system is running. Last time it was rebooted a week ago for a kernel update, and it booted fine.

---

### Post by oldfred on 2019-12-09
If UEFI was updated, it would have been a reboot or reboot required.
Only a few newer systems now update UEFI from within Linux.
       [https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

Have you tried running 
sudo apt update
sudo apt upgrade

---

### Post by lvm on 2020-01-10
I finally tried rebooting the affected server, and as I expected it wouldn't boot with 'no bootable device available', and I was able to recover it simply by upgrading (admittedly ancient) BIOS (EFI) to the latest available version.

---

