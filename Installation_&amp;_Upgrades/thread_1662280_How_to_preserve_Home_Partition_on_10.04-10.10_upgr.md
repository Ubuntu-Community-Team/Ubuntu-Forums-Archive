---
title: "How to preserve Home Partition on 10.04-10.10 upgrade with new hard drive?"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by J Bratton on 2011-01-07
I've been enjoying Lucid or a while, and originally figured I'd stick with it for a while. But I picked up a new 2 terabyte internal hard drive the other day and decided I'd try to do a good clean install of 10.10 and see if that might help a few of the residual problems I've been having with 10.04.

So, I did the original install of Lucid with the /home folder on the same partition as the OS. A little research turns up the benefits of having your home folder in a separate partition from your OS, so I figured I'd try to set it up this way for the install of 10.10 on the new hard drive. 

What is the best way to do this? I have a Live CD of 10.10, and have all my files backed up on a separate external USB hard drive. It would be easy enough to install the new internal hard drive and boot from the Live CD and tell it to install Maverick on the new hard drive, as a clean install. And, from what I understand thus far, I'd want to do a manual partitioning. I would format everything as Ext4. I've got 3 gb of memory, so I allocate 3 gb to the "swap" partition. What about the "extended" partition? If I'm just going to have Ubuntu 10.10 on there on one partition (no desire for another OS at the moment), then my /home folder on another (this would be the vast majority of the two terabytes), then the swap partition... that gets me to 3 partitions, so no need for an extended partition, right? Or am I missing something? One reason I ask is that I see that my current 200gb hard drive has a main partition, a swap partition, and then an extended partition of the same 3 gb size as the swap partition. I don't know if this is an intentional thing, or if it was random.

The second question I have is this: how do I get the /home folder from the old internal hard drive to the new hard drive? 

I see various how-tos on the internet about setting up the /home folder as a separate partition, such as:
[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)
and:
[http://www.trainsignaltraining.com/ubuntu-linux-home-partition](http://www.trainsignaltraining.com/ubuntu-linux-home-partition)
but I'm not exactly sure how I'd adapt those instructions for doing this on a different hard drive...

From what I understand, the first question (the partitioning) would be done in a GUI during the 10.10 install process. And then the transferring of the files and settings for the /home folder could be done via command line. Any help would be greatly appreciated!
John
Denver, CO

---

### Post by C.S.Cameron on 2011-01-07
For 10.10, I would suggest the following and then use rsync to copy your old home folder to the new home partition

Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 10 to 50 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 150 to 190 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (3 GB), Beginning and "Use as" = "swap area" then OK.
Confirm "Device for boot loader installation" points to the correct drive. Default should be ok.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Wait until install is complete.

---

### Post by J Bratton on 2011-01-08
Thanks! That looks like a good plan. So, once I use rsync to copy over the /home from the old drive, then all the settings (like having moved the minimize/maximize/close buttons from the left to the right) and programs from the previous installation will be there and in effect?

---

### Post by C.S.Cameron on 2011-01-08
you may need to edit fstab to make sure the uuid for home is correct.

---

### Post by oldfred on 2011-01-08
Your /home has your settings for you as a user and the settings for your installed programs but will not have the programs themselves. You can easily create a list of installed apps and then use that list to reinstall the current versions to your new install.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

Sometimes when copying /home permissions or ownership get messed up. If you have any issues:
You could create partitions in advance with gparted, move /home and then install selecting partitions, but not formating your (now existing) /home.
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

---

### Post by J Bratton on 2011-01-08
> **C.S.Cameron said:**
> For 10.10, I would suggest the following and then use rsync to copy your old home folder to the new home partition

Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 10 to 50 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 150 to 190 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (3 GB), Beginning and "Use as" = "swap area" then OK.
Confirm "Device for boot loader installation" points to the correct drive. Default should be ok.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Wait until install is complete.

That all worked pretty well, but I have a couple of questions:
Did you base your suggested partition sizes on a 2 terabyte drive? And why use Ext2 for the "/home" partition?

I set the "/" partition to be 50 gb, Ext4. Then I set the next one, the "/home" one- as 1,947,000 mb in Ext2. And then the remainder, a little over three gb, as the swap file. It seemed to work just fine, but I wonder about using the Ext2 instead of the Ext4 for the largest partition.
Thanks for the comprehensive instructions!

---

### Post by C.S.Cameron on 2011-01-08
Ext4 is fine for /home.

---

