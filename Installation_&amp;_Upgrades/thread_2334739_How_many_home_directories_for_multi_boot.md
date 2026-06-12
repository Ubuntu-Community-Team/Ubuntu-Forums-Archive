---
title: "How many home directories for multi boot?"
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by Buntu Bunny on 2016-08-22
I'm getting a new computer and would like to set it up multi boot (comes with Windows 10), home directory, and Xubuntu 16.04. I would also like to install Linux Mint 18 Xfce edition. In doing my preparatory research, I'm reading that when installing two or more Linux distributions it is recommended they not share the same /home due to possible inconsistencies in application settings between various distros. My question is, since Mint 18 is based on Ubuntu 16.04, can they not share the same home? Or would it still be wiser to create a separate home directory for each?

---

### Post by sudodus on 2016-08-22
I agree with the recommendation to have separate home partitions for each of the installed systems. (You can also have /home as directories inside the root directories.)

If you want to share personal files (documents, music, multimedia files) I suggest that you have a separate **data** partition. When you have Windows alongside linux, it is a good idea to use the file system **NTFS** in the data partition to make it available for both linux and Windows. Otherwise you should use a linux file system (for example **ext4**).

(Linux can also read and write the Windows [system] partition, but it is risky, it is better to have a separate data partition.)

---

### Post by ajgreeny on 2016-08-22
Whilst I fully agree generally with sudodous's comment I suspect, having done so myself, that you would probably manage OK with a shared /home partition for those two OSs as long as the version of Mint you are using is exactly the same as the Ubuntu version on which it is based.

For safety, however, I also recommend that you share a data partition as nothing is ever certain about versions when using two different, even though similar, OSs.

---

### Post by Buntu Bunny on 2016-08-22
Sudodus and ajgreeny, thank you for your help. It's very much appreciated. Please bear with me as I try to visualize this. (I hope I'm not getting in over my head). 

What I'm understanding is this. I can *probably* use one /home for the two as long as I keep the same version of Xubuntu and Mint, but I should have a separate data partition for files I might want to use in either one. However, a separate home partition for each would probably be safer. 

So, would that look something like this?

[COLOR="#0000FF"]sda1 recovery (I don't know if Win10 uses a recovery partition, but Win7 does so I've included it in my example)
sda2 Windows
sda3 would be an extended partition with 5 logical partitions (can I have that many?)
[INDENT]sda5  Xubuntu
sda6 Xubuntu home
sda7 Mint
sda8 Mint home
sda9 data[/INDENT]
sda4 linux-swap[/COLOR]

Am I roughly correct? Does the order of the logical partitions matter?

I share nothing with Windows so all the file systems on sda3 can be ext4. I only keep Windows around for the rare times I need hardware tech support (because I'm always told they don't support Linux but for $250 I can get specialized support. Forget that.)

---

### Post by Dennis N on 2016-08-22
On your partition plan, since it is a new computer with Win 10, it is almost certainly to be a UEFI machine with GPT partitioning. With GPT, there are no extended partitions or logical partitions - just partitions. By default, you can create up to 128 partitions.

---

### Post by sudodus on 2016-08-22
Dennis N is right, you will probably get the computer with Windows 10 installed in UEFI mode and the GUID partition table, GPT. There will be at least one more partition, a small EFI partition with the FAT32 file system. That partition is used for booting and replaces the old style boot sector at the head of the drive. When you install Ubuntu, it will automatically add what is needed into the EFI partition. Ubuntu can work in secure mode, but I am not sure if Linux Mint can do that. Anyway, secure mode should be possible turn off. You should also turn off fast boot in Windows. It is a kind of semi-hibernation, and can create problems with linux.

