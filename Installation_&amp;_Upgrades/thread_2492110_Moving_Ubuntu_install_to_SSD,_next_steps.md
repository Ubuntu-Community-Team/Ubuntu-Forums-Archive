---
title: "Moving Ubuntu install to SSD, next steps"
date: 2023-10-31
forum: Installation &amp; Upgrades
---

### Post by dakspyker on 2023-10-31
Hi All,

I would appreciate some advice on the following matter:

I have installed Ubuntu 23.10 on my "D:" drive recently, with Windows 11 running on the SSD. (On a Lenovo Ideapad)
So I am enjoying Linux immensely, and have messed about with it, installed some software and made some customizations. I moved my photo albums and docs and stuff over to my /home/ and all that.
I like it, and want to move over to Ubuntu permanently.
Both drives in the machine are the same size (1TB), one is HDD and the other is SSD. The Ubuntu installer made a nice dual boot menu, it defaults to Ubuntu but you can choose to boot Windows, which I have stopped doing.

So, my problem:
I would like to move Ubuntu to the SSD, and use the HDD as backup for the /home/ folder. (Or possibly to test different flavours of Linux, but that is besides the point)
I have made a "Rescuezilla" clone of my C: drive incase I need to restore windows (*read: if I FUBAR the laptop with this exercise*)

I think I have two options, both has some pros and cons, please if possible guide me to the safest way:

1. Use Rescuezilla to straight up clone the HDD to the SSD. 
[LIST]
[*]Will the bootloader work?
[*]How to make it boot only from the Ubuntu SSD, no need for dualboot.
[*]Delete HDD partitions and reformat for data use.
[*]Anything I did not foresee?
[/LIST]
       

2. Fresh install Ubuntu to the SSD
[LIST]
[*]Copy/Restore /home/ from current backup (*from an external drive with backintime*)
[*]Re install the softwares I like and need (not too many, but still, will take some time)
[*]Will all my customizations carry over properly?
[*]This seems like much more work than option 1, but safer?
[/LIST]

Bootloaders, UEFI and partitions scare me, I don't want to brick the laptop.

Thank you for your time and advice!

Johann

---

### Post by tea for one on 2023-10-31
The Windows nomenclature of C: D: etc. is not always specific.
C: and D: can mean two drives and _also_ two partitions on one drive.

Your first priority is to backup your Windows and Ubuntu personal data to an external device.
Then, make a careful note of your Windows Product Key and Microsoft a/c password.
Operating systems can be restored from scratch but only you can replace your important data.

In order to fully understand your partitions, can you boot into Ubuntu, open a terminal and enter:-
```
lsblk --exclude 7
```
Please post the command and output within code tags via Adv Reply

---

### Post by yancek on 2023-10-31
Windows does not generally give device letter names to non-windows partitions so forget about 'D'.  You should familiarize yourself a bit with Linux device naming conventions.  It appears from your post that you currently have Ubuntu on one physical drive and windows on a separate physical drive.  Is this an EFI install of both Ubuntu and windows?  I expect it is as that is the default.  Posting the output of the command suggested above will tell that.  If it is, there will be windows boot files on the EFI partition in a directory named Microsoft and Ubuntu files in a directory named ubuntu.  You can verify that easily by navigating to the /boot/efi/EFI directory in Ubuntu.  

Cloning the HD to the SSD may present problems.  FIrst, is there an EFI directory on the HD.  If so, you need to copy the contents to the EFI partition on the SSD, the ubuntu directory. 

If you have not make a lot of changes to configuration files in Ubuntu and have not installed a lot of software, it would be a lot easier to just install Ubuntu to the SSD.  Obviously, make note of changes you have make and back up and personal data first.

Cloning the HD to the SSD might work if you have an EFI partition on that drive and you don't mind overwriting windows.  Post the output asked for in post 2 and you should get more specific suggestions.

---

### Post by dakspyker on 2023-10-31
Thank you! This is very good advice about windows, I did not know that I would need the Product Key.

I will run the command as soon as I get home to my machine and post the result.

---

### Post by dakspyker on 2023-10-31
Output of command as requested:

