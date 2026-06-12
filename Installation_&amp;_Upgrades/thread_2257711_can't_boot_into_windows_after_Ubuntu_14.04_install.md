---
title: "can't boot into windows after Ubuntu 14.04 install"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by mnosyke on 2014-12-22
hi all and thanks for having me. i just switched to ubuntu because i am not feeling windows any more. i REALLY REALLY NEED HELP GUYS.  i accidentally installed ubuntu in legacy mode and now cant find my windows 8 operating system. please what do i do to resolve this since all my info is in windows. when i boot in legacy, i see only ubuntu. when i boot in efi, it says operating system not found. please how do i fix the boot for windows 8.......thank to all u nice wizards!!!!!!!!!!!!!!!

---

### Post by mnosyke on 2014-12-22
[COLOR=#000000]hi all and thanks for having me. i just switched to ubuntu because i am not feeling windows any more. i REALLY REALLY NEED HELP GUYS. i accidentally installed ubuntu in legacy mode and now cant find my windows 8 operating system. please what do i do to resolve this since all my info is in windows. when i boot in legacy, i see only ubuntu. when i boot in efi, it says operating system not found. please how do i fix the boot for windows 8.......thank to all u nice wizards!!!!!!!!!!!!!!![/COLOR]

---

### Post by QIII on 2014-12-22
Threads merged and moved to Installation & Upgrades.

Please do not start multiple threads for the same issue in multiple locations.  It dilutes the community's efforts to help and causes confusion.

---

### Post by oldfred on 2014-12-22
We need to see details, and do not run any autofix until someone has reviewed your summary report.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Did you turn off secure boot, and fast boot or always on hibernation in Windows before install?

And I know horse has left barn so a bit late to close barn door, but we always recommend full backups before major system changes. And hard drives do fail, so if any data is valuable you should have good backup procedures, And a separate Windows repair CD or flash drive to fix things. 


 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by mnosyke on 2014-12-22
thanks.for replying. here is my link.    [http://paste.ubuntu.com/9600514/](http://paste.ubuntu.com/9600514/) . i kindly await your reply. uasked me this question "[COLOR=#000000]Did you turn off secure boot, and fast boot or always on hibernation in Windows before install?  . 
my answer- i was never on hybernation  and as i recall, my secure boot was off but i know that i installed in legacy mode. this i know for sure.....[/COLOR]

---

### Post by mnosyke on 2014-12-22
..... i hope i provided all the info necessary....... as for thread tools above, i dont think they can help me because they all require me to be able to boot in windows which i cant do. my system only boot into ubuntu and will not find windows. i have switched between legacy and eufi  and still no luck.

---

### Post by yancek on 2014-12-22
I don't know how you managed to do this or what option you selected during the install but, your bootinfo report shows no sign of windows, not even a recovery partition.  There are numerous detailed tutorials on installing Linux/Ubuntu such as the one below.  Might have been a good idea to read a few before beginning.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2014-12-22
It seems system may have been UEFI, and Windows only boots in UEFI from gpt partitioned drive.

But as yancek has pointed out, you have nothing but Linux in BIOS boot mode on a MBR partitioned drive.

I hope you have good backups.

If no backup and you really have data you want to try to recover STOP using system. Every bit of data you write is overwriting more of old data. And you will not recover a working system nor all data. But Linux is not large, writes to entire drive where Windows writes mostly to beginning of drive so some data may be recoveryable. Long detailed process and you need another drive to copy data into. That drive should have been where you were copying data anyway.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Testdisk is the first thing to try. If deeper search can find files then you want to copy those immediately to another drive. 

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

If testdisk fails, you can use tools that scan drive for anything that looks like a file. I have used it and on a smaller drive it took overnight. And it recovered even my deleted copies and does not recover file names just extensions. So I had multiple copies of some files and had to compare each to my last backup. Weeks of works but I did get some data back. And now have better backup procedures.


 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

I think these require you to move drive to a working Windows system, but may work better at recoverying NTFS data.

 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by mnosyke on 2014-12-23
thanks guys. right now i honestly dont need my files from windows, i just need to be able to boot into windows even if it means restoring to factory. i just need to have access to windows since most things i do involve using windows. please tell me how i can achieve this. 
QUESTION: WHAT IF I DELETE UBUNTU AND RE INSTALL IN UEFI MODE, DO YOU THINK IT WILL RECOGNIZE WINDOWS AGAIN?. REMEMBER THAT I INSTALLED UBUNTU IN LEGACY. ITS WORTHY TO NOTE THAT BEFORE, I HAD  ubuntu and windows together in this computer. itSjust that i upgraded to 14.10 via the onscreen message i received but after the install ubuntu wont load so i deleted ubuntu and re installed my 14.4 mistakenly through legacy. i THINK I MAY HAVE MADE A MISTAKE WHEN DOING THE PARTITION PHASE IN UBUNTU INSTALL. PLEASE HELP

---

### Post by fantab on 2014-12-23
There is no Windows 8 on your Hard Disk. Its gone.
Follow oldfred's post to recover any important data.

Factory restore, also won't work. As restore works from, usually, a dedicated partition on HDD. There is no such partition on you HDD at present.
See below:
```

Model: ATA WDC WD5000LPVT-2 (scsi)
**Disk /dev/sda: 500GB**
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  496GB  496GB   primary   ext4            boot
2      496GB   500GB  4077MB  extended
5      496GB   500GB  4077MB  logical   linux-swap(v1)

```

Windows partitions will show NTFS as file system.

Try the Partition recovery tools, which are bootable and see if you can re-claim the NTFS partitions.
100% recovery may not be possible.

Alternatively, you can contact the machine's vendor, they may provide you with a Win8 Restore Disc. Or you may have to install from a retail DVD and hope your 'key' works.

---

### Post by oldfred on 2014-12-23
I think your product key only works with the OEM version.

But if using testdisk you can restore the NTFS partitions, including one testdisk will not find as it is empty - msftres, which is usually 128MB & just before the main install, but after the efi partition.    Testdisk may include the 128MB inside the main partition or may show empty space which then you can add the msftres with gparted and correct flag.

Then you may be able to run this if it sees enough of Windows to think the repair is all you need. It is not a full install.
Windows 8 has both a Refresh and a Reset option. To find out the details of both, and to decide which best to use, you should check in with the Windows 8 forum:
 [http://www.eightforums.com](http://www.eightforums.com). 
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

      Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
      
These are the minimum you need to recover. You probably have at least one vendor recovery, but if any Linux data was written into it, it will not be usable.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

---

### Post by mnosyke on 2015-01-04
SOLVED     SOLVED    SOLVED    SOLVED    SOLVED


thanks again. you guys are so awesome. so as i said before, i accidentally clicked on my ntsf drive when installing ubuntu and lost my windows. when i rebooted it will only show ubuntu bootloader. i just couldnt find a way to recover the drive so i came to this forum and got some useful advices. well, i finally tried to re install my windows but kept getting the error message telling me that there is no ntsf present. after getting my reCocvery CD from acer,  this is what i did

PLEASE REMEMBER THAT ALTHOUGH I HAD UBUNTU IN THE COMPUTER I  WANTED TO WIPE EVERYTHING AND REINSTALL ALL 

1-  i booted into ubuntu live through usb,
2- i started up gparted and reformated my drive to gpt from mbr since windows can only recognize gpt. 
3- this made me lose everything even the installed ubuntu
( when i tried to install my windows through the recovery cd, i kept getting the message that i should restart using uefi mode, when i did it will tell me to restart using legacy. it was just frustrating!!!!!!!!!!!!!!!!
4- i then rebooted my computer into windows live boot through usb drive.
5- next i started diskpart through windows terminal and cleaned the drive.
6- i then rebooted and tried the windows install again and THIS TIME IT WORKED AND I RE INSTALLED MY WINDOWS 8, THEN I REINSTALLED UBUNTU.


------------------------------------------------------------------------------

1- for ubuntu live disk-  just download ubuntu 14.4, ubuntu live or any other ubuntu version that conatains the " try ubuntu before installing ubuntu"     [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

2- for installing windows live usb go to [http://download.cnet.com/Active-Boot-Disk/3000-2094_4-10450840.html](http://download.cnet.com/Active-Boot-Disk/3000-2094_4-10450840.html)    INSTALL INTO YOUR COMPUTER, FORMAT YOUR USB IN NTFS MODE AND RUN PROGRAM, IT WILL DETECT YOUR USB AND WHEN ASKED WHAT KIND OF SYSTEM, CHOOSE NTFS.   you must install active boot into a running windows computer because its that computers info that it will use to make the live usb. i used my old windows 7 computer to accomplish this

3- for how to clean windows drive go to [https://www.youtube.com/watch?v=g2iFj56NDg8](https://www.youtube.com/watch?v=g2iFj56NDg8)    (if you want to clean your disk just boot into windows live disk using active@boot disk  you created  and run the terminal, then follow the video instructions .

4- for using gparted to convert your disk from ubuntu mbr to windows gpt, go to    [https://www.youtube.com/watch?v=4LigMbTSlhQ](https://www.youtube.com/watch?v=4LigMbTSlhQ)   (please note- by doing this u will lose all data on entire disk. use only if you want to convert the entire disk from mbr to gpt.   GPARTED COMES WITH THE UBUNTU LIVE ALREADY!!!! SO JUST SEARCH AND LAUNCH ONCE YOU ARE DONE BOOTING INTO UBUNTU LIVE.

YOU NEED AT LEAST A 4 GIG USB DRIVE TO ACCOMPLISH ALL THIS. 2 usbs are better so u can install active boot in one and ubuntu in the other. if you have only one then install ubuntu first, convert to gpt then wipe the usb and install active boot. 
 GOOD LUCK !!!!!!!



BONUS!!-----  WANT TO RUN ANDROID OPERATING SYSTEM TOO IN YOUR WINDOWS?    THEN GO HERE  [http://windroy.en.softonic.com/](http://windroy.en.softonic.com/)



PLEASE FEEL FREE TO ASK ME ANY QUESTIONS IF YOU FIND YOURSELF IN THIS TROUBLE. I WOULD HAVE LOVED TO BE MORE DETAILED BUT AM AT WORK. 

thanks ubuntu team. i love the system and just installed kubuntu which i love even more.

---

### Post by mörgæs on 2015-01-04
Good, please read the footnote in Oldfred's post.

---

### Post by mnosyke on 2015-01-04
thanks Mod, you guys are the best!!!!

---

