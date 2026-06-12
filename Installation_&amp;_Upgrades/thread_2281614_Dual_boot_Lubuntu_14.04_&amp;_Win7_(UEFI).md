---
title: "Dual boot Lubuntu 14.04 &amp; Win7 (UEFI)"
date: 2015-06-08
forum: Installation &amp; Upgrades
---

### Post by vasa1 on 2015-06-08
This is my first try to install Linux on someone else's computer. The computer has UEFI and not BIOS and I don't have any experience with UEFI. So I don't want to mess things up.

The computer is a Dell Inspiron 15 3000 Series (low end) laptop with Windows 7 already on it.

From what I could see, **secure boot** is disabled already.

I took over a pendrive with Lubuntu 14.04.2 installed on it, and by changing the boot order, I could test run Lubuntu on his laptop successfully. 

WiFi was detected without any problem.

Then I generated a report as described here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That link is [http://paste.ubuntu.com/11623429/](http://paste.ubuntu.com/11623429/)

As a first step, **could people please look at that report and tell me if things look okay**? I have no knowledge of analysing boot-repair reports. So I don't know if it's good or bad.

If the report is fine, my guess is that the next thing to do would be to delete drive **E** (after moving its data elsewhere) so that the Lubuntu installer can do its job.

---

### Post by leunam12 on 2015-06-08
Get Clonezilla and make a backup copy of your entire hard drive that way if you mess things up you can always go back to square one and start all over again.

Then read this guide

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by kansasnoob on 2015-06-08
> could people please look at that report and tell me if things look okay?

Windows 7 is not installed in UEFI mode so when you do get around to installing Lubuntu you'll want to be sure it also installs in legacy mode, but you have a major barrier to overcome. Since Win 7 is installed on a drive using an msdos partition table there is a 4 primary partition limit to work around and it already has 4:

```
=================== parted -l:

Model: ATA WDC WD5000LPVX-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  106MB   105MB   primary  ntfs         boot
2      106MB   52.4GB  52.3GB  primary  ntfs
3      52.4GB  267GB   215GB   primary  ntfs
4      267GB   500GB   233GB   primary  ntfs
```

Both sda1 and sda2 must remain untouched because they contain important Windows system files:

```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe
```

I'm not sure why but I'd guess the user created two separate data partitions, sda3 = 215GB, and sda4 = 233GB. So probably one of them could be removed after transferring all data to the other but this could be quite a dodgy operation.

Please post a screenshot of what Windows own disk utility shows, and perhaps also a screenshot of Gparted from a live session with Lubuntu so we can get a better understanding of how much data may be on sda3 and sda4.

---

### Post by Bucky Ball on 2015-06-08
*Thread moved to **Installation & Upgrades**.*

Yes, back up valuable data on the machine. When you get to the partitioning section of the install choose 'Something Else' and partition manually. That way you can leave the existing Win NTFS and EFI FAT32 partitions as they are and install Ubuntu into the free space (create / and /swap partitions). If you are installing in EFI, Ubuntu will see the existing FAT32 Win EFI partition and add itself to that. You may need to set that partition to 'Use' but NOT to 'Format' (make sure there is no tick next to it in the 'Format' column).

Don't resize Win partitions with Gparted. Use Win software for them, Linux software for Linux partitions. Good luck. ;)

PS: And yes, as suggested, if you want to be able to put things back 'as they were' if anything screws up, Clonezilla is your friend.

---

### Post by vasa1 on 2015-06-08
> **kansasnoob said:**
> Windows 7 is not installed in UEFI mode so when you do get around to installing Lubuntu you'll want to be sure it also installs in legacy mode, but you have a major barrier to overcome. Since Win 7 is installed on a drive using an msdos partition table there is a 4 primary partition limit to work around and it already has 4:

...

I'm not sure why but I'd guess the user created two separate data partitions, sda3 = 215GB, and sda4 = 233GB. So probably one of them could be removed after transferring all data to the other but this could be quite a dodgy operation.

Please post a screenshot of what Windows own disk utility shows, and perhaps also a screenshot of Gparted from a live session with Lubuntu so we can get a better understanding of how much data may be on sda3 and sda4.

kansasnoob, thank you for taking time to go through the report and your response.

Re. the four partition limit, my friend can empty the E: drive by moving stuff to the D: drive (and to an external backup); there isn't much on the E: drive anyway.

Then I guess we can merge, if that's the right term, both the D: and E: drives and shrink them a bit by using Win 7's disk management tool.

Is that correct? That should then leave us with three primary partitions:
1. Boot
2. Win OS
3. Data

And then Lubuntu can be installed alongside Win 7? If that is the case, how do I ensure that we use the legacy mode? At what point of the installation will that choice appear? Or will that appear just after starting the laptop (pressing F2 for settings or F12 for boot options)?

I have a couple of images taken from a mobile phone of the screen. *But these were taken **after** the boot-repair report was generated and **after** we used  Win 7's disk management tool to shrink the E: drive which might have been a pointless thing to do given that the E: drive needs to be deleted to free up a primary partition (?)*.

I think the first just indicates that Lubuntu can't be installed alongside because of the four primary partition limit.

The second may give you a clue as to what the current state is. It's a bit confusing to me because in the horizontal bar 199.2 GB is shown as free space but in the table below 199230 MB is shown as "unusable".

I don't have access to the laptop now and so can't provide any more information but I'll keep a note of whatever other information is needed.

---

### Post by vasa1 on 2015-06-08
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*

Yes, back up valuable data on the machine. When you get to the partitioning section of the install choose 'Something Else' and partition manually. That way you can leave the existing Win NTFS and EFI FAT32 partitions as they are and install Ubuntu into the free space (create / and /swap partitions). If you are installing in EFI, Ubuntu will see the existing FAT32 Win EFI partition and add itself to that. You may need to set that partition to 'Use' but NOT to 'Format' (make sure there is no tick next to it in the 'Format' column).

Don't resize Win partitions with Gparted. Use Win software for them, Linux software for Linux partitions. Good luck. ;)

PS: And yes, as suggested, if you want to be able to put things back 'as they were' if anything screws up, Clonezilla is your friend.

Thanks, Bucky Ball, all data is backed up. But I'm really hoping to be just able to install "alongside" rather than go for the "Something Else" option. I have absolutely no experience with that though I guess a day will come when I'll have to get to grips with that.

---

### Post by oldfred on 2015-06-08
On systems with UEFI, but installs in CSM/BIOS Mode, how you boot installer is then how it installs.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You should then get two boot options in UEFI for Ubuntu flash drive installer. One clearly should say UEFI & name/label of flash drive. The other will be just the name of flash drive and boots in BIOS mode.

If not sure this shows the first screen you see with both, you want purple screen, not grub on installer:
      Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You still show 4 primary partitions, so rest is unusable. You must delete one of them.
       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by sudodus on 2015-06-08
'Install alongside' is risky. We have seen several threads here in the Ubuntu Forums, where users have 'managed to' wipe Windows, when they have used 'lnstall alongside'. I recommend strongly that you use **Something else** which means manual selection of partitions.

That can be made easier if you use ***gparted*** (that comes with the Lubuntu install drive) and create partitions with a good graphical interface.

After that you start the installer. When you have the partitions, it is rather straightforward to use **Something else**.

-o-

If you have an extra (and fast) USB pendrive or an extra HDD, you can practice with gparted and 'Something else' in another computer (or in a virtual machine, where you need no pendrive, only virtual disks). After that practice, you will be much more confident to install Lubuntu in your friend's computer.

---

### Post by Bucky Ball on 2015-06-08
[This]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343370#343370") may be of some assistance. Good luck whichever way it swings. I did advise 'Something Else' on account of what sudodus mentioned. There are sometimes issues with 'Install Alongside'. You can clearly see what you are doing with something else. :)

As long as you go through it and make a plan before sitting in front of the computer and diving in it should be fairly painless. The main thing with Something Else is you know the installer is not going to mysteriously wipe Win, even though you might! Just mark the existing NTFS partitions 'Do Not Use' and untick 'Format' and sweet.

---