```
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda           8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1        8:1    0   128M  0 part 
&#9500;&#9472;sda2        8:2    0   9.3G  0 part 
&#9500;&#9472;sda3        8:3    0     1G  0 part /boot/efi
&#9492;&#9472;sda4        8:4    0   921G  0 part /var/snap/firefox/common/host-hunspell
                                      /snap
                                      /
sdb           8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1        8:17   0 931.5G  0 part /media/johann/Backup
nvme0n1     259:0    0 931.5G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   128M  0 part 
&#9500;&#9472;nvme0n1p2 259:2    0   260M  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0 930.1G  0 part /media/johann/Windows
&#9492;&#9472;nvme0n1p4 259:4    0  1016M  0 part
```

---

### Post by tea for one on 2023-10-31
Thank you for the info.
Apologies, unfortunately, I should have offered a more elaborate command to identify your partition structure.
Can you show the terminal output from:-
```
lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
```

---

### Post by MAFoElffen on 2023-10-31
You did not say the model and how recent your Lenovo is... With recent HP, Dell and Lenovo's, the Windows Keys and digital Keys that are burned into the permanent firmware of the motherboards, so no need for the key. When I replaced motherboards on those, I had to reburn the key, with the vendor's utilities for that, to transfer that key.

I only had one issue with that, were the person bought where the computer was made with Home, and upgraded to Pro when then bought it... This was an issue when I brought it back up, because the partitions were encrypted with bitlocker.. I had suspended the bitlocker before I started, but... Couldn't turn that back on with only Home Edition.

Microsoft had records of that., and gave the user another key for the upgrade.

---

### Post by dakspyker on 2023-10-31
> **tea for one said:**
> Thank you for the info.
Apologies, unfortunately, I should have offered a more elaborate command to identify your partition structure.
Can you show the terminal output from:-
```
lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
```

No problem, thanks for the help!
```

NAME          SIZE TYPE FSTYPE FSUSE% FSAVAIL MOUNTPOINT
sda         931.5G disk                       
&#9500;&#9472;sda1        128M part                       
&#9500;&#9472;sda2        9.3G part ext4                  
&#9500;&#9472;sda3          1G part vfat       1%      1G /boot/efi
&#9492;&#9472;sda4        921G part ext4      19%  687.6G /
sdb         931.5G disk                       
&#9492;&#9472;sdb1      931.5G part ext4      16%  719.1G /media/johann/Backup
nvme0n1     931.5G disk                       
&#9500;&#9472;nvme0n1p1   128M part                       
&#9500;&#9472;nvme0n1p2   260M part vfat                  
&#9500;&#9472;nvme0n1p3 930.1G part ntfs                  
&#9492;&#9472;nvme0n1p4  1016M part ntfs  
```

---

### Post by dakspyker on 2023-10-31
> **MAFoElffen said:**
> You did not say the model and how recent your Lenovo is... With recent HP, Dell and Lenovo's, the Windows Keys and digital Keys that are burned into the permanent firmware of the motherboards, so no need for the key. When I replaced motherboards on those, I had to reburn the key, with the vendor's utilities for that, to transfer that key.

I only had one issue with that, were the person bought where the computer was made with Home, and upgraded to Pro when then bought it... This was an issue when I brought it back up, because the partitions were encrypted with bitlocker.. I had suspended the bitlocker before I started, but... Couldn't turn that back on with only Home Edition.

Microsoft had records of that., and gave the user another key for the upgrade.

This is good to know! It is fairly new, about a year or so. Is there any way for me to check this?
So if the key is in firmware, all I need to do is restore the rescuezilla backup and it will work?

---

### Post by yancek on 2023-10-31
The output in post 8 shows that sda3 is your EFI partition for Ubuntu.  The SSD shows device partition   nvme0n1p2 as a vfat partition so that is likely the original EFI partition which has windows.  Using sudo, you should be able to access /boot/efi/EFI and see if there is an ubuntu directory.  There should be.  Mount /dev/nvme0n1p2 to look at the contents.  It should have a Microsoft directory with windows EFI boot files.  If you are going to use the SSD only, you need to copy the ubuntu directory from sda3 to the EFI directory on  nvme0n1p2.  You need to verify that these directories are in these locations before proceeding.  You will likely need to reinstall Grub as the entry in the BIOS is looking for the EFI files on the sda drive and they will be on the other drive.  Probably easier to do a new install to the SSD.

