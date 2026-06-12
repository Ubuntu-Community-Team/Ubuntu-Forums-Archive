---
title: "Installer error: could not unmount partitions in mount point cd/rom"
date: 2020-03-03
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2020-03-03
Hello all,

I made a live bootable usb thumb drive with persistence of Xubuntu 18.04 LTS. I used mkusb to make the the live bootable usb from an iso file I downloaded. The live bootable usb with persistence has worked fine, but when I went to install Xubuntu 18.04 LTS to the hard drive, I eventually go this message:

[I]"The installer needs to commit changes to partition tables but cannot do so because partitions on the following mount points could not be unmounted /cdrom.

 Please close any applications using these mount points." [/I]

See attached screen photo of the error message under my initial below.[I]

I cannot complete the installation to the hard drive. 
[/I]
QUESTION: What should I do?

Thanks,

A.[I]

[ATTACH=CONFIG]285144[/ATTACH]
[/I]

---

### Post by CelticWarrior on 2020-03-04
Have you selected some manual partitioning ("something else...") or automatic?

---

### Post by AbleTassie on 2020-03-04
Hi Warrior,

I selected one of the standard choices, I think it was automatic, and definitely not "something else." Other people have had this same problem, see for example this [link]("https://www.reddit.com/r/linux4noobs/comments/4vcl4x/is_there_any_workarounds_i_can_do_to_unmount/") , which says the problem is that the installer is trying to install to the thumb drive the live boot is already on. Somebody in that older thread said you may have to install manually. I am not sure that is the real problem, so I put out this query. I am thinking that maybe I should try creating another live bootable thumb drive without persistence using Disk Creator and try that. 

Here is another similar [link]("https://unix.stackexchange.com/questions/496118/trouble-when-installing-ubuntu-not-sure-where-i-went-wrong") that discusses the problem.

Anybody have any idea what I should do?

Thanks,

Able

---

### Post by yancek on 2020-03-04
Is the hard drive  your are trying to install to blank or have you created partitions or formatted it with a Linux filesystem?  Have you opened GParted to see if it recognizes the hard drive?  I'm not sure Xubuntu has gparted on the iso but most of the major Ubuntu distributions do.  Since you don't indicate any other OS on the hard drive, have you tried the option to Erase disk and install Xubuntu?

---

### Post by CelticWarrior on 2020-03-04
It has absolutely nothing to do with persistence...

At the point where you selected the option to install didn't you checked the drive that was being proposed was the same you were booting from? And that there wasn't any other detected? You should pay attention to those details.

If the live session can't "see" the drive why were you expecting it to install? What's happening is likely a very common issue: An unsupported SATA mode in UEFI ("BIOS"). It needs to be AHCI. Other modes such as "RAID" or Intel RST aren't supported. Now, if you're dual-booting with Windows, you need to install AHCI support in Windows first or it won't boot. Also disable Fast Startup (Windows) and Secure Boot (UEFI).

---

### Post by AbleTassie on 2020-03-04
Thanks Warrior and Yancek,

The drive is absolutely brand new, installed by me yesterday. It is a Samsung 860 EVO V-NAND SSD, 250GB, Model MZ-76E250. It is a friend's PC and we have been using the Xubuntu live boot usb with persistence as a spare until we could get the new hard drive in. I am not sure whether my friend wants to go back to Windows 8.1 Pro that came with the PC or he wants to stay with Xubuntu. But I thought we would use Xubuntu on the actual hard drive until I figure out how to reinstall the old Windows. I am not sure if I can just reinstall the Windows using files burned onto the motherboard memory or whether I have to order disks or what. He has no disks and the PC is maybe 7 years old. I have to check the PC serial number and contact the manufacturer to find out. But no, I am not dual booting at this point.

I think I chose the option to "erase disk and install Xubuntu." There really is nowhere to install the Xubuntu other than on the hard drive or the USB live boot thumb drive itself. And I just figured that the software would detect the new hard drive and install to that and not be confused by the presence of the thumb drive. But I am apparently wrong. 

QUESTION: So what do I do? 

I  am pretty sure there is a Gparted on the Xubuntu. I can try and see if the new hard drive is recognized by Gparted. I already disabled Secure Boot in the UEFI and changed the boot order to get the PC to boot into the thumb drive Xubuntu. 

If it needs AHCI, how do I make sure that is present, by going into the BIOS/UEFI and making changes?   The PC is a Samsung DP500A2D-A02UB, [specs]("https://www.cnet.com/products/samsung-series-5-500a2d-core-i3-3220t-2-8-ghz-monitor-led-21-5-series/") . 

My friend is disabled and he does not do much except email and solitaire. But one reservation i have about Linux/Ubuntu is that my friend has both a speech impediment and a tremor. And I thought voice recognition software on his PC might help him. But given his speech impediment I thought he might need a good speech recognition program that learns and stores audio files. And somebody knowledgeable told me it is unlikely that there is such a Linux-based speech recognition program. So we might be eventually forced to go back to Windows to use a speech recognition program if that is desired.

Thanks,

Able

---

### Post by AbleTassie on 2020-03-04
I just looked at Gparted and it recognizes the new hard drive, but that may be about all. See the attached photo of the screen under my initial below. It looks like there is one large unallocated partition. The hard drive is nominally 250GB and the relevant specs are probably [here]("https://www.samsung.com/semiconductor/minisite/ssd/product/consumer/860evo/") , I think. The drive is a Samsung 860 EVO V-NAND SSD Model MZ-76E250.

