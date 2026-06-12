---
title: "partition a hard drive for 3 linux distros"
date: 2018-12-10
forum: Installation &amp; Upgrades
---

### Post by thedoctor818772 on 2018-12-10
I currently have a 1TB hybrid drive on my HP laptop. After typing   

```

sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

in a terminal, I get the following:

```

NAME   FSTYPE     SIZE MOUNTPOINT                    LABEL
loop0  squashfs   2.3M /snap/gnome-calculator/238    
loop1  squashfs  89.5M /snap/core/6034               
loop2  squashfs  14.5M /snap/gnome-logs/45           
loop3  squashfs  42.1M /snap/gtk-common-themes/701   
loop4  squashfs   3.7M /snap/gnome-system-monitor/57 
loop5  squashfs 102.9M /snap/tusk/16                 
loop6  squashfs    13M /snap/gnome-characters/124    
loop7  squashfs  34.6M /snap/gtk-common-themes/818   
loop8  squashfs 144.4M /snap/skype/63                
loop9  squashfs 140.9M /snap/gnome-3-26-1604/70      
loop10 squashfs  34.2M /snap/gtk-common-themes/808   
loop11 squashfs 140.7M /snap/gnome-3-26-1604/74      
loop12 squashfs  88.2M /snap/core/5897               
loop13 squashfs  87.9M /snap/core/5742               
loop14 squashfs 147.3M /snap/skype/66                
loop15 squashfs    13M /snap/gnome-characters/139    
loop16 squashfs   2.3M /snap/gnome-calculator/260    
sda             931.5G                               
&#9500;&#9472;sda1 vfat       487M /boot/efi                     
&#9500;&#9472;sda2 ext4      47.5G /                             
&#9500;&#9472;sda3 ext4      47.5G                               
&#9500;&#9472;sda4 swap       7.5G [SWAP]                        
&#9492;&#9472;sda5 ext4     828.6G /home                         
sr0              1024M

```

I am currently downloading Deepin Linux and will then write it to a USB stick. I do not have much experience with partitioning but would like to add (upon rebooting into the Deepin USB stick) a partition for Deepin, while still being able to access my home directory from that Desktop Environment.

How can I accomplish this?

Thanks,

-Michael Dykes

---

### Post by yancek on 2018-12-10
Almost your entire drive is taken up by your /home partition so the first thing you would need to do is shrink that partition to make room for your new install.  I'm not sure if Deepin has GParted on it but it if does, that will work.  You won't be able to do it from an installed system.  Make sure you install Deepin UEFI as your current install is UEFI.  Some information on UEFI at the Ubuntu link below, read particularly the General Principles section.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-12-10
Best not to try to share /home, but use a data partition. Your /home has all your user configurations for each install & your data. But if you put all or most of data in a data partition you can mount it in every install. I also move Firefox & Thunderbird profiles that are normally hidden into my data partition so I have same bookmarks & email in all my Ubuntu installs.

I then have multiple 25GB / (root) partitions and a large data partition. Some versions since updated, but still similar.
       Oldfred's current partitions Dec 2015
[URL="http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413"]http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413

      [/URL]
 The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) & 
[https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk](https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk) 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata) 
    [URL="http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413"]
[/URL]

---

### Post by Tadaen_Sylvermane on 2018-12-18
One thing I might suggest is blast the whole thing and rebuild using LVM. Snapshots before major upgrades is just one of the best reasons ever to use it. Another reason is it is easy to add an unlimited number of volumes. You can test and install distros to your hearts content without worry. I also agree on the /data partition. I think I got the idea from OldFred as well, has made my life a breeze. Sharing a home with multiple distros is just asking for conflicting settings.

---

### Post by oldfred on 2018-12-18
If you are using gpt partitioning, you only have primary partitions.

This shows whether gpt(GUID) or MBR(msdos) partitioning.
sudo parted -l

The only reason now to use MBR is if installing or you have an install of Windows in the BIOS boot mode. Windows requires MBR for BIOS and gpt for UEFI. 
All new systems since 2012 and release of Windows 8 are UEFI systems and Windows has to be pre-installed in UEFI mode with gpt partitioning.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

