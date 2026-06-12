---
title: "Cannot find &quot;Install Ubuntu alongside Windows&quot; in the installation menu"
date: 2017-12-09
forum: Installation &amp; Upgrades
---

### Post by p33p3rm1nt on 2017-12-09
I burned the official Ubuntu image 16.04.03 to a USB stick using Rufus. The format was "GPT Partition for UEFI". I have disabled Secure Boot and I have set the allowed OS-s as UEFI only with CSM support.

The Live Demo can boot just fine from the USB Stick and most things work right out of the box. But when I start the installation process I can't find the option to install Ubuntu alongside Windows. I tried by changing the BIOS to allow Both Legacy and UEFI (same result). I genuinely do not know what else to try. I want to install Ubuntu alongside Windows. Any suggestions?

---

### Post by yancek on 2017-12-09
Do you have any unallocated space on the drive you want to install Ubuntu to?  You can use windows Disk Management to shrink your largest windows partition to make unallocated space.  Best to do this from windows and if your windows has been installed for some time, run Disk Degragmenter before resizing and after shrinking reboot windows and run chkdsk before trying to install Ubuntu.  You don't indicate which windows you have but if it is 8 or 10, it is almost certainly UEFI/GPT and you need to install Ubuntu the same.  The link below is the official Ubuntu documentation on dual booting with windows UEFI, read it before starting.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Frogs Hair on 2017-12-09
Was the drive used with a RAID setup ? If not see post above.

---

### Post by westie457 on 2017-12-09
Another thing to be aware of is Windows being protected with 'bitlocker'. Some time ago I had this issue with an Asus Transformer T100chi. Turning off bitlocker allowed all installation options.

---

### Post by p33p3rm1nt on 2017-12-09
@yancek I don't have any free space. But up until now I never had to  resize the windows partition beforehand (I am not comfortable playing  with partitions manually). Everytime I previously installed Ubuntu I  would get to choose how much space I wanted to take off Windows for  Ubuntu (even though initially I had no free space) during the  installation. That's why the "install alongside Windows" missing option  is a problem.

@westie457 No bitlocker on my machine.

@Frogs Hair

I  don't know how to see if it has a RAID setup (if you have a specific  tutorial for Win10). I did not find any reference to RAID, SATA, AHCI or  IDE in the Device Manager. Maybe I should have mentioned I have an SSD  not HDD, so my device controllers are NVMe Express Device Controller and  Microsoft Storage Spaces Controller.

---

### Post by ajgreeny on 2017-12-09
I believe that with the most recent versions of Windows (8 & 10 in particular) it is quite dangerous to edit or shrink the partitions using the Ubuntu installer and much safer to use the Disk management utility in Windows itself.

I also think that the previous versions of Windows that you remember used fewer partitions so there was less of a difficulty making space if on an MSDOS partition table.  GPT partitions may have overcome the numerical limit to the number of possible partitions, but Windows has become a lot more fussy, so for your peace of mind I strongly recommend that you shrink the partition that you need to using Windows, not the Ubuntu installer, nor gparted from the live system if you were tempted to do that before installing.

---

### Post by oldfred on 2017-12-09
Have you turned off Windows fast start up or always on hibernation? Linux does not mount hibernated Windows, so then it cannot see it to know you have it or be able to resize it.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

While normally gparted or Ubuntu installer would resize NTFS partition for install without issue, there have been cases where users had issues. May have been an issue in Windows, but then user blames Linux.
And generally safer to use Windows tools for Windows & Linux tools for Linux.
And NTFS needs chkdsk after a resize, so best to resize using Windows & then reboot immediately so it can run chkdsk.

Be sure to have good backups before making any changes.

---

### Post by p33p3rm1nt on 2017-12-09
Fast Start Up and Hibernation are both off. 

I am hesitant to play around with partitions and risking wrecking the PC. I have never done this before and I do not have the time to deal with a broken or corrupted storage (since I've never had to before and this is new territory). Given all the circumstances that I have described earlier, is erasing the disk and installing Ubuntu - no Windows - a safe course of action (from the Ubuntu installer)? Or would I need to reformat or repartition the storage from Windows beforehand too?

---

### Post by Frogs Hair on 2017-12-09
Take a pause and be sure if you want to remove Windows all together and open Windows disk management and use the snipping tool to take an image of the partition table. You can use the paper clip in the reply box to upload the attachment.It may be helpful to those here to see what the partition table looks like.Shrinking the partition is not that scary and tutorials are easy to find.

---

### Post by p33p3rm1nt on 2017-12-09
This is my partition screenshot. The removable media (D: drive) is just my USB, which is still plugged in.

[https://imgur.com/a/B5awg](https://imgur.com/a/B5awg)

There should be in total 512 GB of SSD, PCIe-NVMe OPAL2.0. And the sum of all the memory sans D: drive (my usb) still falls short of that.

---

### Post by yancek on 2017-12-09
Before you "Erase disk and install Ubuntu" I would suggest strongly that you read the link I posted earlier, the Ubuntu documentation on windows/Ubuntu UEFI.  If you install Ubuntu you will probably still have options in the BIOS for EFI and those vary depending upon the manufacturer and could cause problems.  EFI settings are on the firmware on the motherboard so overwriting the HD won't change that.

From the image you posted, you would need to shrink what windows refers to as the C:\ partition to make room for Ubuntu.  You should be able to find numerous tutorials on using Disk Management on windows 10 with an online search.  If you aren't comfortable with it, don't do it.  You can use Ubuntu from the flash drive until you are more familiar with it.

---

### Post by nothingarian on 2017-12-11
[COLOR=#000000]shrink the partition [http://www.x4artists.com](http://www.x4artists.com) that you need to using Windows, not the Ubuntu installer [/COLOR]

---

### Post by leunam12 on 2017-12-12
If you are afraid of messing up your Windows all you have to do is back it up, that way if something goes wrong just restore it back.
With a Linux tool: download clonezilla from clonezilla.org and burn it on CD or USB drive and boot it and choose to make an image of your
whole Windows drive.

Using Windows: press WINDOWS_KEY+R and type:```
sdclt.exe /BLBBACKUPWIZARD
``` then follow the instructions to make a backup image of your system disk. 
You are going to need a boot disk to restore this image so, press the Windows key and type "create recovery drive", and follow the instructions (you need a USB drive).

---

