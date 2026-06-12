---
title: "Change of hard disk"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2012-01-30
I know it was asked several times, but I think I have a special case for that ;-)

 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/lvmvolume-root
                       49G   17G   30G  36% /
udev                  7.8G  4.0K  7.8G   1% /dev
tmpfs                 3.2G  1.3M  3.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  7.8G  4.2M  7.8G   1% /run/shm
/dev/sda1              99M   50M   45M  53% /boot
/dev/mapper/lvmvolume-home
                       97G   86G  6.1G  94% /home
/dev/mapper/lvmvolume-kde
                       46G  584M   43G   2% /home/ronald/.kde
/dev/mapper/lvmvolume-var
                       49G   41G  5.6G  88% /var
/dev/sr0               37M   37M     0 100% /media/datadisk

As you can see above, I use LVM.
The disks are currently IDE with 60 ~ 120 G and I want to replace it with a SATA 2 TB
The boot partition /boot was only 100M and I want to change it to 2 G

I have more disks, but since I can only have 4 IDE drives, these are currently not connected.


I believe, that only the root and /boot is a "challenge", while the others could be copied just with simple tar -c | tar -x 

Again, some of the partitions are lvm and that gives me headache, since I hardly do something with it and always forget how to handle it. I think it is better to use not lvm anymore or should I?



The second big question is RAID. I plan to buy only one hard disk now and add when all is working with one hard disk, removing all IDE drives - the second 2 TB hard disk. These two disk should work in a RAID.

Where do I find information how to switch from one disk to two disk RAID?

---

### Post by oldfred on 2012-01-31
I am not a fan of either LVM nor RAID on most desktops. To me they just add complications for little gain.  

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

I also believe in clean installs as that automatically becomes a houseclean. You can copy /home so you have all your settings. You can extract a list of installed applications, so you can reinstall easily. Any may have a few settings in /etc if you made system wide customization.

But if you copy, you have to update grub2 & fstab with new UUIDs or device dev/sda settings. There also are a few hidden device, UUID or drive settings that should also be updated or updates may not install to the correct place.

But clean installs to drives to something over 1TB will also convert to gpt not MBR.

---

### Post by ELMIT on 2012-01-31
Thank you very much. 
> I also believe in clean installs as that automatically becomes a houseclean. You can copy /home so you have all your settings. You can extract a list of installed applications, so you can reinstall easily. Any may have a few settings in /etc if you made system wide customization.

I will follow that. How do I get a list of all installed applications?

So the way would be, to burn a 11.10 CD, install from this onto new SATA whereby all IDEs are unplugged. 

Study lvm once again, to be able to attache these IDE disks, so that they can be recognized, ...

Then plug in each one-by-one and copy /home and /etc to a /etc-old

Sounds a big job, ...
Or can I do some short cuts?

---

### Post by oldfred on 2012-02-01
Just a few rsync commands I would think to copy everything over. I am not sure I would copy all of /etc. Sometimes they have new settings that you should keep, but you may have edited a few files for system wide changes and you want just those. I learned just to backup any system file I edit to /home so my backup of /home includes everything without having to copy entire system when only a couple of files are changed.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

You just need the same copy of /home that you would use in moving /home.
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

