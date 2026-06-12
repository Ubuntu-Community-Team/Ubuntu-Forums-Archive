---
title: "Windows 7 Wont boot"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by r3k0iL on 2012-02-16
So, im completely new to ubuntu and I just wanted to try it out. So i set up a dual boot with windows 7 and ubuntu, and ubuntu works fine. Yet, when i try to boot windows 7, it gives me the error "unknown filesystem" with grub rescue under that. I don't know what to do..please help.
If it helps i did install ubuntu before, but it had a grub problem so i did a reinstall, and thats basically where i am now. Again, please help and thanks for any input.

---

### Post by Marcelo Ruiz on 2012-02-16
Two things to do:

First, load into Ubuntu and run in a terminal:

```
sudo update-grub
```

See if it detects the partitions where Windows is.

If it does, then reboot and try to load Windows.

If this doesn't work, try to use the Windows Recovery DVD to detect and repair startup problems. Sometimes that does the trick!

Good Luck!

---

### Post by r3k0iL on 2012-02-16
Ok so I tried the first option, it did detect windows 7 (windows 7  (loader) on /dev/sda2). Rebooted and tried windows 7, but still unknown filesystem. 
So quick question before i try your second option, will it delete the ubuntu partition in any way? Because i spent a few hours customizing ubuntu. 
Thanks for responding so fast

---

### Post by f07sa on 2012-02-16
I have had this problem a couple of times in the past, I will vouch for Marcelo's idea personally when you perform the detect and repair it should'nt do any harm just make sure you don't rush and if there is anything you don't understand come back and ask.

---

### Post by YannBuntu on 2012-02-16
Please could you answer this request: [http://ubuntuforums.org/showpost.php?p=11136267&postcount=1](http://ubuntuforums.org/showpost.php?p=11136267&postcount=1)

This will help us understand your issue.

---

### Post by Rebelli0us on 2012-02-16
> **r3k0iL said:**
> So, **im completely new to ubuntu** and I just wanted to try it out. So i set up a dual boot with windows 7 and ubuntu, and ubuntu works fine. Yet, when i try to boot windows 7, it gives me the error "unknown filesystem" with grub rescue under that. I don't know what to do..please help.
If it helps i did install ubuntu before, but it had a grub problem so i did a reinstall, and thats basically where i am now. Again, please help and thanks for any input.

If you're new there is a much safer option for running Win 7:

In Ubuntu Software Center type "virtualbox", then select "virtualbox OSE" and click "install". Then, using VirtualBox install Windows 7 as a virtual machine. There is no need to screw around with partitions and risk trashing your computer.

The end result looks like this, you'll be running Linux and Windows **simultaneously**. Notice my taskbar, I'm running Ubuntu, Windows 2000 and Windows 7.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212449&stc=1&d=1328903048[/IMG]

---

### Post by r3k0iL on 2012-02-16
@YannBuntu heres my boot info
[http://paste.ubuntu.com/845149/](http://paste.ubuntu.com/845149/)

@Rebelli0us, creating a virtual system would work, but i need to access all of my stuff on my windows 7 (videos,music,applications). 

I'm probably going to do what Marcelo told me to do (recovery dvd) on the weekend. I'll let you guys know how that goes.

---

### Post by oldfred on 2012-02-16
Stealing Yann's thunder.:)

He posted a how to to fix your issue & I have an older one.

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
or:
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

---

### Post by r3k0iL on 2012-02-16
Okay, so Oldfred your first link seems to be broken so i followed the instructions in the second step. In the sixth step since i didnt have the BackupBS it told me to do the recovery CD to repair my boot. So i did that, and now when i power on the computer it now gives me "no such partition" grub rescue. Even when i try to boot from the windows 7 CD again, it gives me press any key to boot from CD or DVD.......error: no such partition. 
This....is quite frustrating. So again, help?

---

### Post by oldfred on 2012-02-16
Often the repair will not work as it does not even see a NTFS partition with grub installed to the PBR or boot sector. You can use the testdisk to create a new NTFS partition boot sector, but that is not fully fixed. On testdisk page I linked to, see the rebuild BS to rebuild the NTFS boot sector.

Then with fixBoot and chkdsk (each depends on the other) run several times should fix it. Boot flag will have to be on that partition which it was in your boot info script.

---

### Post by r3k0iL on 2012-02-16
Well, now i really hate myself. So before Oldfred posted his most recent post i searched up and found the boot repair option (the one at source forge), so i burned it to a disk and booted from that. The first time around it didn't work to fix anything, so in my rage i chose sda3, hoping that would do *something[I]*[/I], but now........when i boot up it gives me "bootmgr is missing press ctrl+alt_delete to restart", i tried to put in the windows 7 CD, but that just gives me "press any key to boot from CD or DVD" followed by the bootmgr is missing dialogue, not allowing me to do anything. Im really hating myself for making the problem worse. So thank you for sticking with me.

---

### Post by oldfred on 2012-02-17
From the Windows 7 DVD or repairCD you should be able to get to a repair screen. But I think you have to run the rebuild BootSector from testdisk so Windows sees a NTFS partition. Without that Windows does not know it is a Windows partition.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If you run the fixMBR you can confirm that Windows will boot on its own again, but will have to reinstall grub2 to the MBR to boot into Ubuntu.


How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by r3k0iL on 2012-02-17
Booting from testdisk gives me this error "error 0400 reading sector 180122 initial menu has no label entries! boot:" :(

---

### Post by r3k0iL on 2012-02-17
Sigh, if im not able to correct the problem by the end of the weekend i think i might just cut my losses. Is there any way to just erase all the memory on the hard drive so the computer treats it as a new hd, (then install windows 7 and start over)?

---

### Post by oldfred on 2012-02-17
Are you repairing sda2, sector 180122 looks like it is in sda1?? 

And sda1 is the recovery partition so it may not be a standard partition that testdisk would normally repair.

---

### Post by r3k0iL on 2012-02-17
Well, im not quite sure which part im repairing, the first message when booting up gives me the "error reading etc.", it doesnt give me a choice where to repair. 
Im not that tech savy, so yeah.....-.-"
Also before the error it says"isolinux 4.04 2011-4-18....peter anvin et al", if that helps at all....

---

### Post by r3k0iL on 2012-02-18
Well, i just ran the recovery disk and ran the repair boot, and guess what it worked! Windows booted up! 
So i guess what i want to know now is what to do now? I want to erase ubuntu from my computer, and make it like it was before i wanted to install ubuntu(perhaps ill try to install later :/) 
Thanks to everyone who posted here, especially Oldfred.

---

### Post by drifter2502 on 2012-02-18
Before you go...unless you have already, I have used super grub disc a couple of times in circumstances similar to your problem. SGD should find your windows side and correct the boot issue. After all both systems are there and SGD should find both and correct the problem.  it is easy to use.[http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html](http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html)

---

### Post by YannBuntu on 2012-02-20
> **r3k0iL said:**
> I want to erase ubuntu from my computer, and make it like it was before i wanted to install ubuntu(perhaps ill try to install later :/) 

Just use gParted or the Disk-Utility from a Ubuntu live-CD to delete your old Ubuntu partitions, and then format the empty space into NTFS (so that Windows can use it).

---

