---
title: "boot error 14.10 with lenovo z510"
date: 2015-03-22
forum: Installation &amp; Upgrades
---

### Post by eda3 on 2015-03-22
Hi,
I have lenovo z510 laptop and installed ubuntu 14.10 but when i open computer i am getting errors so that i am starting with recovery mode in grub.
Then i see ata5.00 failed, failed fpdma queued, comreset faild status DRDY, ATA bus error.
I am waiting your suggestions.
Thank you.

---

### Post by oldfred on 2015-03-23
Does live installer boot ok?

Have you checked that drive is ok in Disks? Click on icon in upper right corner and use Smart Status to view hard drive. All I really know is Disk is ok is good, anything else a problem. But it can run tests and make lots of reports and various drive issues.

Also in UEFI/BIOS is drive set to AHCI?

  Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

---

### Post by eda3 on 2015-04-12
I have installed driver for Nvdia GeForce GT740, nvidia 331.113.
When i open computer i am getting errors like Ata 5.00 bus error status DRDY, I/O error
My bios's sata controller mode is AHCI.
Boot mode, 8 gb sata is legacy.
Grub is coming when i close from power button than i restarting in recovery mode.
But still i couldnt solve to the problem. I have updated, upgraded too.
I just saw your responce.
Thank you for your attentions.

---

### Post by oldfred on 2015-04-12
Someone posted this:

 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 

---

### Post by jeremy31 on 2015-04-12
oldfred, that isn't true of my Lenovo G710.

eda3, you might want to use the gnome disk utility to check the SMART data and self-tests.  The drive in my G710 failed just over a month ago

---

### Post by eda3 on 2015-04-13
My smart disk test result is:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   120   091   006    Pre-fail  Always       -       1482752
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1120
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       35414981
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2189
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1106
184 End-to-End_Error        0x0032   091   091   099    Old_age   Always   FAILING_NOW 9
187 Reported_Uncorrect      0x0032   012   012   000    Old_age   Always       -       88
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       9
189 High_Fly_Writes         0x003a   054   054   000    Old_age   Always       -       46
190 Airflow_Temperature_Cel 0x0022   062   054   045    Old_age   Always       -       38 (Min/Max 24/38)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       146
193 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       8301
194 Temperature_Celsius     0x0022   038   046   000    Old_age   Always       -       38 (0 16 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       8
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       8
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      2188         815393640
# 2  Short offline       Completed: read failure       90%      2188         815393640
# 3  Short offline       Completed: read failure       90%      2188         815393640
# 4  Extended offline    Completed: read failure       90%      2188         815393640
I have some fails. How can i handle to the failings? Thanks all of you for your suggestions.

---

### Post by jeremy31 on 2015-04-15
You might want to back up all data with clonezilla or similar, especially with reallocated sectors.  Might be a good time to shop around for a replacement hard drive

---

### Post by eda3 on 2015-04-16
Hi,
First of all thank you very much for your response.
I may buy a new hard drive but i think this maybe easy way isnt it?
I know mechanical errors cant fix. But what is the aim of to the smartdisk? If so, just for showing errors.
Is there any program or way for increase performance of harddrive?

Thank you for your suggestions.

---

### Post by eda3 on 2015-05-09
Hello
My laptop's problem is solved.
I upgraded to the operating system from 14.10 to 15.04 and computer opens and is not give any error since one month.
 I think this shows my disk have not any mechanic problem.
Thank you for all advices and support.

---

