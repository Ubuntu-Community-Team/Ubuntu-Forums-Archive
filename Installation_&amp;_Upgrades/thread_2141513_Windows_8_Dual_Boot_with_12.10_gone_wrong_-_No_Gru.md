---
title: "Windows 8 Dual Boot with 12.10 gone wrong - No Grub or way to boot into either"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by keevill on 2013-05-02
I have just bought a Lenovo Twist Thinkpad with Windows 8 pre-installed and after reading about dual booting with Linux, I installed Ubuntu 12.10 64 Bit.
Secure boot and fast boot disabled in the bios as I read.
I confess that I used the Windows disk management tool to shrink the disk instead of Gparted .
Everything worked out of the box - even the initial tests with the touch screen. 
Wow !

However, I am unable to boot into Windows anymore.
Error message about cannot find 'drivemap' and Invalid EFI file. 
I tried using Boot-repair via livecd and also installing directly into the Ubuntu os but after taking the defaults, the machine says fault repaired but still no way to boot into windows.
I fiddled around installing another software bootloader called reFIND
This offered me another GUI on boot where I could select Windows or Ubuntu or a repair option.
Again I fiddled.
Now I am in the situation where I cannot get to any boot menu. No Grub nor reFind option.
I land at a blue page headed Recovery and text re PC needs to be repaired.

Can someone point me to the best way to go from here.
Gparted and delete Ubuntu ?
Or what?
Knowledgeable kind person needed here.
Thx,
-keevill-






-david-

---

### Post by oldfred on 2013-05-02
Actually you should use Windows to shrink the Windows partition. It usually works with gparted or the installer but a few have issues.

