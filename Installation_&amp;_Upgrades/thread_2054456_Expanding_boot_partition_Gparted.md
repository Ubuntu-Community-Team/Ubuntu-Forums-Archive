---
title: "Expanding boot partition Gparted"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by goatroper on 2012-09-07
Ihave ubuntu 11.10 on 1 TB hard drive /home is seperate 890 GB partition swap is 8GB and boot is 9 GB now afrter shrinking /home and moving swap I have unallocated 23 GB between / boot and swap.  I need to expand boot to the unallocated space as am getting low disk space warning in boot partition as there is only 796 MB unused in that partition.  If I change unallocated to new logical ext 4 partition will I be able to expand the boot into that space?  I am doing this prior to upgrading to 12.04 as I now know that I created too small a boot partition, and I want to keep /home seperate partition.  Any help appreciated.

---

### Post by TheFu on 2012-09-07
You can only expand into storage that is next to the existing storage.  Gparted has a graphic that shows how the storage is organized on the disk.

I've been running Ubuntu **with** my HOME on a 10G partition for 3 yrs, so 23G isn't needed unless you've never met a program you didn't want to install.  A few months ago, I outgrew that into a 13G partition.

A low disk space warning only matters if you commonly use it.

The idea that you need an 8G swap seems strange to me.  The reason to have swap is to let the system get slower before you run out of memory that can be allocated.  8G seems huge to me.  IMHO, after 2G swap, I need to add more RAM.  Most of the servers here don't have any swap at all. We tune the RAM to the processes.  Without facts and data about your actual running systems use of swap, there is no way to know how much you actually need.

Gparted is pretty easy to use. I'm sure you'll figure out how to get the storage you'd like to expand into next to the storage you need expanded.

---

### Post by goatroper on 2012-09-07
I have 8 GB ram installed and I thought the old rule of thumb was swap should be same size as ram.  Changing that is easy enough but the unallocated disk space is next to the boot partition.  I am currently running that machine on gparted live cd.  I can create a new partition in the unallocated space as ext 4 logical but will I thenbe able to expand the boot partition into that ext 4 partition.  I hoped to expand  the boot to 15 GB just to prevent the low disk space error from popping up even when do not show box is checked.

---

### Post by Epodx64 on 2012-09-07
A 9Gb /boot is excessive I use an ext2 partition thats only 500mb on my /boot partition and even thats excessive 

p.s.
You'll get a better boot speed with ext2 since its a non-journaling filesystem and there's really no good reason to have /boot journaling

---

### Post by goatroper on 2012-09-07
Thanks, so I should return everything back to it's original size and ignore the low spacce warnings?  I guess that since I made boot ext 4 originally I can't change it to ext2 now without trashing the system. Is that a correct assumption? When I do the upgrade to 12.04 can I change the boot to ext 2 then and not trash the system.  By the way the operation to shrink home partition by the 23 GB took 12 hours is this normal or is there a better way?

---

### Post by Epodx64 on 2012-09-07
> **goatroper said:**
> Thanks, so I should return everything back to it's original size and ignore the low spacce warnings?  I guess that since I made boot ext 4 originally I can't change it to ext2 now without trashing the system. Is that a correct assumption? When I do the upgrade to 12.04 can I change the boot to ext 2 then and not trash the system.  By the way the operation to shrink home partition by the 23 GB took 12 hours is this normal or is there a better way?

If you do a fresh install when you upgrade you can format your /boot partition to ext2 just don't format your /home partition and 23 Gb's taking 12 hours really isn't normal what kind of HDD are you using? Mine transfer data at 3Gb/s the only time I had a lengthy format was when I had LVM's setup I accutally had to just redo the partition table

---

### Post by oldfred on 2012-09-07
Are we mixing /boot and / (root) where the /boot folder is still inside the / partition?

Normally a separate /boot only needs to be 200 to 500MB depending on how many kernels you want to keep. But / needs to be 4.5GB to install and usually 10GB to have room to install apps and let histories & log files grow.

You may be able just to do some housecleaining.

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

Basic updates:
HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does as upgrade only does existing packages, this adds new 
sudo apt-get dist-upgrade  #updates dependancies

# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

---

### Post by goatroper on 2012-09-07
> **Epodx64 said:**
> If you do a fresh install when you upgrade you can format your /boot partition to ext2 just don't format your /home partition and 23 Gb's taking 12 hours really isn't normal what kind of HDD are you using? Mine transfer data at 3Gb/s the only time I had a lengthy format was when I had LVM's setup I accutally had to just redo the partition table

WD Green 1.5 TB HDD.  Gparted went through the process twice first time showed 7.5 hrs to completion second time showed 12 hours to completion at that poin I went to bed and this morning it said all operations complete.

---

### Post by Epodx64 on 2012-09-07
> **goatroper said:**
> WD Green 1.5 TB HDD.  Gparted went through the process twice first time showed 7.5 hrs to completion second time showed 12 hours to completion at that poin I went to bed and this morning it said all operations complete.

It's probably because of the size of the HDD 1.5TB is alot of storage.

---

### Post by Epodx64 on 2012-09-07
> **oldfred said:**
> Are we mixing /boot and / (root) where the /boot folder is still inside the / partition?

