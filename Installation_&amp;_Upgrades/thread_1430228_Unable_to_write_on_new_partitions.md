---
title: "Unable to write on new partitions"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2010-03-15
I am using Ubuntu 9.04 on a Sony Vaio. Because when I installed it I was new in Linux, I messed up with the partitions and I have lots of unused logical partitions in my extended one.

I have used Gparted to delete a number of partitions and create a new, bigger one (ext3, logical), within the Linux extended partition I have

well, first of all I do not understand why it created partitions that are not mounted, that is I can only access them typing my password and they got automatically unmounted as I restart the computer

but the worse is that I cannot write on it! I completely deleted the previous partitions but, when I open it, there is still a folder "lost and found" that I am not allowed to open (+_+) and when I drag anything into the window it says "error" that is I cannot write anything on an empty partition...

anybody who solved something similar?

---

### Post by oldfred on 2010-03-15
You need to understand a little about mounting and permanently mounting with fstab:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions.

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

---

### Post by abelito8 on 2010-03-15
Thank you for the suggestion
I have installed pysdm, played a bit with it, opened the assistant and tried to change some settings...but the device remains unwilling to be overwritten

Then I have tried with the commands you gave me but also did not change much

still, I have two small partitions I can use, whereas others I can't (I know, my hard disk is completely messy, but I have not found a way to reorganise the partitions without having to reinstall at least "/" )

---

### Post by abelito8 on 2010-03-15
HI...
something happened, I used chmod and now I am unable to unmount drives and partitions using GUI...
If I right click and ask to unmount the system will say I need to be root to do that...
so I had to do it though the terminal...

is there any way to get back and be able to unmount simply from GUI?

---

### Post by Morbius1 on 2010-03-15
Looks like it's time to get back to basics. Please post the output of the following commands:

Open **Terminal**
Type **sudo blkid -c /dev/null**
[COLOR=Blue]*This will list all of your partitions - mounted or not*[/COLOR]
Type **cat /etc/fstab**
[COLOR=Blue]*This will show us how you are trying to automount your partitions.*[/COLOR]
Type **mount**
[COLOR=Blue]*This will show us what you currently have mounted*[/COLOR]

BTW,
> well, first of all I do not understand why it created partitions that are not mounted, that is I can only access them typing my password and they got automatically unmounted as I restart the computer Partitions will only mount at boot when they're in fstab.

> something happened, I used chmod and now I am unable to unmount drives and partitions using GUI...
If I right click and ask to unmount the system will say I need to be root to do that...You don't want to unmount them. That's why you put them in fstab in the first place. When you shut down your system all these partitions will be unmounted for you.

---

### Post by abelito8 on 2010-03-15
Thank you, here you have

**sudo blkid -c /dev/null**
/dev/sda1: UUID="07C4-6297" TYPE="vfat" 
/dev/sda5: UUID="8bbf3af0-deb2-4db5-a4f1-e5665c390773" TYPE="ext4" 
/dev/sda6: UUID="05a4596f-9ad4-4505-8e0d-0e3f7bb148fb" TYPE="ext2" 
/dev/sda7: UUID="2AEC-648F" TYPE="vfat" 
/dev/sda8: UUID="3a4f3a6e-1c49-4a2a-b1e9-d9d7155e9f18" TYPE="ext3" 
/dev/sda9: UUID="b7c19e3a-349f-4155-a827-8f8f41b86b5e" TYPE="swap" 
/dev/sda10: UUID="90612059-fd20-42c0-8651-373236e4f8ec" TYPE="swap" 
/dev/sda11: UUID="78bb8d03-0d12-4511-9fab-270078185280" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: UUID="4c31af13-dac2-4c90-8d9c-ee523787bf38" TYPE="swap" 
/dev/sda13: UUID="35fd40cc-ee04-47e9-b4cf-39a5bd084455" SEC_TYPE="ext2" TYPE="ext3" 

**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda7
UUID=3a4f3a6e-1c49-4a2a-b1e9-d9d7155e9f18  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda8
UUID=b7c19e3a-349f-4155-a827-8f8f41b86b5e  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda9                                  /media/sda9    vfat         users                       0  0  
/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,umask=000     0  0  
/dev/sda2                                  /media/sda2    ext3         defaults                    0  0  

and

mount


/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-18-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda6 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)




the problem is now that when I use a USB it says I do not have the privilege to mount it...I guess this can be done through the terminal but there must be something I did that changed the settings for anything that I was going to mount

....

---

### Post by oldfred on 2010-03-15
You have 3 swap partitions. Did you try to install 3 times and it created 3 different root & swap partitions?

Also the fstab references show that you added a partition in front of the original install listing. The UUID's match valid partitions so the reference is not important.

What is sdb1 that you have permanently mounted? FAT & NTFS partitions permissions and ownership are set as part of the mount. Normally you just specify defaults? And only permanently mount fixed devices.

---

### Post by abelito8 on 2010-03-16
I installed Linux more than 3 times on this computer, and that was when I had not learned how partition works. The reason why I am keeping like this is that I am not sure where is the "/" of the version I am using (I know my /home is sda6) nor what SWAP my Ubuntu 9.04 is using and I do not want to install 9.10 (I had trouble with skype for months and now it's working, whereas I've been unable to fix it on another laptop that has 9.10)

The priority now is that I do not have the permission to use any USB device on this computer. When I plug my external HDD or any USB flash it gives me error

would "sudo chmod -R 777" solve the issue?

---

### Post by Morbius1 on 2010-03-16
Wow !

First, what **oldfred** said.

Second, from fstab:
> UUID=b7c19e3a-349f-4155-a827-8f8f41b86b5e  none           swap         sw                          0  0
/dev/sda9                                  /media/sda9    vfat         users                       0  0  
/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,umask=000     0  0  
/dev/sda2                                  /media/sda2    ext3         defaults                    0  0  From blkid:
>  /dev/sda9: UUID="b7c19e3a-349f-4155-a827-8f8f41b86b5e" TYPE="swap" sda9 is a swap partition yet it's being mounted as vfat. It's also being mounted via a UUID as swap so I'm not sure if you're even running with a swap.
sdb1 doesn't exist so I'm guessing it's the external USB drive
sda2 doesn't exist and I'm not sure what it is.

What I would do is edit the last three lines of fstab ( by opening a terminal and typing **gksu gedit /etc/fstab** ) and put a # sign in front of them to make it look like this: 
> #/dev/sda9                                  /media/sda9    vfat         users                       0  0  
 #/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,umask=000     0  0  
 #/dev/sda2                                  /media/sda2    ext3         defaults                    0  0  Then reboot.

You will get a proper swap partition.
Your external USB drive ( sdb1? ) will return to it's normal operation.

 [COLOR=Blue]**Here's the thing that complicates my recommendation**:[/COLOR] You posted that all of this currently works. In fact you think that your home partition is in /sda6 even though it's clearly not in fstab so it's not being automounted as such. In light of all this and if you have a system that you're happy with, I would like to make just one suggestion:

Put a # in front of the sdb1 line in fstab so that it looks like this:
>   #/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,umask=000     0  0  Your USB devices should return to normal operation.

---

### Post by abelito8 on 2010-03-16
Thank you it worked, at least for my USB drive and permissions to mount

but what # stands for in fstab? Does it mean to restore permission for the users?

I am still unable to use some of my volumes but that will go with the next installation, at least now I can use again my external hdd, thanks

---

### Post by Morbius1 on 2010-03-16
A "#" sign in fstab tells the system to ignore the line completely. Your system is now mounting USB devices upon insertion as it was designed to do.

---

