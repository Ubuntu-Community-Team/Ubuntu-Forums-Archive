---
title: "Ubuntu messed up my bootloader"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by Oneblo on 2010-06-14
Hi!

I installed Ubuntu on my desktop the other day, and found out I had overwritten Windows 7 bootfiles.
So I decided to uninstall Ubuntu, and then delete the partitions (with the Windows 7 DVD)

Now, once BIOS is finished loading I get a entirely black screen with a white border flashing in the top left corner.

What to do?
I tried to use the Windows 7 DVD to fix it auto, and command prompt on the Windows 7 DVD to with it manually.

---

### Post by garvinrick4 on 2010-06-14
> **Oneblo said:**
> Hi!

I installed Ubuntu on my desktop the other day, and found out I had overwritten Windows 7 bootfiles.
So I decided to uninstall Ubuntu, and then delete the partitions (with the Windows 7 DVD)

Now, once BIOS is finished loading I get a entirely black screen with a white border flashing in the top left corner.

What to do?
I tried to use the Windows 7 DVD to fix it auto, and command prompt on the Windows 7 DVD to with it manually. If you cannot fix windows 7 bootloader with recovery CD and the two lines of code at command line it is in trouble, would have been simple before you deleted anything. Are these the instructions you used for 7:
                                 Vista and 7 fix boot 
How to restore the Windows Vista or 7 bootloader To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD. If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for Vista or Win 7. When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer." On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next. Then click on "Command prompt". From there, type in the following: 

Code: bootrec.exe /fixboot 

Code: bootrec.exe /fixmbr  
 
Please use the words after code and not with code in command line of windows recovery disk

Then close window and restart should have Windows bootloader installed

---

### Post by wilee-nilee on 2010-06-14
Those commands don't remove grub from the MS OS, post the script in my sig in code tags

---

### Post by garvinrick4 on 2010-06-14
> **wilee-nilee said:**
> Those commands don't remove grub from the MS OS, post the script in my sig in code tags

He has got just Windows 7 left and no boot manager. Needs to install windows bcd.
It is a copy and paste I have used often. It is not in code tags because I just copy and
paste that section. Only two short lines, will do.

---

### Post by Oneblo on 2010-06-14
Thank you, garvinrick4.

But I've already tried that with no luck.

---

### Post by wilee-nilee on 2010-06-14
> **garvinrick4 said:**
> He has got just Windows 7 left and no boot manager. Needs to install windows bcd.
It is a copy and paste I have used often. It is not in code tags because I just copy and
paste that section. Only two short lines, will do.

It may be that grub was installed in the widows partition though that is why we need the script to see if that is the case. We need to see the windows boot stuff here.

---

### Post by Oneblo on 2010-06-14
> **wilee-nilee said:**
> It may be that grub was installed in the widows partition though that is why we need the script to see if that is the case. We need to see the windows boot stuff here.

Yes, you're correct. 
GRUB was installed on the Windows partition.

I cannot run the script as I ONLY have Windows 7 installed, but cannot boot into it. The bootloader is messed up after GRUB.

---

### Post by wilee-nilee on 2010-06-14
> **Oneblo said:**
> Yes, you're correct. 
GRUB was installed on the Windows partition.

I cannot run the script as I ONLY have Windows 7 installed, but cannot boot into it. The bootloader is messed up after GRUB.

The script can be run with a live Ubuntu cd.

---

### Post by Oneblo on 2010-06-14
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f112242

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4028 MB, 4028628992 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7868416 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            128     7,868,415     7,868,288   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       5a624f2c-27f1-4a0a-a4eb-58d22995d148   ext4                                     
/dev/sda1        B4A884EAA884AC84                       ntfs                                     
/dev/sdb1        C6C8-E088                              vfat       MULTIBOOT                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/MULTIBOOT         vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


============================== sda1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD

find --set-root --ignore-floppies /boot/grub/menu.lst
configfile /boot/grub/menu.lst