Normally a separate /boot only needs to be 200 to 500MB depending on how many kernels you want to keep. But / needs to be 4.5GB to install and usually 10GB to have room to install apps and let histories & log files grow.

You may be able just to do some housecleaining.

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

Basic updates:
HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does as upgrade only does existing packages, this adds new 
sudo apt-get dist-upgrade  #updates dependancies

# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

My partition table looks like this
ext2 /boot 500mb
ext4 / 37Gb
swap 4Gb
Ext4 /home 200Gb
Fat32 3Gb Back up of old pictures and some music
Fat32 80Gb Music collection back up
Ext2 80Gb Virtual Machine Partition

---

### Post by goatroper on 2012-09-07
> **Epodx64 said:**
> My partition table looks like this
ext2 /boot 500mb
ext4 / 37Gb
swap 4Gb
Ext4 /home 200Gb
Fat32 3Gb Back up of old pictures and some music
Fat32 80Gb Music collection back up
Ext2 80Gb Virtual Machine Partition

Mine is like this
ext4 / 8.93 Gb
swap 8 Gb
ext4 /home 901 Gb
ext4 /Downloads 497 Gb
 
I am now in the process of returning the partitions back to original sizes except I guess there is something keeping a 1 Gb unallocated space between / and swap.  Gparted says 1.5 hrs to complete checking file system reading block size 16.00 MIB then I think the actual resize begins using 2.0 MIB block reads and that will take 8 hrs again.  When upgrading to 12.04 can I change the partitions to ext2 /Boot, swap 4 Gb,  Ext4 / 30 Gb, Ext4 /Home 900 Gb and Ext4 /Downloads 497 Gb without losing data as long as I don't format /Home or stay with 11.10?

---

### Post by Epodx64 on 2012-09-07
> **goatroper said:**
> Mine is like this
ext4 / 8.93 Gb
swap 8 Gb
ext4 /home 901 Gb
ext4 /Downloads 497 Gb
 
I am now in the process of returning the partitions back to original sizes except I guess there is something keeping a 1 Gb unallocated space between / and swap.  Gparted says 1.5 hrs to complete checking file system reading block size 16.00 MIB then I think the actual resize begins using 2.0 MIB block reads and that will take 8 hrs again.  When upgrading to 12.04 can I change the partitions to ext2 /Boot, swap 4 Gb,  Ext4 / 30 Gb, Ext4 /Home 900 Gb and Ext4 /Downloads 497 Gb without losing data as long as I don't format /Home or stay with 11.10?

As long as you don't reformat /home or resize it all your files and settings will be kept intact and transferred to the new install and another thing to about your /downloads if your going to use that as a backup don't give it a mount point and format it as Fat32 that way if anything where to happen to your system the unmounted Fat32 filesystem would be safe and accessible from virtually any operating system I have two separate unmounted Fat32 partitions one for backups of Pictures and one for a backup of all my music (I lost 50Gbs of Music once won't happen again)

oh yeah and yes you can reformat /boot as ext2 with no worries the boot time is noticeably faster i'd suggest resizing it to about 500mb-1Gb and using the extra space as either an extension of your / filesystem or for a Fat32 filesystem 8 Gb's probably isn't enough for / so I'd suggest resizing it to atleast 20Gb I personally use 37Gb just to be safe I ran out of room on / partition once (it was 10-12Gb can't remember it was like 2 years ago) but that's what i'd suggest.

---

### Post by oldfred on 2012-09-07
I cannot recommend FAT32 for anything except smaller external devices where it may be required. It cannot store a file over 4GB and has no journal so recovery is more difficult. 

NTFS is ok for compatibility with Windows as it will store large files & has journal so Window's chkdsk runs faster.
 But NTFS will not maintain ownership nor permissions for Linux files, so it should only be used for data.

If upgrading /home has user & program settings, but not the programs.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

List is just a long text file, but you may want to houseclean out older packages like OpenOffice as it now is LibreOffice and you do not need nor want both.

---

### Post by goatroper on 2012-09-07
> **oldfred said:**
> I cannot recommend FAT32 for anything except smaller external devices where it may be required. It cannot store a file over 4GB and has no journal so recovery is more difficult. 

NTFS is ok for compatibility with Windows as it will store large files & has journal so Window's chkdsk runs faster.
 But NTFS will not maintain ownership nor permissions for Linux files, so it should only be used for data.

If upgrading /home has user & program settings, but not the programs.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

List is just a long text file, but you may want to houseclean out older packages like OpenOffice as it now is LibreOffice and you do not need nor want both.

Thanks for everyones input as that is what Ubuntu and Linux great.  I am waiting for the resizing back to original to complete as it now says 5 hr 30 min to finish and it should be back to basicly where it was before I began.  As soon as I can boot into it and make sure I haven't lost anything or trashed the system I will do an upgrade install using the tools and suggestions provided me.  I will post success and at that time mark it solved if it is.  Thanks again all.

Just booted back into system and no damage done.  As explained earlier /boot is in / and that was the problem cleaned out old linux-images and old linux-headers and now have space to spare.  When I do the upgrade I will make /boot seperate 1Gb partition and thta should take care of the furure peroblems,  Thanks to all again

---

