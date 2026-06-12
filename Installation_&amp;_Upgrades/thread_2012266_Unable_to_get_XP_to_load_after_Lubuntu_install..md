---
title: "Unable to get XP to load after Lubuntu install."
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by dani9678 on 2012-06-28
I wanted to tryout Lubuntu on my laptop a few days ago because for one, I was getting tired of all of the memory Windows XP SP3 was using and I read how much faster lubuntu works on older hardware compared to XP. So, I downloaded Lubuntu version 12.04 32bit and wanted to install it beside XP. The drive is 60GB I believe and I had 20 free. I booted from the CD and installed it with a 15GB partition. After reboot, the grub menu popped up and it listed XP at the bottom. I went ahead and tried out Lubuntu and right off the bat liked how much faster it would load and with 3 websites up and a video playing, I wasn't using more than 380MB of my 1GB of RAM versus almost 1GB in XP. After I was done playing around with Lubuntu, I rebooted and selected XP and after the Windows logo popped up, it would flash a bsod and restart. It was so fast that I couldn't make out the error. I read an article on how to repair the XP boot after a linux install on one of the forums here. It involved using an XP install disc and using recovery console. I followed along and ran fixmbr, and the ntldr repair command(forgot what it was). After rebooting, all I would get now is NTLDR missing. Of course the GRUB menu was gone and so I would immediately get that error message instead of seeing the GRUB menu first. I put the install disc back in and this time it showed 3 partitions. The biggest one which use to be XP listed as a FAT partition instead of NTFS. I followed another article on how to get GRUB working again but now when I select XP from the menu, I get the NTLDR MISSING message still. I don't want to do any more with out some guidance because I don't want to add anymore problems to what I already have. I want to reverse install Lubuntu and get XP back up and running first and then try another route at re-installing Lubuntu without affecting XP.

Please Help!!!

Thanks,  
Matt

---

### Post by marinara on 2012-06-28
your XP repair effort failed.  You can try repairing it again, but most likely you need to install xp over again.  You did back up?

---

### Post by dani9678 on 2012-06-28
Did I do it wrong? Can you walk me through the proper steps? Maybe I missed something. When the GRUB menu loads, it lists that there is an NTFS partition with XP on it but when I use the install CD for XP, it sees the same partition as FAT.

Matt

---

### Post by oldfred on 2012-06-29
Best to post details of install from Boot info script. You can run it from a gui from a liveCD or USB or download the script directly.

This should reinstall grub2's boot loader if you want, but post link to bootinfo so we can see details.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by dani9678 on 2012-07-01
Well, I tried the recommended repair option from the Boot Repair menu and after reboot, the option to pick XP for boot has been removed. Here is the link that was posted. 

[http://paste.ubuntu.com/1070195/](http://paste.ubuntu.com/1070195/)

Matt

---

### Post by elliotn on 2012-07-01
I am not sure but NTDR error means the system can find the OS, I think it got messed up while u partition. can u access the XP files when u click the partition in lununtu,  if so backup everything u want and then reinstall XP but if u can't it really means you messed up the XP partition

---

### Post by oldfred on 2012-07-01
Script is showing an inconsistency. Partition says its boot sector is FAT16, but partition table says it is NTFS. Windows XP if installed in NTFS needs a NTFS partition boot sector (PBR) that will call out the ntldr to boot.

I might try testdisk. You may be able to recover the backup or it can create a basic PBR that Usually works with XP. Windows 7 often still needs repairs to change from XP to Windows 7 PBR.

You do not have grub installed, but the repair to use testdisk to restore from backup is the same.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)


