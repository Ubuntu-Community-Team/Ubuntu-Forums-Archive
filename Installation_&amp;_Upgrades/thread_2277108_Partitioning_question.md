---
title: "Partitioning question"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2015-05-06
Hello everyone, I have a question I'm hoping someone would be kind enough to answer. 

I'm currently running Windows 8.1 and Ubuntu 14.04, as a dual boot, the hard drive I'm using only has about 160.GB I want to remove windows and just allow Ubuntu to be the only os on this machine. My question is how would I apply the space Windows is using and add it to Ubuntu partition with out losing any space. Thanks so much

---

### Post by SeijiSensei on 2015-05-06
Let's suppose Windows is installed on /dev/sda1. (If Windows is on a partition other than /dev/sda1 you should use that instead in the commands below.) We're going to convert that to a Linux filesystem and mount it as /home.

First we'll reformat /dev/sda1 as ext4.  Open a terminal and run these commands:
```

sudo mkfs -t ext4 /dev/sda1
sudo mount /dev/sda1 /mnt
cd /home
sudo rsync -av . /mnt
ls /mnt
sudo umount /mnt

```
 Now the filesystem in /dev/sda1 should have a complete copy of the original /home as shown by ls /mnt.  Next edit the file /etc/fstab as root with "sudo nano /etc/fstab" and add this line
```
/dev/sda1     /home     ext4     defaults     0 0
```
then reboot.

Now the machine should be using the old Windows partition as /home.  Make sure things work as expected, then we have one more step left to free up the space being used in the old /home.

Reboot the machine.  When you get the grub menu, pick "Advanced options" then highlight the "recovery mode" kernel and hit return.  You'll see a lot of text fly by the screen, followed eventually by a menu where you can pick "root shell."  You'll end up facing a "#" prompt.  Now we'll unmount the new /home which is hiding the old version underneath it and delete the old files.
```

# mount -o remount,rw /
# cd /
# umount -f /home
# cd /home
# rm -rf *
# exit

```
Now let the machine reboot.  It will come back up with the old Windows partition being used as /home again. Use the command "df" to see how much space you have in each partition.  The available portion of / should be considerably larger since the home directories are no longer stored on that partition.

---

### Post by grahammechanical on 2015-05-06
You need to become familiar with the basics of partitioning using Gparted.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

A couple of things to keep in mind. We run Gparted from a Ubuntu live session. With Windows 8 pre-installed there will be a partition with EFI boot files in it. Do not delete that partition.

At a very basic level we delete one partition and that creates unallocated space and then we resize another partition to take up the unallocated space. We cannot give more specific advice without knowing more about your specific partition layout.

Screen shot of Gparted open taken from the live session would be useful.

Of course, we could simply re-install Ubuntu using the Use the Entire Disk option.

Regards.

---

### Post by SeijiSensei on 2015-05-06
I proposed a solution that doesn't require repartitioning.

---

### Post by RobGoss on 2015-05-06
Thanks so much guys for the fast response, It seems kinds of complicated but then I really want this machine to only run ubuntu. I have five other machines all running Linux and over the past few weeks I have really enjoyed what Ubuntu and Linux has to offer so over time I will be moving away from Windows.

I think just doing a reinstall of Ubuntu might me the best way to go only because I don't have tons of apps and programs on this drive, all tho I would really prefer just removing Windows and just give this disk space to Ubuntu....

I've used Gpartition only a few time so I'm no expert but I will have to familiarize my self to achieve my goal.

---

### Post by yancek on 2015-05-06
You could take a look at the link below, the GParted Manual and see if the explanations of using/changing partitions and formatting is understandable to you and go for it.  Otherwise, reinstalling might be better if it looks too complicated to you.

  [http://gparted.org/display-doc.php?name=help-manual#gparted-partitions](http://gparted.org/display-doc.php?name=help-manual#gparted-partitions)

---

### Post by RobGoss on 2015-05-06
> **SeijiSensei said:**
> I proposed a solution that doesn't require repartitioning.

And what might that be?

---

### Post by RobGoss on 2015-05-06
Thats a good Idea I am doing that as I type this.

---

### Post by RobGoss on 2015-05-06
Ok so opened up Gpartition and I have the following partitions and file system 

Here we go:

ada1-nfts
ada2-extended
ada5-ext4
ada6-linux swap

I'm assuming **ext4** is my **Ubuntu** partition correct? and the **nfts **is my **Windows** partition correct?
ok so when I opened Gpart is gives me an option for format the** nfts** file system to the **ext4 **file system and so on, is it safe to say that if I choose this option it will format the ntfs file and add the allocated space to the ext4 file system if chosen.

---

### Post by yancek on 2015-05-06
If sda1 is your windows (ntfs) partition, you highlight it and select umount to unmount it then select it again and select Format as ext4.  I will then be available if you create a mount point on your Ubuntu system for it.  If you want it available and mounted on boot, you add an entry to the /etc/fstab file which needs to be edited as root (use sudo).

---

### Post by RobGoss on 2015-05-07
Thanks so much, so if I do a reinstallation of Ubuntu over Windows, it will remove Windows and apply that Windows space to Ubuntu correct?

---

### Post by SeijiSensei on 2015-05-07
> **robert159 said:**
> And what might that be?

[**This one**](http://ubuntuforums.org/showthread.php?t=2277108&p=13280255&viewfull=1#post13280255) that uses the now-empty Windows partition to store /home.

If you re-install, just tell the Ubuntu installer to use the entire disk for itself.  It will repartition and reformat the drive and make all of the space available to Ubuntu.

---

### Post by RobGoss on 2015-05-07
Thanks so much you guys been a big help.

---

