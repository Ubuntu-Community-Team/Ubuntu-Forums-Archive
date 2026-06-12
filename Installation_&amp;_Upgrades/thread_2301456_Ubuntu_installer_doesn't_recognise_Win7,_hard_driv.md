---
title: "Ubuntu installer doesn't recognise Win7, hard drive corrupted"
date: 2015-11-02
forum: Installation &amp; Upgrades
---

### Post by liang4 on 2015-11-02
Hi Everyone,

I tried to install Ubuntu(14.04.3 LTS) using USB last week. 
But the installer failed to detect Win7(32 bit). 
Then I mistakenly click "erase disk and install Ubuntu". After around 5 seconds I hit Install button, some error happened. I have to press start button on computer to shut it down.

As the consequence, my hard drive is corrupted. 
Then I tried to use another computer to read files in it. I put it in enclosure, and plunged in USB of another computer(Win7), the hard drive didn't even show up in "Computer", just a USB icon at the bottom of screen. In the hard drive management screen, it showed as only one GPT protected partition of 500GB.
Then I installed Ubuntu in another hard drive successfully. I tried to read data from the corrupted hard drive using the same enclosure. The hard drive didn't show up either. 

I read several related topics on this forum, seems it is related to GPT or MBR partition. 
But still don't know how could I locate the problem.

Do you guys have any idea how could I locate problem and how could I recover it?