---

### Post by oldfred on 2023-10-31
I almost always suggest new clean install & restore from backup.
It removes built up cruft & makes sure grub is correctly configured.
You cannot have duplicate UUIDs or GUIDs, and some clone tools do not change those.
Be sure to use UEFI install with gpt partitioning. And often best to use Something Else install option to choose/change which partition(s) you want as /, /home or other.

If you change any settings in / (root) like grub, /etc/exports or other system wide configuration files, you want to backup those up. I only edit a couple and just make another copy in /home, so backed up. Others suggest full backup of /etc, but not to restore all of /etc as settings may be different.
Also if any server apps like database or web that are folders in / should be backed up.
You can export a list of installed apps which is just a text file. You can manually edit it, if desired & use to to automatically restore all your apps.
Your user settings are all in /home and then are restored.

This user copied system, but you can it took several days & help in debugging isses.
[https://ubuntuforums.org/showthread.php?t=2491830](https://ubuntuforums.org/showthread.php?t=2491830)

---

### Post by tea for one on 2023-10-31
> **yancek said:**
> Probably easier to do a new install to the SSD.
Having seen the structure, I agree with yancek.

Also, as you are a new Ubuntu user, I would suggest:-

Make a disk image of nvmeon1 (Windows 11) on an external device- Clonezilla would be my weapon of choice
Isolate/remove both sda and sdb - only target disk  nvme0n1 is accessible
Boot into Ubuntu live session in UEFI mode
Check that disk is GPT (via gparted)
Install Ubuntu and allow the the installer to partition automatically
Reboot and check that everything looks good
Restore your personal data

Principal reasons for this approach:-
It builds confidence to install Ubuntu a few times - become familiar with the process
Essential partitions will be created automatically, yet can be altered later if required
You will not have to worry about manipulating Microsoft and Ubuntu directories within /boot/efi/EFI
Restoring a data backup is an invaluable test

---

### Post by dakspyker on 2023-10-31
A huge thank you to everybody for the help. I will do as suggested and do a fresh install. 
I will investigate how to get a list of installed apps, that will help a lot! I have not changed anything apart from user settings, so I should be good to just copy back the last backup from backintime.

Thanks again!
Johann

---

### Post by MAFoElffen on 2023-10-31
> **dakspyker said:**
> This is good to know! It is fairly new, about a year or so. Is there any way for me to check this?
So if the key is in firmware, all I need to do is restore the rescuezilla backup and it will work?
I was a certified HP. Dell, and Lenovo Onsite Warranty Technician... I was the person, that they called out to replace FRU parts under warranty, onsite. If your machine is only a few years old, then yes, I can guaranty that it is burned into the firmware of the motherboard.

Like I said, we had to re-burn that information into replacement motherboards, when we replaced those. If one of us screwed that process up somehow, then we had to ship that new motherboard back, and have another motherboard shipped to us, to do it again. For some vendors, that part of the process was harder than replacing the actual motherboard. LOL

"You can" add an extra fallback for that, through the activation status it shows you from within Windows, by linking it to your Microsoft Account:
> 

[TABLE="class: banded flipColors"]
[TR]
[TH]Activation status
[/TH]
[TH]                             Description[/TH]
[/TR]
[TR]
[TD]                             Windows is activated with a digital license[/TD]
[TD]                             This means that your Microsoft account is not linked to your digital license.
                             Follow instructions for **Add an account**. [/TD]
[/TR]
[TR]
[TD]                             Windows is activated with a digital license linked to your Microsoft account[/TD]
[TD]                             This means that your Microsoft account is already linked to your digital license.
                             No further action is required. You are ready to use the activation troubleshooter.
[/TD]
[/TR]
[/TABLE]


That is also almost a necessity if you do Windows bitlocker, so that you have a fallback for the recovery keys for those. Those keys are 64bits long...

---

### Post by dakspyker on 2023-11-01
Thank you!

---