Thanks,

A.

[ATTACH=CONFIG]285152[/ATTACH]

---

### Post by yancek on 2020-03-05
I'd start by opening GParted and going to the Device tab and creating a partition table.  Then create a partition (or partitions) with a Linux filesystem (ext4 default) and if you are not sure if your friend wants to install windows 8 again, leave unallocated space on the drive on which to install it.  You need to decide whether to use msdos or gpt for the drive.  If you use gpt and want to install windows, it will need to be installed UEFI and Xubuntu should also then be installed UEFI.  If this doesn't help, there is some other problem, possibly bad hardware?

---

### Post by AbleTassie on 2020-03-05
Thanks Yancek,

I have done some computer programming years ago and I am comfortable thinking about these things, but I will have to educate myself regarding what you said in your most recent post. It will take some time and I may have more questions. But, I will try my best to get my friend's system working.

Thank you,

A.

---

### Post by oldfred on 2020-03-05
Have you updated firmware from Samsung?
That was the first thing I did with my new NVMe drive. 
Samsung has a bootable ISO, looks more like old DOS screens that updates.
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)

I allocated additional partitions for more Ubuntu (test) installs and did not fully allocate drive.

```
fred@fred-Z170N-focal:~$ sudo gdisk -l /dev/nvme0n1
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/nvme0n1: 976773168 sectors, 465.8 GiB
Model: Samsung SSD 970 EVO Plus 500GB          
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 28B13235-0C01-4A92-BB59-96C0739F1591
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 381805071 sectors (182.1 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   EF00  esp_nvme
   2         1050624        62490077   29.3 GiB    8300  focal_0
   3        62490624       123930623   29.3 GiB    8300  
   4       915333120       976773119   29.3 GiB    8300  
   5       123930624       533530623   195.3 GiB   8300  nvme_data

```

---

### Post by AbleTassie on 2020-03-06
Thanks Fred,

I think I get the idea, it looks like among other things, that the hard drive has to be formatted so that when the OS is actually installed on the drive the OS can interact with the BIOS or UEFI, correct? One question, are any of the suggestions you or yanckek have made (updating firmware, partitions, partition table, linux file system for partition(s), Xubuntu UEFI install, etc) irreversible? I am thinking they are probably not irreversible, but I just want to double-check for my friend's sake. I don't want to mess up his PC.

Thanks,

A.

Thanks,

A.

---

### Post by yancek on 2020-03-06
I'm not sure about the 'updating firmware' in the BIOS, someone else should be able to help.  Creating partitions and filesystems and modifying there sizes can all be changed very easily with various software including GParted.  The biggest problem with these activities is losing data should not be a problem in this case as there is not data.  Once you have an OS installed and data on the various partition filesystems, you need to be more careful as these actions can delete all data, at least from the perspective of an ordinary user.

Have you verified the hardware is UEFI?  If you are not familiar with the use of GParted, reviewing their manual at the link below should be helpful.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by oldfred on 2020-03-06
I have seen some users downgrade an UEFI to get it to work. Later updates fixed that issue and then upgrades were good. Multiple Acer users.

I also have seen where an UEFI update said that this update could not be downgraded. But previous updates had not had those comments.
Generally you want the newest UEFI and list fixes may not include all the fixes that are included in an update.
Last year you had to have a new update for AMD newer systems as it did not work with Linux without update. And then only with 19.10 or newer.

---

### Post by AbleTassie on 2020-03-06
Thank you Fred and Yancek,

I like to understand what I am doing, so I greatly appreciate your advice, and I have started reading and increased my understanding. But sometimes a good/exhaustive understanding of a computer activity is kind of a luxury. So, in the last 24 hours or so, I am wondering if there is any kind of cookbook type instructions for installing Ubuntu (in this case Xubuntu) on a new SSD. 

QUESTION(S): Does Ubuntu/Linux have anything like that?  I guess the link Fred gave at the end of his post above might qualify as leading to such a cookbook.

It seems to me that the manufacturer of the SSD, Samsung, might have such a thing as well. Does anybody think Samsung might have cookbook type instructions for installing an OS like Ubunutu on a SSD?

Thanks,

A.

---

### Post by oldfred on 2020-03-06
Installing on a SSD is no different than any install to a HDD, flash drive, or MMC devices.
And you have two types of SSD, standard SATA and newer, faster NVMe. 
But with SSD, you do have upgradeable firmware.

I just partitioned in advance, used Something Else to install. I only needed ESP & / (root) as I had all data on HDD. 
But newer NVMe drive was larger & my data is not that large, so I created new data partition on SSD and moved/rsync'd data to SSD. HDD is now mostly for backup and some experimental installs.

Link below has general steps to install in UEFI mode. Links to lots more info and some special cases by brand.

---

### Post by AbleTassie on 2020-03-16
As it turned out my friend decided he wanted Windows 8, not Ubuntu on his machine for the time being. He is the typical Windows person who doesn't question things much. But I may use the information here for a later installation of Ubuntu if we run into problems with Windows. 

Anyway, he has Windows 8 on his PC for the time being. 

Thanks to everybody.

A.

---