I'm new to Ubuntu. I should have backup the data at first. Now I'm totally upset. :(
Any help is greatly appreciated.

Thanks

---

### Post by yancek on 2015-11-02
> But the installer failed to detect Win7(32 bit). 

Several reasons for that  and the most common one is there is no unallocated space or you were using MBR partitioning and windows was already using four primary partitions.
Can you boot the Ubuntu install usb on the computer in question, open a terminal and run the following command and post the output.

```
sudo parted -l
```

Lower Case Letter L in the command.  It would be useful if you knew what the error was you got before restarting.

---

### Post by liang4 on 2015-11-02
Hi yancek,

Thanks a lot for replying. 
Here is the output of your command:

[I]Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  78.9GB  78.9GB  primary   ext2            boot
 2      78.9GB  320GB   241GB   extended                  lba
 5      78.9GB  158GB   78.9GB  logical   linux-swap(v1)
 6      158GB   237GB   78.9GB  logical   ntfs
 7      237GB   320GB   83.5GB  logical   ntfs


Model: WDC WD50 00BPVT-00HXZT3 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  ntfs
 2      538MB   794MB  256MB
 3      794MB   500GB  499GB[/I]

But I forgot the error I got before I restart.  :(
I was panic when I mistakenly click erase the entire drive. So I rushed. I wanted to stop it from formatting.

Please help me have a look. I will also try to find some other methods to figure out the problem.

Thanks

---

### Post by liang4 on 2015-11-02
I also run command "sudo gdisk -l /dev/sdb"
Hope this information is helpful.

Here is the output:[I]
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  **MBR: protective**
  BSD: not present
  APM: not present
 ** GPT: present**

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 44F98981-2612-4E7B-9B59-43B6430CDE8B
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 4077 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   8300  
   2         1050624         1550335   244.0 MiB   8300  
   3         1550336       976771071   465.0 GiB   FFFF [/I]

---

### Post by yancek on 2015-11-02
Which drive do you have windows 7 on?  The output you posted for the first drive shows to windows partitions, both on logical partitions.  You have one primary partition with Linux and a second partition is used as an Extended partition.  Windows needs it's boot files on a primary partition.  The second drive has the first partition shown as ntfs and the other two, both primary don't show a filesystem type?  The first drive is MBR and the second is GPT.  I'm not familiar with GPT so I don't know if that is all or part of the problem.

It might be useful to google "boot repair Ubuntu", go to the site and download and run it selecting the option to Create BootInfo Summary.  You will need to use your Ubuntu installation medium for that.  Post the output or a link to it here.

One other thing, if you get this repaired and want to try the install again, make sure you select the manual (Something Else) option when you start the installer.  If you don't see the windows partitions at the Installation Type window, stop there is some other problem.

---

### Post by liang4 on 2015-11-02
Hi yancek,

Now my computer is running Ubuntu perfectly in the first drive. 
The second drive mentioned above, which is *500GB WDC WD50 00BPVT-00HXZT3 *is the drive where I have problem. 
It originally has Win7. But after the failure of Ubuntu installation, Win7 is corrupted, and the partitions cannot be recognised by either Ubuntu or Windows. 
In windows drive management, it shows as 500GB protected drive, in Ubuntu it doesn't show up in UI.

I'm thinking, is it possible that when I install Ubuntu, the installation messed up the partition table? replace MBR with GPT or something? 
Because I think the partition should be MBR in my Win7 or MBR&GPT hybrid, then Ubuntu think it is GPT somehow, then it cleared partition table and tried to format the entire drive.

And I'm trying to install using "Something else" again, to see if I get some luck.

Thanks a lot

---

### Post by liang4 on 2015-11-02
I tried to reinstall Ubuntu in the corrupted drive, still no luck.  :(  
And I also tried to boot from it, I got "PXE- E61 Media test failure, check cable", then computer went to the working drive.

---

### Post by Bucky Ball on 2015-11-02
Did you boot into Windows and switch off hibernation prior to installing Ubuntu? If not, that could be your problem. If the Win partition was hibernated, Ubuntu wouldn't have seen it, or couldn't identify it, and that leaves you where you are now. The partition is still hibernated and so Ubuntu can't add it to the grub.

---

### Post by liang4 on 2015-11-02
Hi, 

Thanks for helping.

I didn't switch off hibernation. 
This is my second time installing Ubuntu dual boot. 
Last time was three years ago. I used CD. That time went smoothly. 
So I didn't give much thought this time. 
My carelessness leads me to this situation.  :(

Could you let me know how to confirm if it is hibernation problem?

Thanks

---

### Post by Bucky Ball on 2015-11-02
If you didn't switch off hibernation, then a world of trouble can ensue. Three years ago, you were possibly booting with a non-UEFI system? I can't confirm it, but if you:

a) had Windows installed in UEFI and installed Ubuntu in BIOS mode;
b) didn't switch hibernation off in Windows prior to installing Ubuntu;

... then one or both of these things I would rate highly as being the source of your issues.

---

### Post by liang4 on 2015-11-03
Hi Bucky,

I will try to find out whether my Win7 is UEFI or BIOS system. 
I will provide you more information. 

Please wait for a while and help me investigate later.  

Thanks

---

### Post by Bucky Ball on 2015-11-03
Here's a clue. If Win7 was installed on the machine when you bought it new, there is a 99.9% chance it is installed in UEFI. 

Just boot to the BIOS and have a look.

---

### Post by liang4 on 2015-11-03
Sure. I will boot to BIOS and post the output this evening.

---

### Post by oldfred on 2015-11-03
Bucky:
If Windows 7 it probably is BIOS/MBR. Only a few systems just before Windows 8 came out seemed to have Windows 7 in UEFI boot mode on gpt partitioned drives.
And many newer systems with Windows 7 pre-installed in BIOS mode were still UEFI systems, just using CSM/BIOS. 
So depending on how you boot Ubuntu installer, will be how it installs.

Or if system is a bit newer, but still Windows in BIOS/MBR and OP said to erase entire drive, first thing it did was erase MBR partitions and create new gpt partitions.

liang4
I might try testdisk in MBR, or if that does not work then with gpt as partitions to scan for.
       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Bucky Ball on 2015-11-03
> **oldfred said:**
> Bucky:
If Windows 7 it probably is BIOS/MBR. Only a few systems just before Windows 8 came out seemed to have Windows 7 in UEFI boot mode on gpt partitioned drives.
And many newer systems with Windows 7 pre-installed in BIOS mode were still UEFI systems, just using CSM/BIOS.

Ah, tnx. Explains my misconception. :)

---

### Post by liang4 on 2015-11-03
Hi oldfred,

Thanks a lot for advising.
 
I used testdisk in Windows. 
It detected two hard drives :

[I]Disk /dev/sda - 500 GB / 465 GiB  ==> detected as [Intel ] Intel/PC partition
Disk /dev/sdb - 500 GB / 465 GiB  ==> detected as [EFI GPT] EFI GPT partition map 

[/I]I checked the second one, it has all the files and directories. So it must be the right one.But when I do "analyse current partition" it shows 
[I]
Partition
1 P Unknown 
[I]2 P Unknown 
*3 P Unknown *[/I]

[/I]So I think the problem is that the partition table is messed up.

I haven't try to recover partition table.
Please help me have a look, is there any other thing should I concern before I recover the partition table?

Thanks

---

### Post by oldfred on 2015-11-04
Testdisk will see current partitioning. But if changed not sure what it shows.
If deeper search shows files then it must be the correct way to look at it.

---

### Post by liang4 on 2015-11-04
I think I know why two different records exist.


Disk /dev/sdb - 500 GB / 465 GiB ([EFI GPT]) ==> this is the original Win7 drive  
Disk /dev/sda - 500 GB / 465 GiB [Intel ] Intel/PC partition ==> This is created by Ubuntu installer. When I install Ubuntu, the installer failed to detect Win7 because it didn't recognise GPT partition. Then I mistakenly clicked "erase disk and install Ubuntu". Then installer created this record.


So before I recover the partition table, should I worry about the second record here, should I remove it and how ?


Please help me have a look.


Thanks

---

### Post by oldfred on 2015-11-04
The installer recognizes gpt partitions just fine.
It will install in UEFI mode if it is booted in UEFI mode and you then must have the ESP.
Or will install in BIOS boot mode on gpt if you have the bios_grub partition.

Generally best to have all drives as gpt once you start to convert to UEFI. 
Windows requires gpt to boot in UEFI mode and MBR to boot in BIOS mode.

Often the issue with Windows is that it is hibernated or needs chkdsk. Then installer cannot mount it and then cannot see it.
Other issues are a conversion of Windows 8 with UEFI/gpt to Windows 7 in BIOS/MBR. Windows does not correctly convert drive from gpt to MBR, and then Linux installer gets confused on whether drive is gpt or MBR as it has bits of both.

---

### Post by liang4 on 2015-11-04
Thanks for explaining this.
I'm just trying to learn all of this and make myself clear.


There is only one system have ever been installed in my drive before it is corrupted, that is Win7.
And as TestDisk detected, it has GPT partitions. And it maybe hibernated.
When I install Ubuntu, since installer cannot see partitions, it considered the drive is empty and tried to create MRB partitions(I don't see any UEFI configuration in BIOS, so I assume it is BIOS boot mode).
Then I forcedly shut down my computer.


As the result, in Ubuntu I can see the MBR partition(I think this is created by installer) in UI, and the rest of the drive is "protective" and cannot be seen in UI. 
In windows, all GPT partitions shows up as Primary partition. Don't know why. Maybe partition table is messed up somehow.


Is this guessing correct? :confused:

---

### Post by oldfred on 2015-11-04
With gpt you only have primary partitions, it does not have the 4 primary partition limit that MBR has, so it does not have extended with logical partitions. 

Perhaps you installed Windows 7 in BIOS mode and converted drive from gpt to MBR? Then Linux sees both? If drive ever had Windows 8, that would have been UEFI with gpt. And Windows install, just does not correctly convert from gpt to MBR.

---

### Post by liang4 on 2015-11-04
I don't remember I ever convert it from GPT to MBR. 
I just tried to use a software(DiskGenius) to read data from it. I don't think that operation converted it to MBR.

I did some research. All said Win7(32) doesn't support GPT.
This is confusing like hell to me, how could my Win7(32) ran on GPT drive for the last two years! :confused:

Seems my drive is hybrid now.
In Windows, I could not see Drive icons. I can only see three Primary drive in "Drive Management" window.
In Ubuntu which  boot in BIOS mode, I can only see a 512MB (cannot remember if this is the exact number, but very close) drive in UI. 

I don't know how it comes.  I will try to find another computer to have a try, and do more research.

---

### Post by oldfred on 2015-11-04
Yes, if Windows 32 bit you must have had a BIOS boot. Only 64 bit Windows supports UEFI and gpt booting.
You may have had hybrid MBR/gpt which can be a problem. Best to avoid if at all possible.

---

### Post by liang4 on 2015-11-04
Hi oldfred, Bucky,

I just copied my documents out from my corrupted drive using testdisk. 
Thank you very much!   
You guys are awesome!

But I still cannot figure out what happened to my drive. 
My confusions are still there.
I will keep investigating. If I find something, I will update this thread. 
Hopefully it will be helpful to someone else who fall into the same situation.

Thanks

---

