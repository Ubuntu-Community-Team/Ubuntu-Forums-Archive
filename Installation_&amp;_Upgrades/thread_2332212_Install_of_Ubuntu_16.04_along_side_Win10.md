---
title: "Install of Ubuntu 16.04 along side Win10"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by sixgunSal on 2016-07-29
Hello, I am brand new at this and I hope I'm in the right area.
I have win10 installed on a 480gig ssd.  I just upgraded from win7 last week.  The windows(the used part of my ssd was ~330gig or so).  When I installed 16.04 I installed it on the same ssd.  It said it would format(?) the part that I wasn't using for the Ubuntu install.  I did not do anything to the ssd - making, resizing, or adjusting any new partitions, I was assuming that the install would do all this. Anyway, when it was done there was no way to boot into it...there wasn't any menu to give me a choice of what to boot into.  I found help here and installed the boot-repair-disk into Ubuntu Live CD.  I ran this repair tool and it now asks me if I want to delete Grub 2 files - it also says my system would be unbootable if I didn't install another boot loader.  At the top of the window it has three lines highlighted to copy/paste into a terminal window. I would copy paste them here but my main pc is the one I'm installing Ubuntu on and this one is a 2nd pc that I'm using to research and obtain some help. ok I mailed them to myself here, they are -
sudo chroot "/mnt/boot-sav/sda5" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda5" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda5" apt-get purge -y --force-yes grub*-common grub-common:i386
 
I guess I'm stuck here without know if I choose "yes" or "no" to delete grub 2 files and do I copy paste those 3 lines into a terminal?  
Thank you in advance.

---

### Post by grahammechanical on 2016-07-29
Boot Repair will produce a Boot Info Summary report and provide a URL to where the summary report is stored online. Paste that URL and we can see what Boot Repair has found.

When you installed Ubuntu what option did you choose to install? Erase disk and install Ubuntu? Install alongside Windows? Something Else?

Did you install Ubuntu in EFI mode or BIOS/Legacy/CSM mode?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Can you load into Windows? Did the machine load into Ubuntu but without providing a menu to give an option to load into Windows?

Regards

---

### Post by sixgunSal on 2016-07-29
Thank you for your help  :)

the url i got was