Did you install in BIOS/CSM mode or UEFI mode. How you boot installer is how it installs.
Boot-Repair can convert from BIOS to UEFI if needed.
Did you try booting Windows without secure boot on? Some system do, some do not and if you have to have secure boot you need the grub signed version and signed kernel. If secure boot not required you can just use the grub-efi version.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by keevill on 2013-05-03
I'm not sure how to tell in which mode I installed.
I have disabled secure boot in the bios permanently.
Here's the link from boot repair installed as you suggested in Ubuntu live cd.
Hope you can help further
[http://paste.ubuntu.com/5628117/](http://paste.ubuntu.com/5628117/)
-keevill-

---

### Post by oldfred on 2013-05-03
Did you boot Boot-Repair in BIOS mode. It looks like it installed a Windows boot loader to the gpt protective MBR which really does not matter, but it added a boot flag on the main Windows NTFS partition. That would be only correct with BIOS boot and MBR partitioning. With gpt the boot flag defines the efi partition.

Use gparted from liveCD to remove boot flag from sda4 as it is showing as a second efi partition. You can only have one efi partition per drive and UEFI has to find efi partition to fine efi boot files. With 2 it is probably getting confused. That may be all you need or you may need to run Boot-Repair but booted with UEFI not BIOS/CSM mode.

You want secure boot off, but UEFI on. And BIOS/CSM off. Each vendor's UEFI has the switches for those settings different and some seem to be confusing. Some have UEFI on as secure boot off. But secure boot is a UEFI boot also. Most will not let you turn CSM on unless secure boot or UEFI is off and some just auto boot depending on if efi partition is found or not.

---

### Post by keevill on 2013-05-03
> **oldfred said:**
> Did you boot Boot-Repair in BIOS mode. It looks like it installed a Windows boot loader to the gpt protective MBR which really does not matter, but it added a boot flag on the main Windows NTFS partition. That would be only correct with BIOS boot and MBR partitioning. With gpt the boot flag defines the efi partition.
Sorry but I'm not sure what I did .

Use gparted from liveCD to remove boot flag from sda4 as it is showing as a second efi partition. You can only have one efi partition per drive and UEFI has to find efi partition to fine efi boot files. With 2 it is probably getting confused. That may be all you need or you may need to run Boot-Repair but booted with UEFI not BIOS/CSM mode.
I did as you said, booting into Gparted Live Cd and removed that flag.

You want secure boot off, but UEFI on. And BIOS/CSM off. Each vendor's UEFI has the switches for those settings different and some seem to be confusing. Some have UEFI on as secure boot off. But secure boot is a UEFI boot also. Most will not let you turn CSM on unless secure boot or UEFI is off and some just auto boot depending on if efi partition is found or not.

I believe I now did as you suggest and ran Boot Repair in UEFI mode with CSM and Secure Boot turned off.
It gave me the happy message Boot successfully repaired as below but sadly it's the same problem. 
Can you please take a look at the paste summary and advise further.
Thanks very much for your help.
-keevill-

Please write on a paper the following URL:
[http://paste.ubuntu.com/5630837/](http://paste.ubuntu.com/5630837/)

---

### Post by oldfred on 2013-05-03
See post #4, you still have two efi partitions, so UEFI does not know what to boot from.

---

### Post by tfbielawski on 2013-05-03
Try this program: [https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/) 

Its a very useful way to repair/replace your bootloader. I had this happen to me before and this little gem fixed it for me. I was able to boot into Linux using a live  Make sure you choose the free version, should be at the bottom left of the page. The user guides explain how to load it onto a bootable USB so you can repair your bootloader. 

Hope this helps. 

Tom
[www.SpecFiction.net](www.SpecFiction.net)

---

### Post by keevill on 2013-05-03
> **oldfred said:**
> See post #4, you still have two efi partitions, so UEFI does not know what to boot from.

Now I cannot boot up into Gparted  - something about a Xorg problem ( server terminated with error ( 1 ).
This is exactly the same ver of Gparted I used an hour ago to remove the flag you advised.
Tried using the failsafe and the VGA mode but no good.
Any other software I can use to go in and attend ( Delete ??? ) one of these EFI partitions ??

---

### Post by keevill on 2013-05-03
Here's a screenshot of what I have.
[http://s1284.photobucket.com/user/keevill/media/Screenshotfrom2013-05-04023655_zpsc5cb353b.png.html](http://s1284.photobucket.com/user/keevill/media/Screenshotfrom2013-05-04023655_zpsc5cb353b.png.html)

---

### Post by oldfred on 2013-05-04
Gparted puts warning or error messages on partitions with issues. The msftres is just unformatted space that Windows has to have so it always has an error.

Did you not turn off fast boot or hibernation with Windows? If it is hibernated, the Linux NTFS driver will not mount it, so you will not be able to remove boot flag. 

You can try the other tools but they may all rely on the standard NTFS driver.
       sudo parted /dev/sda set 4 boot off

[http://www.rodsbooks.com/linux-fs-code/index.html](http://www.rodsbooks.com/linux-fs-code/index.html)
#download gdisk
sudo apt-get install gdisk
# show partitions
sudo gdisk -l /dev/sda


sudo gdisk /dev/sda

You want to use p to list,   t to change type, 4 for sda4,  and then set partition to 0700 not the current ef00
If that works then a w to write corrected info.

      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by keevill on 2013-05-04
Do you mean Quick boot mode in the bios ? No, I have left it turned on so the long winded verbose messages don't appear when  booting. I did not notice if win 8 hibernation was turned on when I was last able to get into it. RIght now, I can't get into any OS other than the Ubuntu Live Cd.
How can I just boot up into Windows and delete the Ubuntu partition to start again ?

Gdisk is an unknown package when I run that command .

I tried another boot repair and here's the latest pastbin.

[http://paste.ubuntu.com/5631181/](http://paste.ubuntu.com/5631181/)

---

### Post by oldfred on 2013-05-04
Now sda2 shows as a data partition and it should be the efi partition.

You now also have sda4 and sda5 as efi partitions, and they should be data partitions.

Until you have just one efi partition sda2, I do not think you can boot anything. Once you fix that, then you should be able to go into UEFI menu and boot either Windows or grub, depending on whether your system boots with only secure boot on or not. Some have to have secure boot on to boot Windows. Some will boot with it off.

---

### Post by keevill on 2013-05-04
I'm unable to either see these efi partitions or indeed effect any changes using the Gparted in my Ubuntu 12.10 live cd which is the only way I can boot into Gparted.
I'm stuck .

---

### Post by oldfred on 2013-05-04
You have to be able to boot something to fix it. Or you have to then remove drive and plug it into a working computer to make the fixes.

Some systems just get locked up after boot errors. A full cold restart is required which is difficult with laptops.
       Total cold boot with laptop
Laptop full power reset. post #4 hold power on switch after removing battery
[http://ubuntuforums.org/showthread.php?p=12401315](http://ubuntuforums.org/showthread.php?p=12401315)

---

### Post by keevill on 2013-05-04
> **oldfred said:**
> You have to be able to boot something to fix it. Or you have to then remove drive and plug it into a working computer to make the fixes.

Some systems just get locked up after boot errors. A full cold restart is required which is difficult with laptops.
       Total cold boot with laptop
Laptop full power reset. post #4 hold power on switch after removing battery
[http://ubuntuforums.org/showthread.php?p=12401315](http://ubuntuforums.org/showthread.php?p=12401315)

I think we're going off at a tangent here. I am asking how to change the efi properties of the partitions which are showing up as conflicting in the pastebin ( boot repair ) report.
I can now boot up into Gparted but this software doesn't show me either the efi properties nor the fact that the other partitions are data partitions.
How do I change these properties which I am being advised so to do ?
Should I just re-install Ubuntu ? Will that give me a starting point for the repair of a boot loader to adjust for Windows boot selection ?

---

### Post by oldfred on 2013-05-04
Gparted only shows the boot flag for a efi partition. So you should only  have one boot flagged partition and it needs to be the efi partition sda2. If you are in gparted, click on each partition and right click to show flags. Remove boot flag from all other partitions.
I am surprised it lets you set more than one boot flag per drive. When using command line tools setting boot flag on automatically removes boot flag from all others.

---

### Post by keevill on 2013-05-05
I did as you suggested and removed flags except from SDA 2 using Gparted.
Booted up into Ubuntu 12.10 Live Cd and ran boot repair.
I get the message EFI detected and ran the auto repair after checking install boot to SDA2.
Here's the report. 
Are we getting anywhere now ?

[http://paste.ubuntu.com/5634312/](http://paste.ubuntu.com/5634312/)

---

### Post by oldfred on 2013-05-05
You must have booted in BIOS mode, it will still say efi detected. But it reinstalled a BIOS Windows boot loader to the MBR which does to work with UEFI on gpt partitioned drives. Ubuntu will boot from a MBR with gpt but Windows will not.
If Boot-Repair is offering to reinstall a boot loader to the MBR you are not checking the correct efi option. 

Did you not just change boot flags, but reformat partitions? They look like they are now unformatted or you may need to reinstall?

---

### Post by keevill on 2013-05-05
ok , I think it's time to give up trying to repair this and instead I should re-install both OS . Agree ???
So, if that's the way to go , what's the best way to prepare the HDD for this ?
Gparted and then set up partitions in which format for easiest dual booting please?
Thanks,
-keevill-

---

### Post by oldfred on 2013-05-05
With UEFI & gpt Windows has specific requirements. If a clean install or using the recovery it should create the standard set of partitions.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

