---
title: "What is the best way to install ubuntu dual boot"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by dimmaz88 on 2014-07-23
Hi everyone, I've recently had some issues with 12.04 and I made those issues worse by tinkering!

I need to do a re-install and hopefully not affect my windows partition.

Bashing-om has advised me to reformat sdb to MBR to match sda. Thing is, I don't know how.


The way it's setup at the moment is Ubuntu is on a 128Gb SSD, and windows is on a 500Gb hdd. 

Any help is appreciated

---

### Post by Bucky Ball on 2014-07-23
More information, please. This might help a bit:

[http://ubuntuforums.org/showthread.php?t=2234564&page=4&p=13080979&viewfull=1#post13080979](http://ubuntuforums.org/showthread.php?t=2234564&page=4&p=13080979&viewfull=1#post13080979)

That is Bashing-om's advice from the other thread. 

I would personally install Win on the SSD on a 40Gb partition (smaller the better and not sure how much it needs), Ubuntu on the SSD beside it on a 25Gb partition and a 2Gb /swap  after that. I would then use the 500Gb HDD for storage. The SSD is built for speed so you want the OSs on there, not the data (at least not in your setup). That is going to improve the overall experience of both OSs. 

> Bashing-om has advised me to reformat sdb to MBR to match sda. Thing is, I don't know how.

I'm not sure I do either. When you say '... match sda', have no idea how sda is set up so bit hard to advise.. :-k

---

### Post by dimmaz88 on 2014-07-23
Thanks Bucky. I'll try that. I separated them initially in case of any issues, I thought it would be easier to fix. However I don't have a full understanding of the workings.

I use the hdd for storage, and windows is on a small partition on there too.

What other information would you like/need?

---

### Post by Bucky Ball on 2014-07-23
If you are going for two OSs on the SSD, nothing really. ;) Things will change. 

If you want to be foolproof install you could disconnect the hdd and install the OSs to the SSD, make sure everything is sweet there and they're both booting, switch off, reconnect the 500Gb hdd and there's your data drive, job done! (Hope it is that simple!)

If Ubuntu is already on the SSD, it is a matter of booting that, launching Gparted, deleting the partitions on the 500Gb drive and creating a partition(s) on it to suit your future needs (or resizing an existing one). Then go ahead with the SSD install. 

If you are installing both OS fresh on the SSD, install Windows first. This is not essential, but generally saves some stuffing about.

The only other thing you need to decide is if you are going for a UEFI install or legacy. That's probably the biggest decision. Either is an option. Legacy probably more straightforward.

---

### Post by dimmaz88 on 2014-07-23
Every question leads to more questions lol.

UEFI or Legacy being the new one?

As for creating new partitions on the hdd, do I have to create one that windows can use and one for ubuntu? NTFS, EXT4?

---

### Post by Bucky Ball on 2014-07-23
> **dimmaz88 said:**
> 
UEFI or Legacy being the new one?

UEFI is the new one. Windows 7 and 8 can use it, or not. 

> **dimmaz88 said:**
> As for creating new partitions on the hdd, do I have to create one that windows can use and one for ubuntu? NTFS, EXT4?

Correct. You would have something like (for instance):

sda1 = Win; NTFS
sda2 = / (Ubuntu OS); EXT4
sda3 = /swap; 2Gb and swapspace

sdb1 = a 500Gb NTFS partition (so Win can read/write to it) or you can split it how you like it. Have a think.

If you're using legacy you can have no more than four partitions on any one physical drive. You can create an extended partition the size of the drive and put as many logical partitions in that as you like, though (or three primaries and an extended, whatever suits).

With the setup above you will end up with your /home directory in the / partition instead of a separate /home directory. The trick here is to symlink the directories in /home to real data partitions on the storage drive sdb. 

There are options, but this set up is common enough and sounds like it might suit your situation. One of the benefits is that your data is on a completely different drive to the OS. Good for reinstalls and backups. And, of course, if anything goes wrong with the SSD. ;)

PS: An even better way is to have the /swap on sdb. It will barely ever be used anyway if you have a decent amount of RAM. You can add this during install or create the /swap later on sdb then add it to your fstab and reboot.

---

### Post by dimmaz88 on 2014-07-23
Yeah I meant for the storage disk, if I format that one to NTFS both windows and ubuntu can use it is that correct?

I think I'm using UEFI currently, but don't really know.

I assume the symlink is so ubuntu automatically uses the storage drive? How is this done?

What is the purpose of the swap being on sdb? If i make the windows partition as small as it can be, leave 2gb for swap and the rest for ubuntu would that work.
I'll have to figure out how to partion the drive again, the first time I installed ubuntu I just made a single / partition and swap. The current setup has a few, I used a guide and can't remember what I did. I know a couple were quite small.

---

### Post by oldfred on 2014-07-23
GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

If you use gpt partitioning then you have to install Windows in UEFI mode. The Windows 7 DVD only installs in BIOS mode but can be converted to UEFI by copying to a flash drive and doing some updates.

Windows in UEFI mode wants extra partitions, so I would install it first. Then use Windows disk tools to shrink the Windows NTFS main install partition and reboot so it can update to its new size.

      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Winodws disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by dimmaz88 on 2014-07-24
Thanks guys, a few things to consider before I go ahead I think.

I may even just run ubuntu alone, I only have a windows partition for my girlfriend.

---

