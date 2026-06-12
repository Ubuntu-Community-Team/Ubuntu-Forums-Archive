---
title: "How do you install ubuntu on an ssd drive and maintain windows caching?"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by swagz101 on 2013-03-25
Hello,

I wanted to install ubuntu on my laptop. It's a lenovo u310 and it has a 32 gb ssd drive for caching windows and a 500 gb hard drive. 

I want to know if its possible to partition the sdd drive and install ubuntu on about 10 gb of it and keep the rest of the ssd for the windows caching process. Im a college student and we use windows, so I must keep it. And I want it to run as fast as possible, can't really afford the loss in productivity. But I also want to install ubuntu though and want it to run as fast as possible.

Is it possible to do this?

Specs
-Lenovo u310
-Core i5 ulv 1.7 ghz
-500 gb hdd plus 32 gb ssd
-Windows 7

---

### Post by darkod on 2013-03-25
I'm not sure, but in any case this would be a windows question, not ubuntu. You might have better luck posting it on the windows forums too. You need to know if the caching process (is it Intel RST?) can use partition instead of the whole disk. If it can, you will split it into two partitions and use one for caching the other for ubuntu.

If it can't, it doesn't look like you can use it the way you intend.

---

### Post by swagz101 on 2013-03-25
yea it is rst. okay i guess ill just check elsewhere thanks.

---

### Post by oldfred on 2013-03-25
Some info on Intel SRT.
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by swagz101 on 2013-03-27
As much as I want to install ubuntu on an ssd. It looks to risky. I have very important applications installed on my windows system that i can't afford loosing. I guess I'll have to settle for a slower ubuntu. Do you know if the wubi installation will work with the various raid, irst, configurations?

---

### Post by oldfred on 2013-03-27
A few Windows 7 systems were installed in UEFI mode with gpt partitioning. Wubi does not work with gpt partitioning. If you have BIOS/MBR it should work.

       HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)


 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by pfeiffep on 2013-03-27
I have 2 internal drives, 1 SSD for Win7, and 1 HDD for Ubuntu. Grub is installed on SSD, while Ubuntu 12.10 and 13.04 (daily) is installed on HDD. I haven't run benchmarks but I believe that Ubuntu from HDD is pretty much as fast as Win 7 from SDD. 
If you decide on partitioning HDD for Ubuntu keep a portion as NTFS :p so you can easily share data between the 2 OSes.

---

### Post by darkod on 2013-03-27
> **swagz101 said:**
> As much as I want to install ubuntu on an ssd. It looks to risky. I have very important applications installed on my windows system that i can't afford loosing. I guess I'll have to settle for a slower ubuntu. Do you know if the wubi installation will work with the various raid, irst, configurations?

What looks risky? The ssd is only for caching, it doesn't hold your data in most cases. You can "break" the RST configuration and use it for ubuntu. Windows will keep working and your data will still be there. You will only lose the caching capability. It's up to you to decide if it's worth losing it in return of having ubuntu working from ssd.

---

### Post by swagz101 on 2013-03-27
darkod, how would I do what you just said? (If it is possible do what you just said, im more than willing to try it, as long as my windows partition is not broken)

also can ubuntu run with the sata controller set as Raid? Because if I set it to AHCI. My windows partition will not boot.

Additionally, the reason I said it was risky, was because when i booted ubuntu 12.04 from my usb drive and tried to install it, no drives came up. From what i read, in order for them to show, you must disable raid. if i disable raid, i cannot boot into windows.

Additional info

-the only thing the installer will let me do is install the bootloader in /dev/sda

---

### Post by darkod on 2013-03-27
I don't have RST so I can't be 100% sure, you will need to investigate a little bit. But in general it goes like this:
1. In windows disable the RST.
2. In BIOS disable the RST also. You might need to change the sata mode to AHCI from RAID.
3. Boot with the ubuntu cd and delete the meta data from both disks with:
```
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb
```

That will make the disks completely separate. After that simply install ubuntu to the ssd and that's it.

Oldfred had many links about RST, you might have more details in some of his links above.

And make a full backup of your windows + data before you start this, just in case.

---

### Post by swagz101 on 2013-03-27
okay I will try it, made a backup already.

---

### Post by swagz101 on 2013-03-27
Okay i installed ubuntu, and windows is still intact. there is however one problem, when I turn on my computer, it boots straight into windows.

btw I partition the ssd, and gave ubuntu 10 gb. I installed the / folder onto the ssd, swap on 4gb hdd partition, and the /home folder on 100gb of the hard drive.

how do I get the grub menu to appear? (thanks for your help btw, I really appreciate it)

---

### Post by darkod on 2013-03-27
It sounds like grub2 didn't install correctly, or it's on the other disk. What did you select as bootloader destination?

Boot the cd in live mode, and post the output of:
sudo parted -l (small L)

---

### Post by swagz101 on 2013-03-27
ubuntu@ubuntu:~$ sudo parted -l 
Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8589MB  8588MB  primary
 2      8589MB  19.2GB  10.6GB  primary  ext4         boot


Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  211MB  210MB   primary   ntfs            boot
 2      211MB   238GB  238GB   primary   ntfs
 3      238GB   479GB  241GB   extended                  lba
 6      238GB   242GB  3999MB  logical   linux-swap(v1)
 7      242GB   342GB  100GB   logical   ext4
 5      447GB   479GB  32.6GB  logical   ntfs
 4      479GB   500GB  20.8GB  primary   ntfs            diag