See the links from the following link about UEFI: [Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

-o-

You need not worry about any extended partition. The order of the linux partitions does not matter much, neither in an MSDOS nor a GUID partition table.

But in a mechanical hard disk drive the traveling distance of the read/write head might make a difference, so Xubuntu stuff should be near each other and the same for Mint stuff. Optimal for speed would be to have the swap between the Xubuntu stuff and Mint stuff, but in a new computer there is probably so much RAM, that you will use the swap very seldom unless you hibernate linux. But a central location of swap is an obstacle, if you want to change the amount of drive space between Xubuntu and Mint. So I think you can keep the swap partition at the end as you described.

---

### Post by Dennis N on 2016-08-22
Yes, it's a fact that Linux Mint will not install with secure boot on - so you just turn it off in the UEFI firmware settings. How you do that varies with the particular make of the computer and its firmware.

I assume you are aware that Linux Mint 18 XFCE is based on Xubuntu 16.04, and is going to be similar, but there are some important differences, such as no lightdm (you can choose between HTML and GDM for login screen), a different update manager (Mint Updater), and different software manager (Mint Install). It also introduces the first X-Apps to the Mint universe. Also, Mint-XFCE 18 gives 5 years support vs. 3 years for Xubuntu.

What are X-Apps?
[http://segfault.linuxmint.com/2016/02/the-first-two-x-apps-are-ready/](http://segfault.linuxmint.com/2016/02/the-first-two-x-apps-are-ready/)
In addition to these first two, in the release are included three more: X-Viewer, X-Reader, and Pix.

---

### Post by oldfred on 2016-08-22
If you have a shared data partition and link the user folders like Documents, Downloads, Music etc back into /home so each install saves to same shared data folder, you /home becomes tiny. Then you can keep /home inside / and not have the extra /home partitions. I also moved Firefox & Thunderbird profiles so I have same email & bookmarks in every system.

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
       UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
            Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Buntu Bunny on 2016-08-22
I assumed I would be dealing with UEFI, but didn't realize about the partitions. One of the reasons I wanted to ask questions first is because information on the web becomes outdated so quickly. On top of that I seem to find bits here, and bits there. In trying to put it all together I want to make sure I'm doing it correctly and not creating problems for myself. 

So sudodus, thank you for the link. It looks like a more relevant starting place for me. Thank you for the information on partition order; it makes sense.

Dennis N, I was aware of some of what you mention. It was the 5 year support instead of 3 that was attractive to me, although with a separate home and data, I could update more frequently (as long as I could stay with LTS versions - better for me.) The Mint philosophy appealed to me as well, reminding me of when I first started with Hardy Heron. Linux computing for everybody. Sometimes I feel like Ubuntu has gone another direction and gotten more complicated (or maybe it's because I don't have the personality for Unity).

Old Fred, thank you for all those links. When I read your posts you make it sound so easy! 

I need to do some reading now and then I'll be back with more questions, I'm sure. Also thinking I may just stick with a dual boot for simplicity sake. I'm really partial to the Xfce desktop, but am looking into Ubuntu MATE because it reminds me of the old days. :)

---

### Post by gordintoronto on 2016-08-22
If you specify different usernames, you will get different home folders, even if they are in the same partition. That way, you don't have to decide how much space to give to the different installations. You'll still need unique root partitions.

---

### Post by Buntu Bunny on 2016-08-22
Actually, in reading over the links from Old Fred, I'm starting to wonder if I need to separate home from root at all. I'm wondering if I can just create a separate data partition for files I want to preserve through upgrades. If home only contains config files, why would it need it's own partition? A newer release will require new configurations anyway.

---

### Post by oldfred on 2016-08-22
Some users want to preserve the configuration. I do not, but have some configuration settings in a script that I use when I reinstall or test another install. Only a few do I then manually recreate.

But if you want to have same settings the /home is so small that it is easily backed up, unless you have some applications that save lots of data. I moved Firefox & Thunderbird as they are somewhat larger, but I regularly houseclean old emails and do a vacuum & reindex before backing those partitions anyway.

```
fred@Asusz97:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           793M  9.6M  784M   2% /run
/dev/sda6        24G  9.4G   14G  42% /
tmpfs           3.9G  544K  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1       500M   28M  472M   6% /boot/efi
/dev/sdb4       385G  106G  260G  29% /mnt/data
tmpfs           793M   88K  793M   1% /run/user/1000
/dev/sdb9        23G  4.7G   17G  22% /media/fred/2d2d9d53-8df8-4d1b-94a2-3334f552e56d
/dev/sda3        24G   14G  9.4G  59% /mnt/temp
tmpfs           3.9G   32M  3.9G   1% /tmp
```

My /home is less than a GB.

```
fred@Asusz97:/home$ sudo du -hc --max-depth=1
[sudo] password for fred: 
824M    ./fred
824M    .
824M    total

```

I often houseclean this which it turns out is most of my /home:
655M    ./.cache

---

### Post by Buntu Bunny on 2016-08-22
> **oldfred said:**
> Some users want to preserve the configuration. I do not, but have some configuration settings in a script that I use when I reinstall or test another install. Only a few do I then manually recreate.

But if you want to have same settings the /home is so small that it is easily backed up, unless you have some applications that save lots of data. I moved Firefox & Thunderbird as they are somewhat larger, but I regularly houseclean old emails and do a vacuum & reindex before backing those partitions anyway.

OldFred, thanks! I can definitely see wanting to save browser bookmarks and some emails. Settings for older versions Gimp and Scribus seem less important. So a separate /home is a good idea, along with a data partition.

---