[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Rebuilding An NTFS Boot Sector On An NTFS Partition 
small 'system reserved' NTFS partition instead of the partition where windows was installed.

---

### Post by dani9678 on 2012-07-01
It was originally an NTFS partition. I don't know how it was converted to fat 16. I followed the directions for the recovery of XP by running the fixboot command in the recovery console of XP the other day which I guess maybe what caused it to get worse. Will replacing the boot sector with the backup boot sector convert the partition back to NTFS?

---

### Post by oldfred on 2012-07-01
If you ran fixBoot, the backup may also be bad. But testdisk can rebuild a NTFS partition boot sector. After that we need to see if it is ok or needs further repair.

FixBoot should not have caused the problem, not sure how it would occur?

---

### Post by dani9678 on 2012-07-01
OK I ran testdisk and confirmed that both Boot Sectors are bad. So I can run the rebuild bs command?

---

### Post by dani9678 on 2012-07-01
I selected Analyze and it lists two identical primary partitions. What do I do to rebuild the boot sector? I selected advanced and then rebuild bs. It now says : Extrapolated boot sector and current boot sector are different. What do I do next?

---

### Post by oldfred on 2012-07-02
When you were in the screen to compare boot sectors is a button to Rebuild BS or rebuild Boot Sector. Also see attached.

---

### Post by dani9678 on 2012-07-02
In the screenshot it shows the two boot sectors as ok. Mine were both listed as bad. Did you post that there just for reference for me to see what to look for? I did see a rebuild boot sector option and I selected it. After running it goes on to say "Extrapolated boot sector and current boot sector are different." and then it lists at the bottom " Dump, List, Write, Quit".

---

### Post by oldfred on 2012-07-03
Post was from my XP which has a good NTFS PBR & a good backup. It was just to show the screen and the options at the bottom.

I think you have to write the new PBR for it to work. Dump may just compare old & new, list may just show it? Have not had to do all those my self.

 I have had to restore from a backup as I once used a Windows 7 repairCD to run chkdsk. That chkdsk actually worked better than the XP chkdsk, but it wrote a Windows 7 PBR looking for bootmgr not ntldr. It was interesting in the comparison to see the differences in the two versions of NTFS PBRs.

---

### Post by dani9678 on 2012-07-03
So if my backup is bad as it says then when I select "Write", wouldn't that just rebuild the Boot sector with another bad Boot Sector?

---

### Post by YannBuntu on 2012-07-03
Hello
The problem may be bigger than only the bootsector, because XP is now detected neither by os-prober nor BootInfoScript.

Here is another way to repair XP:
1) Download [this ZIP file]("http://fspsa.free.fr/cdr.zip"), extract it somewhere, then burn the ISO on a CD (as an image, not as a file). This is a XP Recovery Console.
2) Boot on the CD, choose the Repair menu ("R"), then type the following commands:
```
fixmbr
fixboot c:
bootcfg /rebuild

```

If the PC reboots directly to XP, you won. Then use Boot-Repair to recover the GRUB menu.
If XP still doesn't boot, I have no other solution than reinstalling XP.

---

### Post by oldfred on 2012-07-03
Testdisk has two functions, one just restores/copies the backup, and the other creates a new NTFS partition boot sector. Windows has several different NTFS PBR, so the one created seems to work for data or XP, but Windows 7 needs the same repairs but from a Windows 7 repair disk to work.

Windows will only normally repairs partitions it sees as NTFS (or maybe FAT). But if partition is not NTFS then the Windows repairs usually fail.

---

### Post by dani9678 on 2012-07-03
> **oldfred said:**
> Testdisk has two functions, one just restores/copies the backup, and the other creates a new NTFS partition boot sector. Windows has several different NTFS PBR, so the one created seems to work for data or XP, but Windows 7 needs the same repairs but from a Windows 7 repair disk to work.

Windows will only normally repairs partitions it sees as NTFS (or maybe FAT). But if partition is not NTFS then the Windows repairs usually fail.

So should I go ahead and select "Write" or should I do what YannBuntu said to do? Which would you do first? I'm just afraid that I may be making the problem worse if I run two different programs.

Matt

---

### Post by oldfred on 2012-07-03
If Windows does not see partition correctly it will not run repairs. So try testdisk first. Then if it does not work you will need to the the Windows repairs  from a Windows CD, that YannBuntu suggested. To some extent they are doing the same thing. Trying to repair the NTFS partition boot sector.

---

### Post by dani9678 on 2012-07-03
I ran "Boot Repair" again but this time just to get a report summary after writing the new boot sector in testdisk.

Here is the link

