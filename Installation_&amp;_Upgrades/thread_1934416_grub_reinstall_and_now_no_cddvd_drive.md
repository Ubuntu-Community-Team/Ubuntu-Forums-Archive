---
title: "grub reinstall and now no cd/dvd drive"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by John Galt on 2012-03-02
Hi guys,  had to reinstall winxp, used boot repair to reinstall grub.  Ued the option to reinstall grub on all devices except usb. Later in ubuntu changed it to install grub in first HDD.  Now the drive in which x is installed has to loaded using ntfs config manually (previously auto mount). Have to use skip option at startup to skip auto mount of ntfs drive.   Please advise if somthing can be done auto mount xp drive in ntfs and to make the cd/dvd drive visible.  Does it have something to do with FSTAB?  Thanks for the patient ear.

---

### Post by ajgreeny on 2012-03-02
> **John Galt said:**
> Hi guys,  had to reinstall winxp, used boot repair to reinstall grub.  Ued the option to reinstall grub on all devices except usb. Later in ubuntu changed it to install grub in first HDD.  Now the drive in which x is installed has to loaded using ntfs config manually (previously auto mount). Have to use skip option at startup to skip auto mount of ntfs drive.   Please advise if somthing can be done auto mount xp drive in ntfs and to make the cd/dvd drive visible.  Does it have something to do with FSTAB?  Thanks for the patient ear.
Yes it does.

The reinstall of WinXP has given that partition a different UUID so your system can not now find the windows partition. That means that error message pops up each time you boot.

Let's see the output from ```
sudo blkid
cat /etc/fstab
``` and an simple edit can put things right again.

---

### Post by John Galt on 2012-03-04
sudo blkid

/dev/sda1: UUID="14FC3625FC360192" TYPE="ntfs" 
/dev/sda3: UUID="eac23ce8-ba48-4be7-8ce5-0f904c312f28" TYPE="swap" 
/dev/sda5: UUID="6825ba8e-0641-47dc-abac-e938d691beda" TYPE="ext4" 
/dev/sda6: UUID="c40ba82a-ad24-4aa8-9c3c-8fc1855dd34d" TYPE="swap" 
/dev/sda7: UUID="43a969ba-64f2-43a3-90cd-ef659e201320" TYPE="swap" 
/dev/sda8: UUID="9a3922c6-5a78-4546-afe1-9b3981d92694" TYPE="swap" 
/dev/sda9: UUID="cee9d139-8310-4c18-bdfa-4c450726af7f" TYPE="swap" 
/dev/sda10: UUID="5a1ba186-be9b-4fa9-9a13-9b5d0c3e6653" TYPE="swap" 
/dev/sda11: UUID="aee0eff0-f4c0-4741-bbbd-b343886eded1" TYPE="swap" 
/dev/sdb5: UUID="EC64FF5A64FF264C" TYPE="ntfs" 
/dev/sdb6: LABEL=" Local Disk" UUID="94B40A20B40A0588" TYPE="ntfs"

~$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=6825ba8e-0641-47dc-abac-e938d691beda    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb6 :
UUID=94B40A20B40A0588    /media/_Local_Disk    ntfs-3g    defaults,locale=en_IN    00
#Entry for /dev/sda1 :
UUID=14FC3625FC360192    /media/sda1    ntfs-3g    defaults,locale=en_IN    0    0
#Entry for /dev/sdb5 :
UUID=EC64FF5A64FF264C    /media/sdb5    ntfs-3g    defaults,locale=en_IN    0    0
UUID=2A207CBA207C8F17    /media/sda1    ntfs-3g    defaults,locale=en_IN    0    0
#Entry for /dev/sda6 :
UUID=c40ba82a-ad24-4aa8-9c3c-8fc1855dd34d    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0

---

### Post by John Galt on 2012-03-04
The above post lists the output of the commands. My apologies, not a regular user of forums and a bit slow with computers. Having a great time with Ubuntu 11.10 and think that this is the os for me.

Your help with this mater at hand is greatly appreciated. Thanks.

---

### Post by oldfred on 2012-03-04
You seem to have one or two extra swaps.:) You should be able to delete all swaps but sda6 which is used by fstab.

You normally do not mount a partition by its device which may cause all sorts of confusion. You have to create a mount point and mount the device to that mount point.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

This is my entry:
> # in terminal
mkdir /mnt/shared
# then in fstab:
# Entry for /dev/sdc2 :"
UUID=44332FD360AA9657         /mnt/shared  ntfs-3g      defaults            0  0
I purposely mount in /mnt so it is not seen in Nautilus but then link it or folders from shared into /home.
# from home so default location will be /home/fred
ln -s /mnt/shared
or
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

Another useful option in mounting a Windows partition:
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,uid=1000,windows_names,umask=000 0 0

---

### Post by John Galt on 2012-03-08
Wow, all this info is very confusing. Too much info......
 
Now there seems to be a new problem at hand. As soon as i select skip option to skip ubuntu from mounting sda1 (winxp partition), a screen with a list of services starting pops up and statys there. This happens every time you select ubuntu 11.10 at startup. Just before his problem also while downloading a few apps through torrents my drive were popping up as full but they still showed lots up sapce in properties menu. 
 
Please help....what is going on...

---

### Post by oldfred on 2012-03-08
Check sizes of partitions.

Partition sizes
df -Th | sort

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h


HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by John Galt on 2012-03-08
my apologies but this is too confusing for me. i think i will settle for a reinstall.
 
Please advise how to copy my downloads folder to the windows drive. This is where all my data is and i want to save this. What command should i put in the terminal ( alt+f2 does give me a command prompt). 
 
Is there a way to rebuild your fstab so that you just mount your root and swap? This way no reinstall would be required and i can do away with muc data damage.

---

### Post by oldfred on 2012-03-08
You can put a # in front of any lines you do not want. That converts it to a comment.

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

You should just be able to use Nautilus to copy any files you want from one partition to another.

---