[http://paste2.org/vGNK0P0V](http://paste2.org/vGNK0P0V)

I think them above "0" are zeros and not O's  at least the zero looks the same as the copy

I choose the option of install along side windows
I’m not sure about the EFI mode or BIOS/Legacy/CSM mode  ---  how would I find this out?
I can boot into windows 10 when I start up...I went into bios and turned off "fastboot"  but it still didn't give me a boot choice, just straight into win10...by reading your link I see that I might have done the "turnoff fastboot" late seeing as I just did that.  I guess Im going to have to boot to win10 and look into the bios to see if its EFI?  I can't getinto my ubuntu install, it only gives me the choice to test it or install it (and I've done that twice just to get to the real ubuntu)

---

### Post by sixgunSal on 2016-07-29
also on a side thread...how do i reboot?  I had to hard boot last time and I dont like doing that

---

### Post by sixgunSal on 2016-07-29
I went into my bios and it says my selected installed operating system is set to UEFI.  The only way to get to a terminal in my Ubuntu install is to reinstall it from my tryout dvd (will be the 3rd time if that matters)
Under disk management all my c: drive is NTSF, the new partitions for ubuntu(?) dont have that.


should i reinstall ubuntu again to get to a terminal to see what it install as?  or should it be good?

---

### Post by oldfred on 2016-07-29
I see three drives, sda as 2TB, sdb as 500MB & sdc as 4TB. The drives show as less with partitioning & formatting.
But all drives are partitioned with MBR(msdos) partitioning which is the 35 year method.
But MBR has a hard internal max of 2TB as even GB was not heard of 35 years ago.

If you have a new UEFI system, you need to always boot in BIOS/CSM/Legacy mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    But are missing out on newer UEFI/gpt capabilities. Installing Windows 7 in BIOS mode originally was probably not optimal but does work.

And Windows only boots with BIOS mode from MBR partitioned drives.
Or Window only boots with UEFI (newer systems) on gpt partitioned drives.

You show grub installed to MBR of sda to boot Ubuntu install on sda.
And you have Windows installs on sda & sdb. And another Ubuntu install on sdb.

Because you used MBR on 4TB drive, you get this error.
 
ERROR: unsupported sector size 4096 on /dev/sdc.
Some vendors tried to make a drive compatible with XP as XP only worked with MBR, not gpt by using non-standard sector sizes.
Better to repartition and reformat using gpt.
If you want to boot Windows on sdb, just choose that drive in BIOS.
The grub in sda, will boot into the Ubuntu install in sda, but grub menu shows Windows in sda & sdb. It does not yet show second Ubuntu install.
Grub on sdb, shows both Ubuntu & both Windows, but you are not booting that version directly.

Bigger issue with Windows 10 is its fast start up or always on hibernation. Grub only boots working Windows and that means no hibernation nor chkdsk required(often required after abnormal shutdown). So with multiple drives often better to have Windows boot loader in Windows drive and Ubuntu boot loader in another drive even if booting install on same drive as Windows. Then when you need to directly boot Windows you can just select to boot that drive.
Those with one drive, when Windows gets corrupted have to temporarily install Windows boot loader, fix Windows, then restore grub.

You need to have Windows 10 Repair flash drive and Ubuntu live installer always available to make repairs when needed.

 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 

If you in BIOS choose to boot sdb drive, does it boot Windows?

---

### Post by sixgunSal on 2016-07-29
The 4T drive is a WD Elements External backup I just got for backing up this pc and the other one. (sdc) was already formatted.
The 500meg is the new SSD I also just bought. I imaged the Win 7 from the 2T drive and copied it to here then upgraded to Win10. I'm thinking of going back to Win 7 after the anniversary update next week. (sdb)
The 2T is the original Win 7 build drive.  I think I installed that from the Win 7 disk so Im really not sure what the bios was set at. (sda)

I can unhook the external 4T drive and run this again, but I guess I still have Windows 7 and Ubuntu on my sdb drive (2T main drive) How do I get Windows and Ubuntu off that drive?  Win 7 & 10 need to stay on the sda drive (500mb ssd).  The SSD was formatted when I bought it .  This is the drive I would rather boot from seeing it is so much faster. Any thoughts of how it can be "fixed" w/o loosing my windows OS?

Okay I also turned off fast startup in the control panel.

Im not sure I understood all that you wrote, I read it about 5 times, and wondering where I go from here.   thank you again

---

### Post by sixgunSal on 2016-07-29
Im not sure what has changed except for the external drive being unconnected

[http://paste2.org/m699eDKP](http://paste2.org/m699eDKP)

---

### Post by oldfred on 2016-07-29
How did you image Windows to new drive?

I missed this before, you cloned drive exactly, but then left old drive plugged in.
You cannot have duplicate UUIDs.

      ```
 /dev/sda2 54CE7E1ACE7DF518 ntfs 
/dev/sdb1 54CE7E1ACE7DF518 ntfs  


```

And you changed the partition number. I do not know Windows well enough but any system does not like changes.

I would install a Windows boot loader to SSD and disconnect temporarily hard drive. And see if you can boot & repair Windows.

Then we will have to change UUID on one drive or the other.

---

### Post by sixgunSal on 2016-07-29
What I did was remove the Ubuntu partitions on the 2T drive.  I didn't realize that Ubuntu makes those partitions automatically until I read that answer you wrote that I read so many times.  After I deleted them and expanded the 2 partitions to take up the un-allocated space and rebooted I got a menu where I could log into Ubuntu or win 10 (plus about 5 other choices).  It works now but will do one of those files to post tomorrow if I don't get a chance tonight.  thank you again.  And yes I have a copy of win 7 on the 2T drive that I imaged using that external drive and cloned it to my new SSD...that would be why I have 2 exact copies of win 7 on 2 different drives.   I'm not sure how to remove it from the 2T drive now that I have it on the SSD.

---

### Post by DuckHook on 2016-07-29
*Thread moved to **Installation & Upgrades** as the more appropriate forum.*

---

### Post by oldfred on 2016-07-29
So is Windows booting ok, even with the duplicate UUIDs?
Ubuntu would not, but Windows seems to work primarily from one drive, so booting would not see other drive.

---

### Post by sixgunSal on 2016-08-01
[Solved]Re: mark post as solved

---

