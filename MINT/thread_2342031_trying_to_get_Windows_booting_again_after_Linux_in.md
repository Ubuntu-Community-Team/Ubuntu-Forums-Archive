---
title: "trying to get Windows booting again after Linux installation"
date: 2016-11-03
forum: MINT
---

### Post by harald1 on 2016-11-03
I have Installed Linux Mint 18 Xfce on a partition and tried with  boot-repair to set  grub / mbr up so that all 3 OS (Linux and 2  Windows)  are available to boot.
I have also played around with Testdisk setting up boot sectors for a Windows partition, without success.

Here is what I did with boot-repair launched from a live USB stick:

Recommended repair : --> only Linux and memtest appears in grub 

[http://paste.ubuntu.com/23419847](http://paste.ubuntu.com/23419847)



Tried to repair MBR: 
Advanced options:
Under Main Options: selected 'Restore MBR'   (default was 'Reinstall Grub')
Under  MBR Options - Partition booted by the MBR: selected 'sda7(Windows)'   ; ( default was 'sda1 (Linux Mint 18 Sarah)' )

--> no boot at all, no error, just a cursor blinking on a black screen
[http://paste.ubuntu.com/23420015](http://paste.ubuntu.com/23420015) 


Recommended Repair: --> grub with Linux and memtest available
[http://paste.ubuntu.com/23420051](http://paste.ubuntu.com/23420051) 


In  short, recommended repair works fixing grub to boot Linux, but I need  help to figure out how to set it up to be able to boot Windows.


I am looking forward to hearing from you, thank you.

---

### Post by Bucky Ball on 2016-11-03
*Thread moved to **MINT**.*

Welcome. Have you tried opening a terminal and doing this?

```
sudo update-grub
```

... then reboot. Any sign of Windows?

You have Windows inside an extended partition. Not sure that will boot at all. You need to give more detail. Have you just installed all this??? Windows should be installed *first* on first *primary* partition of the *first* drive if you want to save yourself some time and headache. Install Ubuntu second and anywhere, it doesn't mind.

---

### Post by harald1 on 2016-11-03
Thank you for taking the time to reply.
Yes, I have indeed tried before to change the default partition with 'sudo xed /etc/default/grub'  and  than applying it with 'sudo update-grub'. 
When I set it to 2 it always booted into memtest and I had to get into grub with holding the shift key to be able to boot Linux again and set it back to 0. When setting it to 4 and rebooting, nothing changes, only the options with Linux and memtest appear in grub. Btw, memtest does show 0 errors. 


I thought the summary files should provide enough info to get this fixed; on the description of the tool it says the issues are solved by a simple click.

Anyway, the 2 Windows Os are installed and working now for years, I could choose at boot which one to use and that was working fine until yesterday. So, to answer the question, Windows was installed first. If the issue is with primary/secondary partition, the question would be if it is possible to change this property with some utility, maybe with gparted. 

I have installed Linux on a partition which was available and since then Windows does not show up at boot time. From what I read on the web (I spent **a lot** of time trying to fix it myself) I think the MBR was damaged/deleted  and I am hoping to repair it with the boot-repair tool. Are there some options to choose in this tool to achieve this? As 'Restore MBR' does not seem to be enough..

---

### Post by Bucky Ball on 2016-11-03
Boot Repair will not repair the Windows boot. There is a specific way of fixing this and I don't know it (and am not willing to blindly guide you). Hopefully someone else can chime in that does but Boot Repair is not it. Boot Repair is to get the Grub working in Ubuntu so you can see all OSs. If the Win boot is broken, it's not going fix that.

Can't really help, but yes, you have got some problems. There is this:

```
Quantity of real Windows: 1
WinSE in sda7
/mnt/boot-sav/sda7/ may need repair.
/mnt/boot-sav/sda7/bootmgr may need repair.
```

And you have this same message for sda6, 7 and 8:

```
Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
```

Might have something to do with it.

---

### Post by harald1 on 2016-11-03
Hmm, I was really hoping it would repair Windows boot, at least this is what is says in the description:

Boot-Repair lets you fix these issues with a simple  click, which (generally reinstalls GRUB and)** restores access to the  operating systems you had installed before the issue**.  

Boot-Repair also has advanced options to back up table partitions, back up bootsectors, create a [Boot-Info]("https://help.ubuntu.com/community/Boot-Info")  (to get help by email or forum), or change the default repair  parameters: configure GRUB, add kernel options (acpi=off ...), purge  GRUB, **change the default OS, restore a Windows-compatible MBR**, repair a  broken filesystem, specify the disk where GRUB should be installed, etc.

and also the option 'Repair Windows Boot files'  in the 'Other options' tab.  ( [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) )

---

### Post by Bucky Ball on 2016-11-03
Yea, Boot-Repair "restores access to the operating systems you had installed before the issue." Exactly what I said. I, and this description, say nothing about fixing the Windows boot sector if it is broken. You have a broken Win boot sector and also a dodgy partition or more by the looks of it. ;)

I said this:

[QUOTE=BB]Boot Repair is to get the Grub working in Ubuntu so you can see all OSs. If the Win boot is broken, it's not going fix that.[/QUOTE]

Pretty much what it says on the packet ...

---

### Post by harald1 on 2016-11-03
Thank you for the clarification, it is more clear now to me.

before testing with boot-repair I have used testdisk with instructions from here [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) .

At NTFS Boot sector recovery section, it shows a screenshot with bad sector and after this is repaired. On my system both partitions with Windows had 'Boot sector' and 'Backup boot sector' on OK. In my opinion this makes actually sense, as they were working fine until installing Linux Mint.  Even so, I have used the option 'Rebuild BS' for sda5 , without success though. 
Before I installed Linux Mint I looked at the system/hidden folders on that drive/partition. There was a folder 'boot' and I suspect this is the one which is missing and makes me searching for an utility to restore/repair it. 
Before using testdisk I have used gparted and have set the boot flag to sda5 partition, which unfortunately did not bring Windows in the boot options either. 

What do you think about these tools?

---

### Post by harald1 on 2016-11-03
Following the code you have posted I have taken a closer look at it in the summary file.

I can see that actually sda5 partition (with Windows) is fine:

```
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda5 was processed successfully.
```

and think that "Quantity of real Windows: 1"  is referring to this partition.

The other Windows partition, sda7 is according to the summary "Refusing to operate on read-write mounted device /dev/sda7." 


Shouldn't this actually mean that boot-repair should be able to restore access to sda5 ?

---

### Post by oldfred on 2016-11-03
Boot-Repair only fixes minor Windows issues, normally you need to have a Windows repair flash drive especially if chkdsk is required or other major repairs.
If you have Windows install flash drive it also should have repair console.

But your issue is you deleted the Windows boot partition.
Windows only boots from one primary NTFS partition with the boot flag. 
Then second installs overwrite boot code in first install's boot partition, so normally only one NTFS partition is bootable.
Since Windows 7 the default Windows install is a separate Boot partition (usually sda1) and then main install. Boot partition is typically just 100MB.
A second install of Windows can be a logical partition but again, its boot files will be in the primary NTFS partition with boot flag. You do not have to have separate Boot partition, but Windows partition with boot files must be a primary NTFS formatted partition with boot flag.

It looks like you have primary partitions left. So shrink sda1 and make a new NTFS partition with boot flag as primary partition. Then from a Windows repair disk run the full set of Windows repairs. Cannot be done from Boot-Repair. (needs copywrited Windows files, so Boot-Repair cannot use them). Some third party Windows tools may work, as they licensed Windows files.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

---

### Post by yancek on 2016-11-03
Your boot repair shows 3 and sometimes 4 windows partitions starting at sector 63 which is the first partition sector on the drive.  That won't work.  You also have all of your windows partitions on logical partitions and you need to have at least the boot files on a primary partition in order to boot windows so it looks like you modified your partitions somehow.  You can install pretty much any Linux on a logical partitions without problem.

Just noticed the post above by oldfred which gives details on how to try to repair.  You're not going to fix this with boot repair or Linux tools.  If you don't have a windows installation DVD or Recovery CD for whichever windows version you have, you might be able to find something to download online.  Good luck.

---

### Post by harald1 on 2016-11-03
@ olfred
thank you for the information.

sda1 is actually the 10GB partition where Linux Mint is installed, would you think this OS will have enough space if I shrink it?

On  the disk there is 10 MB unallocated space, I have seen it is possible  to create a primary partition with gparted out of it. Do you think this size would be enough to set it with boot flag as primary partition with NTFS file system and afterwards to run the Windows repair?  If yes, would it also work to create 2 primary partitions of 5 MB, as you advised to create a second one? 

@yancek
yes, I installed Linux Mint on that partition, which seems to be the primary partition. This installation probably has deleted the 'boot' folder from this drive.

---

### Post by oldfred on 2016-11-03
I consider 10GB tight for a full install. You have to regularly houseclean and cannot install a lot.
But I have a 16GB flash drive with 8GB for install & 8GB for data, but do not install much of anything as it is just for emergency boot.

But Windows boot partition is typically 100MB, and I think it uses most of it. Have not really paid attention to actual used size, but many posts show dual booting Windows with boot partition in Boot-Repair's summary report.

Generally best to keep Windows as first or first couple of partitions and only use logical partitions for Linux with the older BIOS/MBR configuration. New UEFI/gpt systems do not have logical partitions, so totally different.

---

### Post by harald1 on 2016-11-03
I see; well in this case I either have to take 100 MB from the Linux partition, or remove the Linux and run Windows repair to set is as primary with boot flag.
I choose the first option now.

---

### Post by harald1 on 2016-11-04
Hi,

I have created a new 200 MB primary Ntfs partition with label 'A', by shrinking the one where Linux is installed and have set the boot flag on it.

Then I ran Windows repairs by following these instructions [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader). 

I inserted the Windows XP CD, ran repair mode.

When entering "fixboot" into the console it says target partition C:. It asks if I am sure to write new boot sector in partition C:. C is the drive where Linux is installed.
I choose yes, so it was executed successfully 

fixboot a: - did not work , could not find the drive     (a is, or should at least, the new 200 MB partition )
fixboot d: - worked fine, result at reboot:  "BOOTMGR is missing "   (d: is the windows xp partition)


fixmbr  --> successful
it wrote a new MBR on physical drive \Device\Harddisk0\Partition0 

result: --> at boot it says
NTDLR is missing
Press Ctrl + Alt + Delete to restart 



Changing the the boot flag (using the USB ) back to the partition where Linux is installed (drive C) at boot it says: "Error at loading operating system".
Changing flag back to the 200  MB partition -->  "NTDLR is missing" at boot time .


Please help..

---

### Post by harald1 on 2016-11-04
Hi, 

an thank you answering to the thread. 

No, one XP on drive d: / sda5   and one Vista on drive f: sda / 7 . --> the recovery console of XP offered to access the one from drive f: as well, but it did not accept the administrator password, so I was able to test only with XP on drive d:. 

The partitions are basically the same as before, just with an extra 200 MB primary with boot flag Ntfs partition which I have created following your advise. 


This is the boot.ini file  on c:  (which probably was created with fixboot or fixmbr):

```
[boot loader]
timeout=20
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
```

partition 3 is correct, it is the windows partition where XP is installed and which has assigned drive d: --> this can be seen in diskpart. 

I could correct the ntldr message by copying  ntdlr and ntdetect to  drive d:  as I have found in a tutorial on the web. 
Then I got the error about the file   Windows\System32\Hal.dll which I was able to correct with these instructions: [https://support.microsoft.com/ro-ro/kb/945380](https://support.microsoft.com/ro-ro/kb/945380)


Current error I get and cannot fix with what I found on the web is: "[SIZE=2]Reboot and select proper device[/SIZE]" - I applied [this]("http://www.deskdecode.com/reboot-and-select-proper-boot-device-explained/") . 

I have also set the hard drive to be primary master as it was not, and still the same message shows up at start time.
When trying to set the partition active as indicated in the "Set partition as active on Windows XP section"  from [here]("https://neosmart.net/wiki/set-partition-as-active/#Set_partition_as_active_on_Windows_XP") , I get stuck at step 7. After typing 'diskpart' the partitions are displayed; there is no option to type anything the only options available are  ESC=Cancel and L=delete  (its in german, german word for delete starts with L).  If  you think it is useful, I can write here the partition list, which diskpart displays. 

In short I need help on setting the partition active with diskpart   and correcting and progressing from the "[SIZE=2]Reboot and select proper device[/SIZE]" error.

---

### Post by oldfred on 2016-11-04
Are all your Windows installs XP type? Then you may not be able to use separate boot partition.
XP is so obsolete you need to think about retiring it anyway.

Windows boots from MBR which looks for partition with boot flag. It then loads the code the the PBR or partition boot sector.
The site on Windows explains there are two PBR versions for Windows. One is the XP type that uses XP files to boot, so you then have to have XP's ntldr and boot.ini. The other type is all versions of BIOS boot from Vista on. That uses bootmgr & BCD. Normally XP is all in one c: drive. Vista was also, but from Windows 7 on, they you have the separate 100MB boot partition. 
You may need to use a Windows 7 or later repair/install disk.

 Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM

Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe  

Not sure now what partitions you now have, but since earlier post showed several primary partitions available. If sda5 was Windows and first partition in extended, you probably could convert it back to a primary.

---

### Post by harald1 on 2016-11-04
sorry I edited the above post, instead of replying;
the answers to the questions you have posted and what I tested and current bottleneck are there.

```
diskpart shows following partitions:

J: Partition1 [Unknown]         10031 MB  ( 10031 MB free  )  --> this is the Linux ext 4 partition which probably diskpart can't read very well
C: Partition2 (A)          [NTFS]      204 MB   (    201  MB free)
D: Partition3  (XP)       [NTFS]     20401 MB   (  4490   MB free) 
E: Partition4  (Musik)    [NTFS]     30710 MB   (   5006  MB free)
F: Partition5  (Server)  [NTFS]      30710 MB   (   2511  MB free)
G: Partition6  (VM)       [NTFS]     60463 MB   (   3959  MB free)
    Unpartitioned space    8 MB   
```

---

### Post by oldfred on 2016-11-04
You may need chkdsk on your NTFS partitions. 
The PBR must have the correct start and size of partition to match the partition table.
Your earlier report showed partitions all starting at sector 63?

---

### Post by harald1 on 2016-11-04
yes, I ran chkdsk on c: and d:  before running the windows repairs;
do you mean to run it on all partitions? that would take a lot of time and I would be able to finish only tomorrow. 

Yes, the report showed that, but now the partition sd5 ( partition d: with XP )  did not show that anymore and looked good. The others do further show that in the summary file, probably because I did not work on them ( except c: of course ).

---

### Post by oldfred on 2016-11-04
Not sure what else to suggest.
Sometimes Windows internals get out of sync and the only fix is reinstall & restore from backups.

---

### Post by harald1 on 2016-11-05
managed to finally boot Windows XP!
We were on the right track, I found that actually the 200 MB partition should be set to active, not D: with Windows XP. I did this by setting the boot flag in gparted  on the live Linux USB disk and Windows XP booted.

After this I have tried a lot to get the other Windows to start - I have downloaded a Vista repair disc and burned it to a CD. 
Booted the computer with this CD and saw it does repairs automatically, it does not show options in the 'System Recovery Options' window as described here [https://neosmart.net/wiki/set-partition-as-active/#Set_partition_as_active_on_Windows_Vista](https://neosmart.net/wiki/set-partition-as-active/#Set_partition_as_active_on_Windows_Vista) .  So it does not offer a recovery console.
It shows only the operating system and gives 2 options: 'load drivers' and 'next'. 

In the protocol it says  that the boot sector code for the partition is corrupted  (although it has been rebuilt with testdisk).
Repair action: Boot sector repair
Result: Completed successfully. Errorcode = 0x0

--> this time at reboot Windows Vista finally started :)   - It took 3 times running these automatic repairs of the recovery disc. 


Then searching how to add XP to the boot menu, I discovery the wonderful EasyBCD tool which made it very easy to do this.

It also allowed me to add Linux Mint from the first partition to the boot menu, so now I can choose between all 3 operating systems at boot time :)

Thank you all for the help and advises, It took 3 and a half days of work and frustration to achieve this, but without the advise to create an additional primary partition for booting, I wouldn't have got here. It is amazing how much work such an installation can do, but anyway I have learned a lot these days.

---

### Post by oldfred on 2016-11-05
Glad you got it working. :)

I think I said Windows only boots in BIOS mode from a primary NTFS partition with boot flag.
And chkdsk from correct/booting version of Windows can fix PBR. You may be booting Vista from XP partition so correct version is then Vista.

I believe testdisk still makes an XP type PBR to boot with NTLDR. But if you have converted to using Vista you need the newer PBR to boot with bootmgr.
I once ran chkdsk from a Windows 7 repair disk on my XP. It did more fixes than the old XP chkdsk, but converted PBR to Windows 7 type. In testdisk using the [dump] command on testdisk's NTFS recovery screen, I could see backup said ntldr and primary said bootmgr.

---