Model: USB2.0 Flash Disk (scsi)
Disk /dev/sdc: 1061MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1061MB  1061MB  fat16

---

### Post by swagz101 on 2013-03-27
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8589MB  8588MB  primary
 2      8589MB  19.2GB  10.6GB  primary  ext4         boot


Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  211MB  210MB   primary   ntfs            boot
 2      211MB   238GB  238GB   primary   ntfs
 3      238GB   479GB  241GB   extended                  lba
 6      238GB   242GB  3999MB  logical   linux-swap(v1)
 7      242GB   342GB  100GB   logical   ext4
 5      447GB   479GB  32.6GB  logical   ntfs
 4      479GB   500GB  20.8GB  primary   ntfs            diag


Model: USB2.0 Flash Disk (scsi)
Disk /dev/sdc: 1061MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1061MB  1061MB  fat16

---

### Post by darkod on 2013-03-27
OK, according to what you said, sda2 is the root partition. From live mode try adding grub2 to the MBR of the disk with:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Make sure you boot from the ssd in bios. If it doesn't let you boot from the ssd because it was only meant to be a caching disk, you might need to install grub2 to /dev/sdb.

If this doesn't work, you might need to do a full purge reinstall of grub2, the longer procedure. Try the above short procedure first.

---

### Post by swagz101 on 2013-03-28
works perfectly now I can dual boot thanks. It turns out that all I had to do was make sure the ssd partition was the first option to boot off of in the menu. 

Thanks for the help, I appreciate it alot!

---

### Post by darkod on 2013-03-28
No problem, enjoy it now. :)

---

### Post by swagz101 on 2013-04-06
I figured out that after you install ubuntu, you can in fact re-enable intel rapid storage technology. 

so heres a summary of what i did for anyone who might be trying to do the same thing. 

**1.) first made a back up of my windows system and created a ubuntu 12.04 live usb **
  
  *Also from windows, i disable all the intel processes by hitting the start button, typing in msconfig and hitting enter, then i clicked the services tab and searched for any intel  irst related processes and clicked the check boxes next to them to disable it. Also, from windows, I used the disk partition-er to delete a hibernate partition on my ssd leaving the ssd as only "unallocated space", (idk if it will be there for anyone else, and the hibernate feature wasn't even working so i wonder what it was there for)*

**2.) then i turned of computer and entered the bios, then turned off all the intel smart response options, changed the sata controller from Raid to ACHI, and turned off  uefi (secure boot).**

[B]3.) also in the bios i set the usb drive to boot first, then restarted my pc and booted from the live usb
[/B]
[B]4.) when asked to install ubuntu, i choose instead to try it instead
[/B]
[B]5.) i opened the terminal and put the following line of code: 
[/B]
    sudo dmraid -Er /dev/sda
    sudo dmraid -Er /dev/sdb

**6.) I then ran the installer and installed the root folder  ( /  )   on 10 gb of the ssd, i installed the home folder ( /home) on 100 gb of my hard drive, and I also made a 4gb swap  partiton from the hdd**
     (you have to leave 18.6 gb of space on your ssd to be able to cache windows)

**7.) After the installation was complete, i restarted the computer and entered the bios where I set the ssd as the first boot option. So now i was dual booting with no caching for windows**

[B]8.) also while in the bios, i re-enabled all that i disabled except for uefi secure boot.
9.) then i booted into windows and re-enabled all the irst processes[/B]

**10.) then i went to the following where i found out info on how to setup ssd caching and followed it:**
 
[http://www.overclock.net/t/1227655/how-to-set-up-intel-smart-response-technology-ssd-caching](http://www.overclock.net/t/1227655/how-to-set-up-intel-smart-response-technology-ssd-caching)
 initially i had problems finding the irst software they were talking about, but eventually i found it here: [http://downloadmirror.intel.com/21730/a08/iata_cd.exe](http://downloadmirror.intel.com/21730/a08/iata_cd.exe)

when installing the program, you have to hit a check button that ask for you to install an intel control center.

(make sure when using the irst software that you specify to the program to use part of instead all of the ssd to cache the main hard drive)

and just like that, i now have dual booting between ubuntu and windows with both of the os's using the ssd for better performance.

---

### Post by orioles_fan on 2013-08-05
Has anyone else tried the steps above and had good results? I also have the Lenovo U310 Touch and it came with Windows 8 and the SSD as a cache drive. I really want to get Ubuntu running on this thing but I'd rather not destroy my Windows OS in the process. If the above is correct, then it would be the first time I've seen someone able to properly install Ubuntu on the U310 without issues. Nearly everything I've read online, the user either ends up having to completely remove Windows 8, reinstall Windows 8, and just boots to a black screen. I have too much professional software on the Windows side to warrant completely reformatting everything.

---

### Post by riccardosl45 on 2014-02-19
Hi, to install ubuntu I did these commands

sudo dmraid -Er /dev/sda

now windows is not able too boot, how to add again dmraid to my sata disk?

---

### Post by oldfred on 2014-02-19
You should just need to turn Intel SRT back on in UEFI.
But that may not be why Windows does not boot. Did you also run the backup & rename for buggy UEFI with Boot-Repair. Best to undo that if you did.

---

### Post by riccardosl45 on 2014-02-21
> **oldfred said:**
> You should just need to turn Intel SRT back on in UEFI.
But that may not be why Windows does not boot. Did you also run the backup & rename for buggy UEFI with Boot-Repair. Best to undo that if you did.

No I was not able to use the command

efibootmgr

It's not working

---