[http://paste.ubuntu.com/1074205/](http://paste.ubuntu.com/1074205/)

It now lists it has having an NTFS partition on the drive but there are inconsistencies in it. I rebooted the computer and it still loads the GRUB menu with no mention of XP so apparently the GRUB menu wasn't affected by the write done by testdisk.

---

### Post by oldfred on 2012-07-03
It still says FAT16.

>  Boot sector type:  FAT16

Did you write a new NTFS PBR from testdisk?

If partition was actually reformated to FAT16, it may be a bigger issue.

---

### Post by dani9678 on 2012-07-03
I just ran testdisk again and it doesn't list duplicates like before for the primary partition. It lists it as 
                      Start         End      Size in sectors
1 * HPFS - NTFS      0  1  1  5473 2178 32      87937385


Is the above name just that a name given for the primary partition and not actually telling me that it is an NTFS partition?

It is also telling me that the boot sector and backup boot sector are both OK and the sectors are identical. It also gives me the option to repair the MFT which I don't remember seeing before. Should I attempt this?

Matt

P.S. I tried to arrange the above partition info as it was listed on my screen but there must be an auto arrange enabled or something because it gets drawn up together. Is there a way that I can do a screen capture in Lubuntu and paste it somehow? I'm new to Linux as you can tell.

---

### Post by oldfred on 2012-07-04
If it is just text from a terminal, you can preserve formating by using the code tags. You can easily use code tags by highlighting like a copy and click on the # icon in the edit panel above your message. You can also take screen shots and upload with the paperclip icon.

---

### Post by dani9678 on 2012-07-04
I know that I can by pressing prt scrn and pasting in Microsoft Paint or notepad but I don't know how to do that in Linux. If I could, I would paste it and save the file so that I could attach it for you to see. Anyways, I was hoping that you could make out what I said in the earlier post. Can I just repair the Master File Table? Do you think that might do the trick? That option wasn't there before I had written in the new boot sector which also seemed to have eliminated the double primary partition listing.

Matt

---

### Post by oldfred on 2012-07-04
Normally you only run the testdisk repair of the MFT after chkdsk from Windows has failed. Windows tools to repair Windows is normally the first choice, but Linux can often do some repairs easier or even better than Windows.

If you have the NTFS boot sector back then Windows should see the NTFS partition and let you run chkdsk.

Does this say it is NTFS?
```

sudo fdisk -lu
```

---

### Post by dani9678 on 2012-07-04
Here is what the first row says  under device boot after running the above command:

/dev/sda1 * start: 63 End: 87937447 Blocks: 43968692+ Id: 7 System: HPFS/NTFS/exFAT

---

### Post by oldfred on 2012-07-04
Partition table entry looks ok. Have you tried chkdsk from your XP repair console or install CD?

---

### Post by dani9678 on 2012-07-04
No I haven't yet. Should I go ahead and do what YannBuntu suggested?

---

### Post by oldfred on 2012-07-04
Yes, but also include chkdsk. Some additional instructions if you want linked below.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by dani9678 on 2012-07-04
I ran the commands in the order you had listed and bootcfg /rebuild came back with an error saying that it was corrupt. I went ahead and I'm now running chkdsk. It seems to hang at 50% and then speed to 75% before starting back over at 50% complete.

---

### Post by dani9678 on 2012-07-04
OK it finally stopped repeating. It says it fixed one or more errors on the volume. I'll go ahead and reboot to see if it made a difference.

---

### Post by dani9678 on 2012-07-04
Here is the new Boot Repair log.

[http://paste.ubuntu.com/1075620/](http://paste.ubuntu.com/1075620/)

It states that it is now an xp ntfs but XP isn't listed in the grub menu when I reboot.

---

### Post by dani9678 on 2012-07-04
I decided to go ahead and download that recovery console file that YannBuntu posted and found that it's in French  so I guess I'll just stick with what I have. I don't know if it matters or not but I believe that XP Professional SP3 is what I have installed on the laptop. Let me know what you think of the latest report that I posted a link to.

---

### Post by dani9678 on 2012-07-04
I ran fixboot again and then I ran bootcfg /rebuild which I got the same negative results again. It says the following:

Error:
Failed to successfully scan disks for Windows installations. This error may be caused by a corrupt file system, which would prevent Bootcfg from successfully scanning. Use chkdsk to detect any errors.

One other thing I noticed also is that as soon as I run chkdsk, it gives the volume creation date which I thought would be the date at which it was installed on the drive but it says 02/26/01 at 04:38p which I don't understand because the laptop was made back in 2006.

---

### Post by oldfred on 2012-07-04
Script looks normal to me.

Have you tried 

sudo update-grub

It should find your Windows and add it to the menu. Cross your fingers & it should boot.

---

### Post by dani9678 on 2012-07-04
I didn't realize you just replied. I added a few more lines to my last post in regards to chkdsk. I'm running chkdsk /r again and it's at 62%. I don't know if that's going to cause a problem running it again. I ran recovery console again just before chkdsk and it still couldn't find the Windows installation.

---

### Post by oldfred on 2012-07-04
If chkdsk had an error before, rerunning it is a good idea. Chkdsk does not fix all errors on each pass, so often more than one run is required.

---

### Post by dani9678 on 2012-07-04
Alright. I'll let you know how I do with the commands you gave to add XP back to the grub menu.

---

### Post by dani9678 on 2012-07-05
I ran sudo update-grub and it found Windows XP and added it. I rebooted and selected xp and now it just shows a black screen with a blinking cursor at the upper left corner.

---

### Post by oldfred on 2012-07-05
If os-prober found it and added it to menu, it was able to mount NTFS partition and see boot files.

It is now just an XP issue. Boot files look ok. Did chkdsk complete ok the last time?

Can you see the rest of the Windows files from Ubuntu that you normally have?  Particularly Windows and Windows/System & Windows/system32?

Did you run fixBoot from the XP disk. Sometimes that also repairs something more than the chkdsk?

---

### Post by dani9678 on 2012-07-05
I powered up the computer this evening and now the grub menu is gone and it loads straight to a blank screen with a blinking cursor.

---

### Post by dani9678 on 2012-07-05
I booted into recovery console again and this time I typed fixboot and enter. Then I typed fixmbr and enter. It came back with the following message:

**CAUTION**

This computer appears to have a non-standard or invalid master boot record. FIXMBR may damage your partition tables if you proceed.

 This could cause all the partitions on the current hard disk to become inaccessible.

If you are not having problems accessing your drive, do not continue.

Are you sure you want to write a new MBR?

That is the message I get.

I went ahead and booted from the Lubuntu CD since now I'm unable to access lubuntu because of the grub menu missing. Yes I'm able to view all of the folders you mentioned in your previous post and also access the files inside of them.

---

### Post by oldfred on 2012-07-05
If you did fixMBR that puts the Windows boot loader into the MBR. That is fine as then you can test that Windows works and that it is not an issue with grub2.

You can restore the grub2 boot loader any time.

You can use the Boot-Repair or manually install grub2's boot loader to the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
[COLOR=DarkRed]sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda[/COLOR]
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
[COLOR=DarkRed]sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR]


# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by dani9678 on 2012-07-05
So even though it says that it has detected an invalid boot record and that if I proceed, I may be lose access to the drive by writing another MBR that I can do this with confidence? If I do lose access, will I be able to get back in? The caution makes it sound as if I will lose all access to the drive and have to reformat if I write another MBR.

Matt

---

### Post by oldfred on 2012-07-05
The MBR consists of two parts, one is the boot loader and the other is the partition table.

Overwriting the boot loader is very common and done with every install of a new or different system.

Normally gparted or other partition tools are the only way to change the partition table. You have posted your partition table so it is actually possible to use that info to restore it in worst case (not easy as you manually have to rebuild it). But just reinstalling the Windows boot loader should not change partition table.

If you really want you can back up your partition table to a text file and then that can be restored easily if necessary.
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by dani9678 on 2012-07-05
How do I access lubuntu from boot without grub so that I don't have to use the lubuntu CD?

---

### Post by oldfred on 2012-07-06
Did you get Windows to boot, or do you still have grub2 in the MBR?

You really cannot boot Lubuntu with a Windows boot loader in the MBR. Another repair CD, super grub often works  as it bypasses grub and finds the kernel to boot.

You can install another copy of grub to a liveUSB or a CD and make that the copy of grub that boots your install in the hard drive. But you have to manually add the boot stanza. You can copy the one in your install, so that is not so difficult, but it is a bit to create a grub2 only boot USB or CD.

I have grub2 installed in every hard drive & flash drive I have. In many of them I have added extra boot stanzas to allow booting something else just in case I need it.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

### Post by dani9678 on 2012-07-07
I typed the following command just as you had it typed and got the following message:

Warning: extended partition does not start at a cylinder boundary. DOS and Linux will interpret the contents differently.

I used the Lubuntu install CD to run Lubuntu. I don't know if this may be causing the above message to display

Matt.

---

### Post by oldfred on 2012-07-07
Ignore the cylinder boundary error. Disk drives do not use cylinders anymore even though many tools report them. BIOS converted from cylinder to LBA or large block allocation when hard drives went over 8GB 15 years ago. Sectors are now more important, not cylinders.

With very new drives having the new 4K drives or SSDs on 8 sector boundries is important.

But your BIOS should not be set to some legacy IDE setting?

---

### Post by dani9678 on 2012-07-07
I went ahead and ran fixmbr and agreed to the caution. After rebooting I still get the blank screen with the blinking cursor. I also restarted with the xp cd again and loaded it as if I was doing a repair install and it still didn't detect an existing OS.
All it sees is an NTFS partition on C: and two unknown partitions that Lubuntu created. This sure has been a mess. All from me just wanting to try out Linux on a seperate partition.

---

### Post by oldfred on 2012-07-07
Is boot flag still on your XP partition? Windows only repairs the partition with the boot flag or in Windows the active partition.

Not sure why you seem to have so many issues. Many have just installed and had dual booting work without issue. It used to be a bigger issue with Windows 7 as then you really need to use Windows 7 tools to shrink the NTFS partition. But with XP gparted or the install normally shrinks the NTFS partition and lets you install.

---

### Post by dani9678 on 2012-07-07
I don't know what "boot flag" is. How do I find if it's on the partition?

---

### Post by msammels on 2012-07-07
From Lubuntu:

```
sudo apt-get install gparted
sudo gparted
```

Selected the right /dev/sd and check under "Flags" for "boot".

---

### Post by dani9678 on 2012-07-07
/dev/sda1 which is NTFS has the "boot" flag listed. What would be the next thing to try?

---

### Post by dani9678 on 2012-07-10
Well..... I hadn't heard back from ya since my last reply a few days ago. Everything alright?

---

### Post by oldfred on 2012-07-11
I have lost track of where we are. What works and what error messages do you still get. Post link to  a new copy of BootInfo report.

---

### Post by dani9678 on 2012-07-11
I have forgotten how to get a boot info report. I have to use the Lubuntu boot CD because I don't have the grub menu to load Lubuntu on the hard drive. As for what it is doing now. Without the Lubuntu or XP install CD in the drive, it will do it's memory tests and the screen will refresh, then it just has a blinking cursor at the upper left corner of a black screen. I do know that I can reboot the computer by pressing ctrl-alt-delete at this point which I couldn't with linux. I believe this is only possible with Microsoft. Not sure. I would have to find another computer and pull the drive then press the same keys to see if it would reboot.

---

### Post by dani9678 on 2012-07-11
I figured out how to get the boot info report.

Here is the "Boot-Info" results.

```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /ntdetect.com

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    87,937,447    87,937,385   7 NTFS / exFAT / HPFS
/dev/sda2          87,939,070   117,209,087    29,270,018   5 Extended
/dev/sda5          87,939,072   115,130,367    27,191,296  83 Linux
/dev/sda6         115,132,416   117,209,087     2,076,672  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7C00BDFCC08E2000                       ntfs       
/dev/sda5        d247e574-a5cd-41d9-b96b-e40d64457c2b   ext4       
/dev/sda6        8f24eb50-228a-44f5-9f3e-4efa0a98cfa3   swap       
/dev/sr0                                                iso9660    Lubuntu 12.04 i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/7C00BDFCC08E2000  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/d247e574-a5cd-41d9-b96b-e40d64457c2b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root d247e574-a5cd-41d9-b96b-e40d64457c2b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root d247e574-a5cd-41d9-b96b-e40d64457c2b
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d247e574-a5cd-41d9-b96b-e40d64457c2b
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=d247e574-a5cd-41d9-b96b-e40d64457c2b ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d247e574-a5cd-41d9-b96b-e40d64457c2b
	echo	'Loading Linux 3.2.0-26-generic ...'
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=d247e574-a5cd-41d9-b96b-e40d64457c2b ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-26-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d247e574-a5cd-41d9-b96b-e40d64457c2b
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=d247e574-a5cd-41d9-b96b-e40d64457c2b ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d247e574-a5cd-41d9-b96b-e40d64457c2b
	echo	'Loading Linux 3.2.0-25-generic ...'
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=d247e574-a5cd-41d9-b96b-e40d64457c2b ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d247e574-a5cd-41d9-b96b-e40d64457c2b
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=d247e574-a5cd-41d9-b96b-e40d64457c2b ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d247e574-a5cd-41d9-b96b-e40d64457c2b
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=d247e574-a5cd-41d9-b96b-e40d64457c2b ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d247e574-a5cd-41d9-b96b-e40d64457c2b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d247e574-a5cd-41d9-b96b-e40d64457c2b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 7C00BDFCC08E2000
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d247e574-a5cd-41d9-b96b-e40d64457c2b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8f24eb50-228a-44f5-9f3e-4efa0a98cfa3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  48.442501068 = 52.014739456   boot/grub/core.img                             1
  46.538181305 = 49.969991680   boot/grub/grub.cfg                             1
  43.363723755 = 46.561443840   boot/initrd.img-3.2.0-23-generic               2
  43.369049072 = 46.567161856   boot/initrd.img-3.2.0-25-generic               3
  43.691036224 = 46.912892928   boot/initrd.img-3.2.0-26-generic               2
  46.479732513 = 49.907232768   boot/vmlinuz-3.2.0-23-generic                  1
  42.898086548 = 46.061469696   boot/vmlinuz-3.2.0-25-generic                  1
  43.464485168 = 46.669635584   boot/vmlinuz-3.2.0-26-generic                  2
  43.464485168 = 46.669635584   vmlinuz                                        2
  42.898086548 = 46.061469696   vmlinuz.old                                    1



```

---

### Post by oldfred on 2012-07-11
You are directly booting Windows and the boot script seems to show everything in the correct places. The partition boot sector at least reports itself as NTFS, you have the three main boot files, ntldr, ntdetect.com & boot.ini. And script printed boot.ini and it looks normal as it says it is booting from the first drive & first partition which is correct.

Some have just replaced ntldr & ntdetect.com. Very occasionally they may be damaged.

You said you have run chkdsk until there are no errors so file structure should be ok.

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

Beyond that I cannot offer anything else. Perhaps a Windows forum may know more.

---

### Post by dani9678 on 2012-07-12
I'm beginning to wonder if the xp os is actually home and not professional. I thought for the longest time it was professional but now without seeing it boot, I'm not sure. I know the laptop was a refurbished government model.

Do you know how to see which it is even though it doesn't load? Could using an  xp professional install cd cause problems with an XP Home OS?

---

### Post by dani9678 on 2012-07-18
You asked if I could boot into lubuntu. I have to use the install CD of lubuntu because there is no menu to access lubuntu at boot. Do you know how I can access it without using the CD or menu and not affect the boot partition of Windows? Also, How do I mount the NTFS drive to do what you said?

---

### Post by dani9678 on 2012-07-18
I went ahead and used the Lubuntu CD and did what you said and copied the ntldr and ntdetect files from the 386 folder to the root drive and it still wants to give a blank screen with a blinking cursor.

---

### Post by oldfred on 2012-07-18
Windows partition looks normal. Has the boot files and script at least says it normal. It can only be some internal errors and normally Windows repairs will fix those.

I might try the full set of repairs, but then I am out of ideas. Re-install and recover from your backup.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by dani9678 on 2012-07-23
I'm going to be using another drive until I can get this squared away and was wondering if you know how I could get my wireless card to work on my laptop with Lubuntu? I read the directions and it seems I have to wind up going through a hole ordeal just so that it will work. That was another reason why I wanted to keep XP on there so that I could use my wireless card. In case I hadn't already given this info, it is an HP/Compaq nc6220. p/n: EG828EC#ABA.

It says it contains an Intel WLAN radio model WM3B2915ABG.

Thanks,
Matt

---

### Post by oldfred on 2012-07-23
Open a new thread with that info or search forum. Some know a lot about wireless issues, I do not.

---

### Post by dani9678 on 2012-07-23
Alright, Thanks

---

