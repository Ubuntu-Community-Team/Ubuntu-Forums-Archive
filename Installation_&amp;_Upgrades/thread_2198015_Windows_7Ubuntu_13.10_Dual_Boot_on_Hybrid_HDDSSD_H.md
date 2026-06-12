---
title: "Windows 7/Ubuntu 13.10 Dual Boot on Hybrid HDD/SSD Hard Drive"
date: 2014-01-06
forum: Installation &amp; Upgrades
---

### Post by ravis51 on 2014-01-06
Hey everyone,

I used to use Ubuntu on my old laptop and have recently bought a new one. I was trying to dual boot Ubuntu and windows on my new laptop when during the installation I did not find the option to install windows alongside with ubuntu. Looking around various forums I found two possible issues that I am not sure how to solve. The first issue I think may be possible is that my hard drive is formatted with a GPT which I have read may be an issue when it comes to dual booting. The second is that when I look at my hard drive's partitions, I see on FAT32 partion which I believe is Windows recovery tools, My standard 400 GB NTFS partition which is windows. A 128 MB partition which I read to be the Microsoft reserved partition and a separate T: (unformatted) partition which I believe is the solid state part of my hybrid drive. I read that it may be neces[COLOR=#222222][FONT=Times New Roman][FONT=Verdana]sary for me to "[/FONT][/FONT][/COLOR][FONT=Verdana][COLOR=#000000]need to remove one partition to get 'logical space' to create an extended partition where to install Ubuntu" because I have 4 partitions.Is this true and if so which partition should I remove or is there another issue I may be missing?
[/COLOR][/FONT][COLOR=#000000][FONT=Times New Roman][SIZE=3][FONT=Verdana]
[SIZE=2]Thanks,
Ravi
[/SIZE]
[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by tfrue on 2014-01-06
You may need to disable secure boot, fast boot, and then try, but here are two really good articles to read that may help you

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2014-01-07
tfrue's links are good for your UEFI install issues. :)

Do not read the old instructions on BIOS and MBR(msdos) partitions, they do not apply with UEFI.

With gpt there is no partition limit (really 128).

Ubuntu installs fine with UEFI, but has some issues with Ultrabooks dual video and possible RAID from Intel SRT.

---

### Post by ravis51 on 2014-01-16
Thanks for responding to my thread. I have been playing with some of the solutions given but I haven't gotten anything to work yet. My computer does not have fast boot nor secure boot so that is not the problem. Any other suggestions?

---

### Post by zemega on 2014-01-16
Can you run a live Ubuntu using CD/DVD/USB and post the partition table using gparted? Sounds like my case before. 100 GB for Windows, 13 GB for Windows Recovery and 487 GB NTFS partition. First in Windows, I shrink the 487 GB partition giving 50 GB for Ubuntu installation.  Then I install Ubuntu.

You're trying to install Windows alongside Ubuntu? Do you mean that you want to install Ubuntu alongside existing Windows?

---

### Post by oldfred on 2014-01-16
Post this to see exact partition layout.

sudo parted -l

---

### Post by ravis51 on 2014-01-16
@zemega yes that is exactly what I want to do. Also here is the partition layout.

> ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS72756 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size   File system  Name  Flags
 1      20.6GB  20.8GB  273MB  fat32        EF    boot
 2      20.8GB  21.0GB  134MB               Mi    msftres
 3      21.0GB  449GB   428GB  ntfs               msftdata
 4      533GB   640GB   107GB                     msftdata


Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 7803MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  7803MB  7799MB  primary  fat32        boot, lba


---

### Post by oldfred on 2014-01-17
You do have Windows in UEFI boot mode with gpt partitions.

If you have Windows 8, you must have secure boot as an option and have fast boot or the always on hibernation.
Microsoft requires vendors to use secure boot with Windows 8 and that users be able to turn it off.

---

### Post by ravis51 on 2014-01-17
@OldFred I do not have Windows 8, I have Windows 7.

---

### Post by fantab on 2014-01-17
Why do you say "Hybrid HDD/SSD"? From the above posted output (sudo parted -l) you only have an HDD...
Is there an SSD?

Check in your UEFI menu for **IntelSRT**, if you have it then disable it. 
Check the SATA mode, it should be set to **AHCI**.

Is your Windows7 'Hibernating'? If yes, then you have to disable hibernation and actually shutdown Windows.

For Ubuntu installer to offer an option to "install alongside windows' you need show the installer some space on the HDD/SSD to work with, either as a 'separate linux partition' or 'unallocated space'.
To create space for Ubuntu you have to ['Shrink a Windows partition']("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html") (in your case 428gb parition looks good for this), then either create a Linux partition, or leave the created space as 'unallocated'.
You MUST manage Windows partitions with Windows tools only.

---

### Post by 1clue on 2014-01-17
Is this an OEM windows or one you bought a license for separately?

I guess what I'm getting at is that IMO a dual boot is one step away from useless.  If it were me, I'd have one main operating system and then put the other one on a VM.

If you dual boot, you can't access functionality from the other operating system.  If you use a VM then you can run both at once and shut the secondary one down when you're not using it.

---

### Post by zemega on 2014-01-17
Running Windows in VM is also a good choice, provided your laptop can handle it, and if your laptop can handle it, just run it inside VM.

Its better to shrink the partitioin using Windows. I'm seeing the the whole 400GB as Windows installation. If its me, I would set only 100 GB to Windows partition, only because I don't run any game or lots of programs. then 250 GB NTFS partition that can be accessed by both Windows and Ubuntu. Then 50GB for Ubuntu installation, again I keep my OS slim without any games or unnecessary programs to me. So your partition might differ. And also, I linked all the documents and data to the 250GB partition, so that if the Windows or Ubuntu partition become corrupted, your data partition is still alright.

Seeing your partition again, I believe you wanted to install Ubuntu on the 107GB? Why don't you post your HDD/SSD hybrid brand and model? If its GPT, then you can have more than 4 partition. SSD/HDD hybrid usually means 128 GB SSD housing Windows partition and the HDD to put the rest of the stuff. Or rather post your laptop brand and model, see if you can upgrade your RAM and your HDD.

[ATTACH=CONFIG]249560[/ATTACH]
In your partition table, theres a missing first 20GB. That I believe is your Windows Recovery partition (mine was 15 GB). Looking from Windows Disk Management, you can see my example here, first is C: which is Windows, then 15GB which is the Windows Recovery partition or rather Windows reinstallation partition (ASUS set it up like that, though I dont complain), a 300GB data partition that can be accessed from any OS you want to put in, 22.6 GB Ubuntu 13.10, 24.09GB OpenSuse (work purposes), and 4 GB SWAP. I hope this gives you information that you needed. Whatever you do, if you want to keep Windows for future use, do not delete, move or even toucch the 20GB (mine is 15 GB) as it is linked to your motherboard (when you want to restore or reset your Windows, the motherboard will go to that partition and reinstall Windows, which usually will wipe your other OS as well. Of course you can always reinstall fresh Windows 7 through USB or CD/DVD.

PS: Microsoft is abondaning Windows 8, they are gointo treat WIndows 8 like Windows Vista, forget about it and introduce Windows 9 next year. They probably will not really support Windows 8 just like what they did to Windows Vista. So if you want to jump to Ubuntu, you better jump all the way, and run Windows inside VM.

---

