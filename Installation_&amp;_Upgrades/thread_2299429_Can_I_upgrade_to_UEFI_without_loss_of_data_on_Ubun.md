---
title: "Can I upgrade to UEFI without loss of data on Ubuntu Server 14.04 legacy boot?"
date: 2015-10-18
forum: Installation &amp; Upgrades
---

### Post by patricia1066 on 2015-10-18
I installed Ubuntu server 14.04 on a new Dell T20 Poweredge, using USB live created on my mac using dd.
I usually install linux legacy mode when using USB, so I chose this as the sole OS on the server machine. Now I realise I cannot get AHCI which has advantages in monitoring the server remotely.
I have a backup of Webmin but could lose the Mac time machine on the drive /dev/sda1, so hope I wont have to reinstall with loss of data. 

My brand new drive is showing errors, and worse, today fdisk shows that the drive doesnt contain a valid partition table. Yesterday this test was fine, but that was before I tried to change to UEFI, and it failed to boot. I saw this post with instructions on changing from Legacy to UEFI. 
[http://askubuntu.com/questions/509423/which-commands-to-convert-a-ubuntu-bios-install-to-efi-uefi-without-boot-repair](http://askubuntu.com/questions/509423/which-commands-to-convert-a-ubuntu-bios-install-to-efi-uefi-without-boot-repair)

Is this relevant to me, and as my 1TB drive is one of 4 drives is AHCI useful enough to risk my backups? I want to install 16GB RAM and run 
Ubuntu server with Snapraid.

My configuration:

Dell Poweredge T20
Intel(R) Xeon(R) CPU E3-1223 v3 @ 2.60GHz
4GB RAM, 

Ubuntu Server 14.04.3
Postfix, Webmin 7.3
RAID Yes, but Disks are non-RAID at present


```
serverpat@DU:~$ sudo fdisk -l /dev/sda1
Disk /dev/sda1: 996.0 GB, 996004593664 bytes
255 heads, 63 sectors/track, 121090 cylinders, total 1945321472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   142   142   000    Old_age   Offline      -       69
  3 Spin_Up_Time            0x0007   126   126   024    Pre-fail  Always       -       182 (Average 182)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       50
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   113   113   000    Old_age   Offline      -       35
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       101
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       50
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       51
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       51
194 Temperature_Celsius     0x0002   148   148   000    Old_age   Always       -       37 (Min/Max 17/42)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0012   100   100   000    Old_age   Always       -       101
241 Total_LBAs_Written      0x0012   100   100   000    Old_age   Always       -       1539795734
242 Total_LBAs_Read         0x0012   100   100   000    Old_age   Always       -       552033503

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        99         -
# 2  Short offline       Completed without error       00%         2         -
```

---

### Post by patricia1066 on 2015-10-18
I could resolve this by going into BIOS to allow boot from USB, install on another disk UEFI nonsecure.

The disks are ext4 with MBR. 

Will this work?

---

### Post by oldfred on 2015-10-18
You want to list sda, not sda1, so error on a partition not having partition table does not mean anything.

sudo fdisk -l
       sudo parted /dev/sda unit s print

But if you want UEFI, you need drive to be gpt partitioned, not MBR(msdos). And it is recommended that ESP- efi system partition be first, although Windows makes it second or third, but not at end of a large TB size drive. Not sure if you created an ESP at end of drive is UEFI can find it.

But my BIOS only system worked with ACHI on. I actually booted same Ubuntu with it on or off. But I had to turn it on to use SSD and have trim work, but with ACHI on XP would not boot. That was a plus as I wanted SSD, but had to finally turn off XP. :)

My newer system is UEFI and I only have it configured for UEFI.

---

### Post by patricia1066 on 2015-10-18
Thanks oldfred, good to know the current boot disk is fine.

I dont have plans to use SSD on the Dell so maybe I will make do without AHCI. 

If I format a disk gpt and install Ubuntu to it, I can then remove the MBR from the old boot disk?

---

### Post by oldfred on 2015-10-18
If not a boot disk you may be able to convert from MBR to gpt. But good backups required. If a boot disk it requires reinstall of grub & lots of editing.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by patricia1066 on 2015-10-18
On rereading I wasnt clear that I have a few disks to play with. 

Currently sda is legacy boot. 

/dev/sdc is newly formatted ext4 160gb drive. If I reformat sdc with GPT, then install uefi on it, will the boot files on sda be ignored on boot? No editing needed in this case?

---

### Post by oldfred on 2015-10-18
With UEFI grub only installs to the ESP on sda. Not sure what it does if sda is MBR.
I tried installing to sdb in UEFI mode and had ESP on sdb & it said installing to sdb, but installed to sda.
You can change drive order if plugging in new drives. SATA port order is usually the drive order in UEFI and then in Ubuntu. So move new drive to SATA port 0 or first port.

---

### Post by patricia1066 on 2015-10-19
Will do tonight. Thanks for the links, very useful

---

### Post by patricia1066 on 2015-10-22
I decided to live with the current setup, as its stable.

---

