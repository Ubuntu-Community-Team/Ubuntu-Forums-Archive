---
title: "Partition hd"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by taxidimu on 2010-10-28
New installation of Ubuntu server 10 on a 250GB HD.
I need to partition the HD as follows:

[LIST=1]
[*]50 GB for OS (Ubuntu server)
[*]remaining space for user data (say "mydata")
[/LIST]
Which selection and values have I to choose?
Thanks.

---

### Post by ajgreeny on 2010-10-28
> Which selection and values have I to choose?What exactly do you mean by that question?

Using a gparted live CD to make the partitions is probably the easiest way.  Just make the two partitions as ext4 and then install the server OS to the small one using manual partitioning when installing, then edit the /etc/fstab file to mount the data partition at boot.

---

### Post by taxidimu on 2010-10-28
[COLOR=Blue][I]Using a gparted live CD to make the partitions is probably the easiest  way.
[/I][/COLOR]I suppose that a "live CD" is the CD I have created from the downloaded ISO file, to install the U Server. I cannot find on the web any other "live  CD" info.

[COLOR=Blue][I]Just make the two partitions as ext4 and then install the server  OS to the small one using manual partitioning when installing, then edit  the /etc/fstab file to mount the data partition at boot
[/I][/COLOR]This is what I need.
I have already installed the OS, only one partition.
But as I have done no more work, I could restart from scratch the installation.
In this case, could you list the steps to make two partitions (the user partition named "mydata")?
I am a little bit confused with LVM!
And is the swap partition automatically created?

---

### Post by ajgreeny on 2010-10-29
Does your CD boot into a gnome desktop?  If not then you don't have a live CD, and I suggest you either download a ubuntu live CD which has gparted on it, or you download the gparted live CD from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and then burn it to a CD and boot to it.

Alternatively you could restart and using manual partitioning, make a new install with a smaller / (root) partition and a much larger /home partition.  You will also need to make a swap partition if you do it this way.  A swap is produced automatically if you let ubuntu install all by default, and you will probably see this listed if you use gparted.

You will see a desktop like my screenshot, which is of my own disk, using a separate /home as mentioned above.  Click on your single partition that should be showing, and choose to "Resize" it.  Grab the right hand edge and pull it to the left to make an OS partition of your chosen size; 50 GB is probably much larger than needed as you are having a separate data partition for all your files and only the OS will go into that partition, I assume.

The remainder of the disk will then show as unallocated space which you can click in and choose "New" and format it to ext4, or whatever file system you want.

Once you have done that reboot to your installed server, run sudo blkid, and then use that output to find the UUID of the new partition and edit your /etc/fstab file using ```
sudo nano /etc/fstab
```adding a line something like ```
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /media/mydata ext4 defaults,relatime 0 2
```Now make the folder /media/mydata with ```
sudo mkdir /media/mydata
``` and then make it owned by you as your username ```
sudo chown -R username:username /media/mydata
```I hope that all helps.  It may sound very complicated, but is not really as bad as it may seem at the moment.  You have already said you can start again if that is easiest, but if you choose the gparted way, you may find that you learn a lot about the system and installing which may be very useful in future.

---

### Post by taxidimu on 2010-11-04
Clear answer, easy operation, works fine.
Thank you.

---

