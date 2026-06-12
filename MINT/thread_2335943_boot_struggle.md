---
title: "boot struggle"
date: 2016-09-02
forum: MINT
---

### Post by saiad on 2016-09-02
firstly hello there I m said from Algeria  I wanted to install a second operating system on my pc after win 10 -because it was free -so I download the ISO and tried to install it and fail from the beginning  until now ... the boot partition is corrupted or have mint files and don t let windows to startup i tried boot repaid but don t resolve the problem  so please help .

---

### Post by saiad on 2016-09-02
here is the report [http://www.cjoint.com/c/FIcvLHWjQF3](http://www.cjoint.com/c/FIcvLHWjQF3)

---

### Post by yancek on 2016-09-02
Your boot repair output shows windows code in the Master Boot Record and the windows boot files on the first partition.  I'm not sure what you did but you didn't install Mint as there is not sign of anything related to Linux Mint on your drives except for the flash drive you used to install.  Have you removed the flash drive with Mint on it from the port on the computer?

---

### Post by saiad on 2016-09-02
hello  yes I have removed the flash drive but there zere the 0xc000001 error then the bsod inaccessible boot I m connecting with the os from the usb because both mint and win 10 don t work actually and also with cmd -command prompt-  *disk part* it says that mint is my primary system and win 10 files or drives are hibernating .when trying to reinstall mint there  is detecting of remaining data witch are not delete or unmountable please help .

---

### Post by Bucky Ball on 2016-09-02
> **saiad said:**
> ... win 10 files or drives are hibernating .

That is your problem, then. You must boot into Windows and switch off hibernation before attempting to install any other operating system or the disk will remain locked. Unlikely you would have been able to install anything on it in that state so I'll take yancek's word for it that you don't have Mint on there.

I don't know how to help you from here. Hopefully someone does. Not sure what you've done there to screw up the Windows boot, but if you can boot into Windows, do so, switch off hibernation, switch off secure boot in BIOS and try again. Good luck.

---

### Post by westie457 on 2016-09-03
There is another problem.
This one is the number of allowed 'primary' partitions.

From your Boot-Report> [COLOR=#000000]=================== parted -l:[/COLOR]
Model: ATA WDC WD10EZEX-00W (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start  End     Size   Type     File system  Flags
1      525MB  184GB   184GB  primary  ntfs         boot
2      184GB  506GB   322GB  primary  ntfs
3      506GB  678GB   172GB  primary  ntfs 
[COLOR=#000000]4      678GB  1000GB  322GB  primary  ntfs[/COLOR]With a 'msdos' partition table the maximum number of primary partitions is 4.
[B]
After backing up all of the files you want to keep[/B] 
You can either delete one of the primary partitions to make space to create an 'Extended' partition.
An extended partition is a container to allow for the creation of more partitions, these partitions are known as 'Logical' partitions. 

The other option is to completely wipe the drive and give it a new 'GPT' partition table.

Both of options are best done using 'Gparted' from the Live dvd/usb.

---

### Post by saiad on 2016-09-03
> **Bucky Ball said:**
> That is your problem, then. You must boot into Windows and switch off hibernation before attempting to install any other operating system or the disk will remain locked. Unlikely you would have been able to install anything on it in that state so I'll take yancek's word for it that you don't have Mint on there.

I don't know how to help you from here. Hopefully someone does. Not sure what you've done there to screw up the Windows boot, but if you can boot into Windows, do so, switch off hibernation, switch off secure boot in BIOS and try again. Good luck.

yes thank you for replay I thought so but there is a lock or a key witch I don t put it because sign in don t request user nor pass by using the terminal from usb live mint it says access denied to the drive of course .
i can enter to the BIOS but I don t know how to switch off or on the hibernation .

---

### Post by saiad on 2016-09-03
> **westie457 said:**
> There is another problem.
This one is the number of allowed 'primary' partitions.

From your Boot-ReportWith a 'msdos' partition table the maximum number of primary partitions is 4.
[B]
After backing up all of the files you want to keep[/B] 
You can either delete one of the primary partitions to make space to create an 'Extended' partition.
An extended partition is a container to allow for the creation of more partitions, these partitions are known as 'Logical' partitions. 

The other option is to completely wipe the drive and give it a new 'GPT' partition table.

Both of options are best done using 'Gparted' from the Live dvd/usb.
I have Gparted 1 GB disk but can you please show me the tutorial thanks for the attention .

---

### Post by yancek on 2016-09-03
If you want to delete/create and or modify partitions with GParted, the best resource for that is the GParted Manual at the link below.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by saiad on 2016-09-03
finally problem solved the solution was the nuber of primary disks and here is the way how insert g parted disk choose disk manager verify if the 500 MB partition is allocated copy one partition in another delete the empty one -copied one - reactive the system partition reboot to the safe mode execute a check disk to the system partition 500 MB there will suggest to do it after reboot then reboot automatic check disk then congratulation you 're back from where you started .
I thanks all the answers of the members and their contribution may peace will be with you .

---

### Post by Bucky Ball on 2016-09-03
Thanks for sharing that. :)

You will spread the message further by marking the thread as 'solved' from Thread Tools' at top of page. See last link in my signature at the bottom of this post if you have trouble with that. 

Enjoy. :)

---

### Post by saiad on 2016-09-04
thank you for every thing ....

---

