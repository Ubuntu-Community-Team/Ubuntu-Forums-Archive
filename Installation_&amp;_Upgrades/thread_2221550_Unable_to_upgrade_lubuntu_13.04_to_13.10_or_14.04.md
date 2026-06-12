---
title: "Unable to upgrade lubuntu 13.04 to 13.10 or 14.04"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by HiRez_L on 2014-05-02
OK, I have been working with Linux for 20+ years, do it for a living, should be able to fix this myself . . . but can't.  So I am crowd-sourcing my problem.

System:  Dell Optiplex 320 (Don't laugh)
CPU: Single physical core, 2 logical core Pentium 4 3.2GHz
GPU: NVidia GT520, 2 monitors attached
OS:  Lubuntu 13.04 x86_64
Kernel:  3.8.0.30-generic
RAM:  4gb, 2 2GB sticks, 4GB Swap

I cannot upgrade this.  I know, I could just reinstall, but I am running my Plex media server on this box, with terabytes of storage full of shows and movies, and want to preserve data.  Could I put it all on separate file systems, and reinstall anyway?  Yes, if I had space to swap it all around, but I don't.  So I would really like to upgrade instead of reinstalling.  Here's what I get:

  
 rfelty@REZ:~$ sudo do-release-upgrade -dChecking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)

<goes through sources.list, updates everything>

Fetched 1,424 kB in 6s (237 kB/s)                                              
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 


Updating repository information

<more updates>

Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 


Calculating the changes


Calculating the changes


Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 




If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
rfelty@REZ:~$

I've tried this 4 or 5 times over the last 6 months or so, always with the same result, and run sudo ubuntu-bug ubuntu-release-upgrader-core multiple times, which I assume sends some info to someone somewhere at Ubuntu, but never heard anything back.  Googled the problem all over the place, found no solution.  So now I am asking the Ubuntu community for help, does anyone have any idea how to work around this, or do you need any more info to help diagnose what's wrong?  I am not running a pre-release version, or upgrading to a pre-release version.  I do have a modified sources.list, but I have added so many ppas over time for this package or that package that I have no idea what an unmodified sources.list would look like.  I probably should have done a cp sources.list sources.orig before I made the first change, but I didn't.  Thanks in advance for any help you can offer.

---

### Post by slooksterpsv on 2014-05-03
I'm not sure how to help with that one, the only things I can advise are this:

1. Hopefully you have a backup because there is a way to upgrade without destroying your data - as long as the data isn't in any system folders like /var /bin /etc and so on.
2. If your data is in /home that's good, if it was on a separate partition, better.

When you install Ubuntu, Xubuntu, etc. you can choose - something else, and manually setup your partitions to where it doesn't format the drive, but keeps the same filesystem (e.g. ext4) and you set the mount point to /

So you find the partition you want to install, double click, choose the same partition type like ext4, set mount point to / - DO NOT CHOOSE FORMAT, and it will go through and install over top.
Now for the caveats:

If you installed your software through the Software center, it may delete it, where you'll have to reinstall.
If it uses any SQL databases, those may be deleted which means if its setup through a database via plex, that info will be gone and have to be repopulated.
If you compiled, you may have to recompile and reinstall plex as Plex will most likely be removed from the system.

So good:
Data still there
Bad:
Apps gone, settings potentially gone, databases gone, etc.

Be careful about how you approach and see if you can do backups on anything you currently have that may be small like DBs, configuration settings, etc.

---

### Post by fantab on 2014-05-03
The output of the following will help us see where your system files and other data is, then perhaps you can follow 'slooksterpsv's suggestion.
However, if you have your data separate say in /home partition then re-installing is quite simple without much risk of data loss.
```
sudo parted -l
sudo fdisk -l
```

---