# All your boot are belong to NeoSmart!
```

---

### Post by garvinrick4 on 2010-06-14
Hey partner run the whole script in Live Cd and then highlight whole text and the click on the pound sign and it will put it in window that can be scrolled and will not take up whole page.

---

### Post by Oneblo on 2010-06-14
> **garvinrick4 said:**
> Hey partner run the whole script in Live Cd and then highlight whole text and the click on the pound sign and it will put it in window that can be scrolled and will not take up whole page.

I'm sorry, but I have no idea what you're talking about.

---

### Post by garvinrick4 on 2010-06-14
Still got a WUBI in bootmanager in Windows it seems.
Needs to be deleted. 

If you can get to command line in Windows 7 disk and delete it

```
bcdedit
```

find one with wubilder in it.
 
```
bcdedit delete {indentifier # in the one with wubilder with the brackets}
```

---

### Post by garvinrick4 on 2010-06-14
willee-nelee he had a WUBI install not a partition. How about that. Stupid of me not to ask.
That is why you were right in wanting to see a script run. Good call wilee-nelee.

---

### Post by Oneblo on 2010-06-14
> **garvinrick4 said:**
> Still got a WUBI in bootmanager in Windows it seems.
Needs to be deleted. 

If you can get to command line in Windows 7 disk and delete it

```
bcdedit
```

find one with wubilder in it.
 
```
bcdedit delete {indentifier # in the one with wubilder with the brackets}
```

This is what I have:

[[IMG]http://img18.imageshack.us/img18/9977/14062010138.th.jpg[/IMG]](http://img18.imageshack.us/i/14062010138.jpg/)

---

### Post by garvinrick4 on 2010-06-14
> **Oneblo said:**
> I'm sorry, but I have no idea what you're talking about. you did it right no problems.

---

### Post by wilee-nilee on 2010-06-14
> **garvinrick4 said:**
> willee-nelee he had a WUBI install not a partition. How about that. Stupid of me not to ask.
That is why you were right in wanting to see a script run. Good call wilee-nelee.

I don't know much, really you have more skills in knowing commands, but I know the importance of seeing the whole picture. ;)

OP I think this will take some work with more experienced people. You are in good shape it just has to be approached in the correct manner. The most important role for me here is protecting the operating system, by not running willy-nilly with instructions. Within a couple of hours the regulars who are very good at this will be on line.

I think I know the fix but would rather see the people who really know the approach to this that is best, give you instructions.

I see one of the people on line now so I suspect you will getting a visit shortly.

---

### Post by Oneblo on 2010-06-14
Well, after running bcdedit command in command prompt it semms only Windows 7 is in the bootloader.

I used this guide to do that: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Anyways, I don't see why it should not work as it looks good in bcdedit.
Might be NeoSmart?

---

### Post by wilee-nilee on 2010-06-14
> **Oneblo said:**
> Well, after running bcdedit command in command prompt it semms only Windows 7 is in the bootloader.

I used this guide to do that: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Anyways, I don't see why it should not work as it looks good in bcdedit.
Might be NeoSmart?

The best thing to do here is not to mess with it until we have more experienced help. If you have run some fixes then you need to post the script again. It is difficult to fix these things if fixes are tried that don't work and the original script posted does not represent the setup now. So take a breath relax run the script again, if you have done additional fixes and wait for help.

As I added to my last post one of the best at this is on line right now so hang if you can.;)

---

### Post by darkod on 2010-06-14
> **Oneblo said:**
> Well, after running bcdedit command in command prompt it semms only Windows 7 is in the bootloader.

I used this guide to do that: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Anyways, I don't see why it should not work as it looks good in bcdedit.
Might be NeoSmart?

So are you able to boot win7 now or not?

You didn't seem to have full ubuntu at all, so I have no idea what partition you say you deleted with the win7 dvd or which boot files you overwrote initially.

All looks fine in the results. Even wubi is still there and you said you uninstalled ubuntu.

---

### Post by Oneblo on 2010-06-14
I installed Ubuntu 32-bit and booted it up.

The GRUB bootloader welcomed me, and I selected Ubuntu (not Windows 7)

Ubuntu started booting, and when I was finished with whatever I was doing in Linux, I rebooted and selected Windows 7 instead (on the GRUB menu)

The GRUB menu wasen't able to boot Windows 7, and I tried several fixes without any good.

So I decided to uninstall Ubuntu (booting up on my Windows 7 DVD and format the Ubuntu partition).

After reboot I still got the grub menu, but was later able to get rid of that menu with bcdedit /fixmbr - bcdedit /fixboot -- bcdedit /rebuildbcd.

I even deleted the bootloader, and set up a new one from scratch (and I know I did it right).

Now, I only have a white borderline blinking on a black screen just after BIOS is loaded. Its just blinking and blinking.
I can abort the blinking by pressing Ctrl + Alt and Delete, and the PC restarts.

I have not done any changes after I posted the script report I was told to do.

---

### Post by darkod on 2010-06-14
On the win7 partition you have some file /NST/menu.lst. Short google search says it's probably some NeoGrub, I guess from NeoSmart.

Were you trying to install that? Did you try to use any bootloader except grub2 from ubuntu?

---

### Post by Oneblo on 2010-06-14
To be honest, I don't know.

All I know is that I installed Ubuntu bootloader on my Windows 7 partition. so I guess I overwrite my existing Windows 7 bootloader and installed GRUB instead.

I have been using EasyBCD, maybe that is the problem. But I can't fix it now as I have no access to Windows 7.

---

### Post by darkod on 2010-06-14
And this is exactly why I always recommend to dual boot in the "normal" way, just put grub2 on the MBR and let it dual boot ubuntu and windows.

Don't try too many things out of the ordinary especially if you don't have experience with them. Look at the mess now. :(

I even don't know if the restore of the win7 boot files was or was not supposed to delete EasyBCD too. You restored win7 boot process but EasyBCD files seem still here.

Boot the ubuntu cd in live mode, find in Places your win7 partition and open it. Delete the /NST/menu.lst file.

After that install generic mbr on /dev/sda with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give. Don't do what the warnings will tell you!!! Just execute those two lines of commands.

Restart and check if win7 will boot directly.

---

### Post by Oneblo on 2010-06-14
Thanks, I will try that. 
But does it require a internet connection? I cannot get Ubuntu to connect to wireless in liveCD.

---

### Post by darkod on 2010-06-14
> **Oneblo said:**
> Thanks, I will try that. 
But does it require a internet connection? I cannot get Ubuntu to connect to wireless in liveCD.

Yes it does. Use a wired connection, can you connect it to your router?

PS. Or try if it will work just after removing the file. Doing the lilo commands can be second step if just removing doesn't work.

---

### Post by Oneblo on 2010-06-14
I have connected it to the router now, and I will try toget it working..

---

### Post by Oneblo on 2010-06-14
Wow.. I still can't boot into Windows 7.. "/

---

### Post by darkod on 2010-06-14
> **Oneblo said:**
> Wow.. I still can't boot into Windows 7.. "/

This is only up to win7. Maybe that's why it couldn't boot from grub2 also. It might be that you deleted your ubuntu for nothing, win7 seems to have problems booting itself.

Run again the automatic repair process with the win7 dvd, but run it three times even if it says it fixed everything the first time. It seems it needs three passes.

---

### Post by Oneblo on 2010-06-14
> **darkod said:**
> This is only up to win7. Maybe that's why it couldn't boot from grub2 also. It might be that you deleted your ubuntu for nothing, win7 seems to have problems booting itself.

Run again the automatic repair process with the win7 dvd, but run it three times even if it says it fixed everything the first time. It seems it needs three passes.


Seems like I was not connected to the internet while executing the command. I will try again.

You can't do a startup repair 3 times if it "fixes" it the first time.

---

### Post by lukeiamyourfather on 2010-06-14
For future reference if you want to dual boot with Windows its easier to install the boot loader on the drive with Ubuntu. Then change the boot device in the BIOS to the Ubuntu drive where you can then select either Windows or Ubuntu when booting. If the Ubuntu drive is ever removed then the system will go back to booting from the Windows drive which will have an unmodified boot loader. By the way, the last thing the Ubuntu installer asks is where you want to put the boot loader.

In your current situation either just use GRUB and concentrate on correcting the list so it boots Windows successfully, or try the guides to reinstall the Windows boot loader using the recovery mode on the Windows 7 install disc.

---

### Post by wilee-nilee on 2010-06-14
> **Oneblo said:**
> Seems like I was not connected to the internet while executing the command. I will try again.

You can't do a startup repair 3 times if it "fixes" it the first time.

It is standard to run it 3 times.

---

### Post by Oneblo on 2010-06-14
I have tried tons of fixes now, but nothing seems to be fixing it.

I have used the startup-repair from the Windows 7 disc
Different commands in command prompt

The screen is still black, and a white border is flashing - as you where about to type something in.

---

### Post by wilee-nilee on 2010-06-14
> **Oneblo said:**
> I have tried tons of fixes now, but nothing seems to be fixing it.

I have used the startup-repair from the Windows 7 disc
Different commands in command prompt

The screen is still black, and a white border is flashing - as you where about to type something in.

Are you using the auto repair with the install dvd.

---

### Post by Oneblo on 2010-06-14
Yes. After the boot up I choose "Repair", and then the first option that comes up.

---

### Post by darkod on 2010-06-14
> **lukeiamyourfather said:**
> For future reference if you want to dual boot with Windows its easier to install the boot loader on the drive with Ubuntu. Then change the boot device in the BIOS to the Ubuntu drive where you can then select either Windows or Ubuntu when booting. If the Ubuntu drive is ever removed then the system will go back to booting from the Windows drive which will have an unmodified boot loader.

The OP has a single hdd. How are you supposed to do that?

@Oneblo

A thought crossed my mind. Do you keep the 4GB stick plugged in all this time? Don't tell me you are booting from it by mistake?

It has some syslinux bootloader which might not be working correctly. Is that your ubuntu live usb?

The win7 dvd should at least be able to repair the win7 boot process you would think.

---

### Post by Oneblo on 2010-06-14
I'm booting from a liveCD not USB.
I take out the CD everytime I reboot to check if I fixed it.

---

### Post by wilee-nilee on 2010-06-14
@darkod do you think these commands should work.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by darkod on 2010-06-14
What is that 4GB device /dev/sdb in your results file?
usb stick? memory card? internal small ssd?

---

### Post by Oneblo on 2010-06-14
It was a USB stick, but I've removed it now. That was the stick I transfered the results.txt to this forum.

---

### Post by darkod on 2010-06-14
> **Oneblo said:**
> It was a USB stick, but I've removed it now. That was the stick I transfered the results.txt to this forum.

Try to reboot without it.

---

### Post by lukeiamyourfather on 2010-06-14
> **darkod said:**
> The OP has a single hdd. How are you supposed to do that?

Its not like hard disks are made out of gold. There's a 500GB drive from Seagate for $39.99 with free shipping.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148395](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148395)

Anyway, I'd suggest installing Ubuntu again and focusing on getting GRUB to boot Windows properly if you're not having much luck with the Windows boot loader.

---

### Post by Oneblo on 2010-06-14
I have done that all the times I've rebooted.

---

### Post by Oneblo on 2010-06-14
I'm about to try and install Ubuntu again to see if it fixes the problem.

Where should I install the bootloader? 
I also see that instead of "Windows 7" I get "Windows Vista (Longhorn)" instead in the partition part in the installer.

I get these opetions at the end:

Install bootloader (checked)
hd0
/dev/sda (Western Digital 1TB disk)
/dev/sda1 (Windows Vista/Longhorn (loader) )
/dec/sda5

---

### Post by lukeiamyourfather on 2010-06-14
> **Oneblo said:**
> I'm about to try and install Ubuntu again to see if it fixes the problem.

Where should I install the bootloader?

What disk and partitions are in the system? If its a single disk then install the boot loader to the MBR which is the default option in the installer. If using more than one disk, what's on each disk?

---

### Post by darkod on 2010-06-14
I'm out of ideas.

1. There is a testdisk procedure able to repair boot sector from a backup, but not sure if it will work at this point at all. You can try to do this on partition #1 on disk /dev/sda:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

2. Depending how much data you have on your /dev/sda1 partition, and whether you have too much software to reinstall back, just boot in ubuntu live mode, copy the data to external disk, and reinstall win7.
If you plan to dual boot again don't let it take the whole hdd, then you would have to shrink it immediately.

I am still confused what happened from the start. You said you used the win7 dvd to delete the ubuntu partitions and then repaired the windows bootloader. But in that case you would have unallocated space. You whole hdd is taken by /dev/sda1, like no partitions were deleted.
Unless you also reinstalled win7 but in that case it wouldn't show wubi inside it, it would be brand new win7 install.

---

### Post by Oneblo on 2010-06-14
I deleted Ubuntu partition with the Windows 7 DVD. After boot, I clicked install, then I got to the Window s7 partition editor.


I get these opetions at the end on Ubuntu installation:

Install bootloader (checked)
hd0
/dev/sda (Western Digital 1TB disk)
/dev/sda1 (Windows Vista/Longhorn (loader) )
/dec/sda5

---

### Post by darkod on 2010-06-14
> **Oneblo said:**
> I'm about to try and install Ubuntu again to see if it fixes the problem.

Where should I install the bootloader? 
I also see that instead of "Windows 7" I get "Windows Vista (Longhorn)" instead in the partition part in the installer.



Your win7 is not booting even on its own. In that case there is almost no way grub2 to boot it.

Also, trying to install now requires shrinking the win7 partition so just that you know, you are risking your data without much chance of success.

Win7 partition should usually be resized with the windows Disk Management, not with the ubuntu installer side-by-side option.

---

### Post by Oneblo on 2010-06-14
> **darkod said:**
> Your win7 is not booting even on its own. In that case there is almost no way grub2 to boot it.

Also, trying to install now requires shrinking the win7 partition so just that you know, you are risking your data without much chance of success.

Win7 partition should usually be resized with the windows Disk Management, not with the ubuntu installer side-by-side option.

We can edit the GRUB so it will boot Windows 7, right?

---

### Post by darkod on 2010-06-14
> **Oneblo said:**
> I deleted Ubuntu partition with the Windows 7 DVD. 

Do you understand at all what I am asking you? Deleting a partition leaves unallocated space. You don't have any.

Did you resize your win7 partition after that to take the whole space? Where did the unallocated space go?

If you were resizing win7 that might have corrupted it.

---

### Post by Oneblo on 2010-06-14
> **darkod said:**
> Do you understand at all what I am asking you? Deleting a partition leaves unallocated space. You don't have any.

Did you resize your win7 partition after that to take the whole space? Where did the unallocated space go?

If you were resizing win7 that might have corrupted it.

I expanded the Windows 7 partition.

---

### Post by darkod on 2010-06-14
> **Oneblo said:**
> We can edit the GRUB so it will boot Windows 7, right?

JESUS MAN, NOT IF IT DOESN'T BOOT BY ITSELF!!!! What am I talking about here.

Grub2 only passes the booting to the windows boot files. If the windows process itself doesn't work, forget about grub2 booting windows. Get it?

You will be just risking your data, if you have any on the hdd. At least boot in live mode first and copy your data.

Then do what ever you want.

---

### Post by lukeiamyourfather on 2010-06-14
> **Oneblo said:**
> I deleted Ubuntu partition with the Windows 7 DVD. After boot, I clicked install, then I got to the Window s7 partition editor.


I get these opetions at the end on Ubuntu installation:

Install bootloader (checked)
hd0
/dev/sda (Western Digital 1TB disk)
/dev/sda1 (Windows Vista/Longhorn (loader) )
/dec/sda5

You will want to install the boot loader to /dev/sda which is the MBR of the first and only hard disk.

---

### Post by lukeiamyourfather on 2010-06-14
The posts by darkod bring up a good point. If the Windows partition was hosed by something else, then it won't boot regardless of what boot loader is used. My suggestions are assuming the Windows partition isn't hosed.

---

### Post by Oneblo on 2010-06-14
So, is there any way to fix this ****, or do I have to do a clean install?

If I do a clean install, but Windows make a Windows.old folder?

---

### Post by darkod on 2010-06-14
> **Oneblo said:**
> So, is there any way to fix this ****, or do I have to do a clean install?

If I do a clean install, but Windows make a Windows.old folder?

As I said, at this point after trying everything we did, maybe a reinstall is the way to go. Boot in ubuntu live mode, copy your data from the partition, and then you are free to reinstall.
Of course, you will need to install all your programs again. If that's too much bother, don't reinstall but I can't really figure out a solution to this.

---

