---
title: "Problem installing Ubuntu 14.10"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by Chris62 on 2014-10-27
Hi,

I have been trying to do a clean install of Ubuntu 14.10 on my desktop machine. I chose the "Something else" option when the installer asked about where it should be installed because I have a separate /home directory, and chose /dev/sda1 for the Ubuntu system and designated /dev/sda2 as my home directory. The installer got as far as saying that it was now preparing /dev/sda1 as an ext4 file system ready to copy the files to it and then it hung. Initially I though that the DVD I had burned might be faulty, so I burned another but had the same result. I have, however, installed Ubuntu 14.10 on my laptop without any problems and I wondered if anyone could suggest why I can't install it on my desktop machine.

The desktop has an Intel i7 processor and 8 GB RAM and I had no problem installing Ubuntu 12.04 and, later, 12.10, 13.04, 13.10 and 14.04 on it so I wonder what is different about 14.10 that it can't be installed on this machine

Any suggestions would be greatly appreciated.

---

### Post by Bucky Ball on 2014-10-27
You don''t need another /home or /swpa. You can use what you already have. 

Mark the / partition to 'Use' and 'format'. Mark /home and /swap to 'use' but NOT to 'format'. 

Prior to proceeding you should make sure you've backed up your /home partition in case things go pear-shaped.

Doesn't solve your problem I wouldn't think, but worth a try.

---

### Post by kansasnoob on 2014-10-27
> **Chris62 said:**
> Hi,

I have been trying to do a clean install of Ubuntu 14.10 on my desktop machine. I chose the "Something else" option when the installer asked about where it should be installed because I have a separate /home directory, and chose /dev/sda1 for the Ubuntu system and designated /dev/sda2 as my home directory. **[COLOR="#FF0000"]The installer got as far as saying that it was now preparing /dev/sda1 as an ext4 file system ready to copy the files to it and then it hung[/COLOR]**. Initially I though that the DVD I had burned might be faulty, so I burned another but had the same result. I have, however, installed Ubuntu 14.10 on my laptop without any problems and I wondered if anyone could suggest why I can't install it on my desktop machine.

The desktop has an Intel i7 processor and 8 GB RAM and I had no problem installing Ubuntu 12.04 and, later, 12.10, 13.04, 13.10 and 14.04 on it so I wonder what is different about 14.10 that it can't be installed on this machine

Any suggestions would be greatly appreciated.

Sounds like it could possibly be this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1361951](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1361951)

I'm the one that reported it but since it's not been confirmed it got no attention during the Utopic dev cycle :(

---

### Post by Chris62 on 2014-10-27
Thanks for your replies. 

Your description of what happened , kansasnoob, is exactly what happened when I tried installing 14.10. I suppose the thing to do is to wait until the Ubuntu developers sort it out. It seems that other people have been affected by this problem too. I had thought of formatting the partition before trying to install 14.10 but I seem to specialise in getting things pear-shaped so I will wait a bit instead

---

### Post by sudodus on 2014-10-27
Please mark that you are affected by that bug (unless you did it already) :-)

That will increase the chances to solve it.

-o-

                        Reported by       [Erick Brunzell]("https://launchpad.net/%7Elbsolost")       on 2014-08-27                    
                                                                    
                                                                        [[COLOR=#006400]This bug affects 2 people. Does this bug affect you?[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1361951/+affectsmetoo")           [             [IMG]https://bugs.launchpad.net/@@/edit[/IMG]           ]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1361951/+affectsmetoo")

---

### Post by Chris62 on 2014-11-02
This may (possibly) be of interest to anyone else who has this problem. I decided to make one last attempt to install Ubuntu 14.10 having made several previous attempts which all ended in failure and when specifying where to install it in the "Something else" menu, I forgot to ask the installer to format the partition. To my surprise the installation succeeded and towards the end there was a message saying that conflicting files were being removed. At no stage did the installer say it was formatting the partition so I assumed that it just overwrote everything in the partition.
The only thing that I am not sure about is that when the machine boots, the boot menu has "Advanced options for Ubuntu" and selecting this reveals that there is a kernel from the previous installation of Ubuntu. Although it is not being used I can't find it in order to remove it. Normally I use Synaptic and get it to search for "linux-image" and then get it to remove the ones that are outdated, but in this instance Synaptic can't find it. Where are the kernels kept?

---

### Post by Bucky Ball on 2014-11-02
What are you using as the search criteria?

---

### Post by oldfred on 2014-11-02
I think you ended up with what we call a "dirty" install. It overwrites old files with new files including configuration, but leaves any file that does not have a new replacement.
       Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

But since your files are still there but not part of install they are not registered with dpkg. You then still have old kernels, old log files and other old date more like an upgrade does. One of the advantages of a new install is that it does a thorough houseclean.


 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

This may only work if still in dpkg:
      
 Determine your current kernel:
uname -a
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic

If you manually delete, then you also have to manually empty root's trash which can be tricky.
I think this did not even work for me when I want to delete some files in root's trash. I had to temporarily change ownership and then changed it back.

 gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.


 # remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

Also check this:
cat /usr/src/*

---

### Post by misiunt on 2014-11-04
I had the same issue when I tried to install Kubuntu 14.10 over the old 14.04 installation. The solution I found ist quite simple :) I chose not the default file system (ext4) but btrfs for the "root partition" and the installation succeeded without any further issues. I guess, the issue is somehow related to ext4 and to the amount and structure of all partitions on the disk.

---

### Post by Chris62 on 2014-11-07
Thanks for your reply oldfred, and for all the tips you included with it. You are right; I have got a dirty install. Before I did this upgrade I had a minor problem in that all the hidden files in my home directory were 'unhidden' by default and I was unable to reverse this and make them hidden by default. Now, after the upgrade the files are still unhidden so I assumed that it was not the clean upgrade I had wanted. Two other "by-products" of this upgrade are that despite having a separate /home directory, which the experts all seem to recommend, the contents were destroyed by the upgrade despite my request that the installer should leave it alone but as far as I can tell I still have a home directory on the partition where I put it albeit an empty one now....perhaps I also have one in the root partition as well...... The other problem is that I wanted to transfer the contents of my Thunderbird profile folder to the newly installed Thunderbird by means of a USB memory stick but there are problems in that what I copy to says "Access denied" when I try and access it. Previously I tried transferring Mozilla profiles from my Windows machine to Ubuntu and found that they worked "as is", but this installation of Ubuntu will not read the memory stick. Frustrating, but I suppose it keeps the adrenalin exercised!

---

### Post by oldfred on 2014-11-07
What format is memory stick. If Linux you may have to reset ownership & permissions. Same if you have separate /home in another partition. You can still update fstab with new entry for separate /home if you have that.

If you had a separate /home you have to mount it, but not reformat it during install. Otherwise it just creates a new /home inside your / (root). 
I do not think with a dirty install or not reformatting /, you have the issue where an install erases entire hard drive. LVM, LVM with encryption and some other options default to erasing entire drive. Only safe install now is Something Else or manual install.

You would only need the entries in fstab, since you already have partition?
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

      
 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I use these to reset my data partition., caution that -R is recursion and it changes everything. Only use on data partition.

 sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data

---