### Post by RGMoonen on 2014-05-03
As slooksterpsv has said, the only problem you really have, provided that all your media is in the /home directory is that you will lose your database, so perhaps do a mysql dump first.
I am in a similar position with a debian based mythtv-backend machine I have, in that the system hard drive has crashed. :-( But I don't have a mysql dump.

Your dist-upgrade problem seems to be that the distribution specific upgrade packages are no longer on the repos, you may have some luck if you can locate an archive repo for your distribution.

cheers

Robert

---

### Post by Elfy on 2014-05-03
You might manage to do this by pointing your sources at [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

13.04 is EOL.

I'd disable all the PPAs though.

PPAs should be in /etc/apt/sources.list.d/

If you're not about your source list then give people your /etc/apt/sources.list to look at.

---

### Post by HiRez_L on 2014-05-03
parted -l:

Model: ATA WDC WD10EZEX-00R (scsi)Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  996GB   996GB   primary   ext4            boot
 2      996GB   1000GB  3999MB  extended
 5      996GB   1000GB  3997MB  logical   linux-swap(v1)




Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot




Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1500GB  1500GB  primary  ntfs         boot




Model: Seagate GoFlex Desk (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ext4

---

### Post by HiRez_L on 2014-05-03
fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00008d26


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1945712639   972855296   83  Linux
/dev/sda2      1945714688  1953525167     3905240    5  Extended
/dev/sda5      1945716736  1953523711     3903488   82  Linux swap / Solaris


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x87c02c20


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1953521663   976759808    7  HPFS/NTFS/exFAT


Disk /dev/sdd: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006f1bd


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1953525166   976762552   83  Linux


Disk /dev/sdc: 1500.3 GB, 1500299395072 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930272256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a97d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  2930272255  1465135104    7  HPFS/NTFS/exFAT


Disk /dev/sde: 8166 MB, 8166703104 bytes
256 heads, 63 sectors/track, 989 cylinders, total 15950592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          56    15950591     7975268    c  W95 FAT32 (LBA

---

### Post by HiRez_L on 2014-05-03
Tried the old releases thing:

sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list

I get connection err on most of them:

WTH?!?  Just tried again, and they all worked, maybe there was a weird network thing going on yesterday, will try do-release-upgrade again!

---

### Post by HiRez_L on 2014-05-03
Odd, it doesn't err out on a sudo apt-get update, but it does on a do-release-upgrade:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                       
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                          
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US            
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US      
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                          
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                   
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US             
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US        
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US             
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                          
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US               
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US      
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US      
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                          
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US        
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US            
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US      
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US      
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US        
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US            
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US      
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US      
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US        
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US     
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                       
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                          
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US            
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                       
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                          
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                   
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US             
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                          
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US        
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US             
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US               
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US      
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                          
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US      
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US        
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US            
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US      
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US      
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US        
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US            
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US      
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US      
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US        
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US

---

### Post by fantab on 2014-05-05
> parted -l:

Model: ATA WDC WD10EZEX-00R (scsi)Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  996GB   996GB   primary   ext4            boot
 2      996GB   1000GB  3999MB  extended
 5      996GB   1000GB  3997MB  logical   linux-swap(v1)


You don't have your data separate from root files... Backup your DATA and follow [slooksterpsv's suggestion]("http://ubuntuforums.org/showthread.php?t=2221550&p=13011618#post13011618").
lf that doesn't help either then install a clean copy of 14.04.

---

### Post by HiRez_L on 2014-05-05
> **fantab said:**
> You don't have your data separate from root files... Backup your DATA and follow [slooksterpsv's suggestion]("http://ubuntuforums.org/showthread.php?t=2221550&p=13011618#post13011618").
lf that doesn't help either then install a clean copy of 14.04.

Most of the data is on sdb, sdc and sdd.  I don't have the capacity to back it all up, but I am pretty sure I could do a fresh install without impacting those drives.  My main concern is that all the apps live on sda, so if it gets wiped, I lose the Plex db, the sickbeard db, the couchpotato db, etc.

---

### Post by Elfy on 2014-05-05
> **HiRez_L said:**
> Most of the data is on sdb, sdc and sdd.  I don't have the capacity to back it all up, but I am pretty sure I could do a fresh install without impacting those drives.  My main concern is that all the apps live on sda, so if it gets wiped, I lose the Plex db, the sickbeard db, the couchpotato db, etc.

Back them up elsewhere perhaps. 

Even if they are system owned you can still copy them - just need root rights to do it. 

If they are in you're home - just copy them :)

---

### Post by HiRez_L on 2014-09-15
Did a fresh install without formatting, all my stuff on the other drives was fine, had to re-install most of the apps, plex database got reset.  Interestingly enough, the sickbeard db did not get reset, kept all my shows and knew what was downloaded and what was needed, etc.

---

