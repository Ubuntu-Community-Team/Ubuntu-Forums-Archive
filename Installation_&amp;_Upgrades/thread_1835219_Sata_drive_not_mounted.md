---
title: "Sata drive not mounted"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by ExTruckie on 2011-08-29
I reinstalled 10.04.03 and not I cannot mount my sata drive. These are the errors I get in addition to one at boot stating that "cannot mount media/Stuff" press S to skip or M for manual recovery.

I hit skip and boot onto the desktop and try to mount the volume there and I get the errors attached below

What am I do to next? I don't want to reinstall again!!

---

### Post by Hakunka-Matata on 2011-08-29
did you use a different user name with the new install?  I'd try navigating there using the Terminal, check permissions on the folder???

---

### Post by ExTruckie on 2011-08-29
> **Hakunka-Matata said:**
> did you use a different user name with the new install?  I'd try navigating there using the Terminal, check permissions on the folder???

Here is a bit of additional,  I can see the drive in mountmanager  I am not able to mount it. 
If I go there in terminal I can see the folder I just cannot access it.

---

### Post by coffeecat on 2011-08-29
In your second post, your terminal screenshot shows that you are trying to cd to the folder "stuff" whereas in your first post you report "cannot mount media/Stuff". Linux is case-sensitive.

Anyway, you are using one of the third-party mount applications - mountmanager. I don't know about that one but there are some in the repository that cause more problems than they solve. Let's do some investigating. Please post the output of these terminal commands:

```
cat /etc/fstab
ls -l /media/
sudo fdisk -lu
ls -l /etc/udev/rules.d/
mount
```

Please don't post these are screenshots. Highlight the terminal output with the mouse, right-click and "copy". Now paste it into your post, but between [noparse]```
 and 
```[/noparse] tags, so that when you post this:

[noparse]```
Your
terminal
output
```[/noparse]

It is appears like this:

```
Your
terminal
output
```

---

### Post by ExTruckie on 2011-08-29
Ok 
My bad on the terminal.  I never had any trouble with mount manager and it is under the Software Center. It was added in 10.04. 

Here is the output from the commands you gave me.
mark@Fileserver:~$ cd /media
mark@Fileserver:/media$ cd /Stuff
bash: cd: /Stuff: No such file or directory
mark@Fileserver:~$ clear

mark@Fileserver:~$ cat /etc/fstab
/dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=3c64c76a-5c12-481d-952b-4c3b105e4454 /media/Stuff ext3 remount,users 0 0
UUID=0f56150f-0984-45a7-ac7d-9b3948e5d777 / ext4 defaults 0 0
UUID=50378997-de74-46f7-b153-e9d166d057d6 swap swap sw 0 0

mark@Fileserver:~$ ls -l /media/
total 8
lrwxrwxrwx 1 root root    7 2011-08-28 22:44 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2011-08-28 22:44 floppy0
drwxr-xr-x 2 root root 4096 2011-08-29 00:22 Stuff
mark@Fileserver:~$ sudo fdisk -lu
[sudo] password for mark: 

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb3c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    74823679    37410816   83  Linux
/dev/sda2        74825726    78123007     1648641    5  Extended
/dev/sda5        74825728    78123007     1648640   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c03b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625137344   312568641   83  Linux
mark@Fileserver:~$ cat /etc/fstab
/dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=3c64c76a-5c12-481d-952b-4c3b105e4454 /media/Stuff ext3 remount,users 0 0
UUID=0f56150f-0984-45a7-ac7d-9b3948e5d777 / ext4 defaults 0 0
UUID=50378997-de74-46f7-b153-e9d166d057d6 swap swap sw 0 0

mark@Fileserver:~$ ls -l /etc/udev/rules.d/
total 12
-rw-r--r-- 1 root root  727 2011-08-28 22:58 70-persistent-cd.rules
-rw-r--r-- 1 root root  605 2011-08-28 22:40 70-persistent-net.rules
-rw-r--r-- 1 root root 1157 2010-04-19 05:30 README
mark@Fileserver:~$ 

mark@Fileserver:~$ mount
/dev/sda1 on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)
mark@Fileserver:~$ 
Ok I see that the OS is seeing the drive and folders but cannot mount them. 
Also the mount command only seems to bring back a response from sda1 and I am having trouble with sdb1.


One other thing. I noticed when I was installing the OS the installer asked under the advanced button where I wanted to put the boot manager. Default was on sdb and I wanted to have the bootloader on sda.
This caused several failed installs because I do not have the sata drive listed as a boot drive in the BIOS, and was not changing it. 

Thanks

---

### Post by coffeecat on 2011-08-29
> **ExTruckie said:**
> Here is the output from the commands you gave me.
mark@Fileserver:~$ cd /media
mark@Fileserver:/media$ cd /Stuff
bash: cd: /Stuff: No such file or directory
mark@Fileserver:~$ clear

Your "cd /Stuff" syntax is wrong. You're trying to cd into a folder called Stuff in the root of the filesystem. Since you've already cd'd into /media, you should use one of these:

```
cd Stuff
```

or

```
cd ./Stuff
```

Next - you didn't take notice of what I said about code tags. Compare:

> **ExTruckie said:**
> 

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb3c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    74823679    37410816   83  Linux
/dev/sda2        74825726    78123007     1648641    5  Extended
/dev/sda5        74825728    78123007     1648640   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c03b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625137344   312568641   83  Linux

With:

```


Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb3c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    74823679    37410816   83  Linux
/dev/sda2        74825726    78123007     1648641    5  Extended
/dev/sda5        74825728    78123007     1648640   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c03b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625137344   312568641   83  Linux
```


Without code tags, the output loses its formatting and is near unreadable.

The output of the mount command shows nothing mounted on /media/Stuff even though there is a line in /etc/fstab for this. My guess is the UUID is wrong. I forgot to ask you to post the output of blkid, so please post this output (in code tags):

```
sudo blkid
```

Then, hopefully, we'll have all the information needed to see why nothing is mounted on /media/Stuff.

---

### Post by ExTruckie on 2011-08-29
Just about the time I was notified of your posting. I made a discovery that has some bearing on the problem.  I have two (2) /media/Stuff folders. One on sda1 and the other is on sdb1. The sda1 is the only one that is active.The one on sdb1 is, I believe, is causing the problem  and I can't seem to remove it. 

Here is the output of the code you asked for, sorry I forgot to close the code box

```
 mark@Fileserver:~$ sudo blkid
[sudo] password for mark: 
/dev/sda1: LABEL="Stuff" UUID="3c64c76a-5c12-481d-952b-4c3b105e4454" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="Fileserver" UUID="0f56150f-0984-45a7-ac7d-9b3948e5d777" TYPE="ext4" 
/dev/sdb5: UUID="50378997-de74-46f7-b153-e9d166d057d6" TYPE="swap" 
mark@Fileserver:~$ 

```[LEFT]
[/LEFT]

---

### Post by ExTruckie on 2011-08-29
I reran the fdisk -l and here is the output. FYI, sda is my data disk on the server and sdb is the OS disk. 


```
 mark@Fileserver:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c03b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb3c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4658    37410816   83  Linux
/dev/sdb2            4658        4863     1648641    5  Extended
/dev/sdb5            4658        4863     1648640   82  Linux swap / Solaris
mark@Fileserver:~$ 

```

---

### Post by coffeecat on 2011-08-29
This is a bit of a mystery. The UUIDs in your blkid output match up with the UUIDs in your /etc/fstab, so your "Stuff" partition should be being mounted OK.

Your second fdisk output shows what was sda as sdb and vice versa. This happens sometimes with some BIOSs and is of little consequence. This is why UUIDs are used in /etc/fstab. You don't have two partitions labelled stuff. By the way, I think you are getting mixed up between folders and partitions:

> I have two (2) /media/Stuff folders. One on sda1 and the other is on sdb1.

"/media/Stuff" is the mountpoint (which is a folder) in your main filesystem. It is in partition 1 of your 40GB drive. The Stuff partition is partition 1 in the 320GB drive.

I'll come back to this when I'm fresh in the morning. At the moment I can't see what you need to do and why you're getting the error message that you posted originally.

---

### Post by ExTruckie on 2011-08-29
ok I just realized where your at. Ok I'll look for your reply in the morning.

Good nite.

---

### Post by ExTruckie on 2011-08-29
Just so you have everything in the correct format, I reran all the terminal commands. and posted them here. 
I hope this helps.
```

mark@Fileserver:~$ cat /etc/fstab
/dev/fd0                                   /media/floppy0  vfat  noauto         0  0  
UUID=3c64c76a-5c12-481d-952b-4c3b105e4454  /media/Stuff    ext3  remount,users  0  0  
UUID=0f56150f-0984-45a7-ac7d-9b3948e5d777  /               ext4  defaults       0  0  
UUID=50378997-de74-46f7-b153-e9d166d057d6  /               swap  sw             0  0  
mark@Fileserver:~$ ls -l /media/
total 12
lrwxrwxrwx 1 root root    7 2011-08-28 22:44 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2011-08-28 22:44 floppy0
drwxr-xr-x 2 root root 4096 2011-08-29 17:54 More Stuff
drwxr-xr-x 2 root root 4096 2011-08-29 00:22 Stuff
mark@Fileserver:~$ sudo fdisk -lu
[sudo] password for mark: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c03b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   625137344   312568641   83  Linux

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb3c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    74823679    37410816   83  Linux
/dev/sdb2        74825726    78123007     1648641    5  Extended
/dev/sdb5        74825728    78123007     1648640   82  Linux swap / Solaris
mark@Fileserver:~$ ls -l /etc/udev/rules.d/
total 12
-rw-r--r-- 1 root root  727 2011-08-28 22:58 70-persistent-cd.rules
-rw-r--r-- 1 root root  605 2011-08-28 22:40 70-persistent-net.rules
-rw-r--r-- 1 root root 1157 2010-04-19 05:30 README
lrwxrwxrwx 1 root root   13 2011-08-29 16:56 z80_user.rules -> ../user.rules
mark@Fileserver:~$ mount
/dev/sdb1 on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)
mark@Fileserver:~$ 

```

---

### Post by coffeecat on 2011-08-30
In your post #7 you made this comment:

> **ExTruckie said:**
> Just about the time I was notified of your posting. I made a discovery that has some bearing on the problem.  I have two (2) /media/Stuff folders.

Which is why I thought you were confusing folders and partitions. But now it seems that I am trying to hit a moving target.

In your post #5:

```
mark@Fileserver:~$ ls -l /media/
total 8
lrwxrwxrwx 1 root root    7 2011-08-28 22:44 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2011-08-28 22:44 floppy0
drwxr-xr-x 2 root root 4096 2011-08-29 00:22 Stuff
```

But in your most recent post #11:

```

mark@Fileserver:~$ ls -l /media/
total 12
lrwxrwxrwx 1 root root    7 2011-08-28 22:44 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2011-08-28 22:44 floppy0
drwxr-xr-x 2 root root 4096 2011-08-29 17:54 More Stuff
drwxr-xr-x 2 root root 4096 2011-08-29 00:22 Stuff
```

The /media/More Stuff folder was not there yesterday. How did you add it? With mountmanager? As an aside, it has a space in the folder name which is a very bad idea for a mountpoint.

More worryingly, the reason I asked you for this (from your post #5):

```
mark@Fileserver:~$ ls -l /etc/udev/rules.d/
total 12
-rw-r--r-- 1 root root  727 2011-08-28 22:58 70-persistent-cd.rules
-rw-r--r-- 1 root root  605 2011-08-28 22:40 70-persistent-net.rules
-rw-r--r-- 1 root root 1157 2010-04-19 05:30 README
```

... was to see if mountmanager had created custom udev rules for mounting your "Stuff" partition, which would have complicated things. On the evidence of the above, I could see that it had not, which is why I did not comment on that output. But now I see this (in your post #11):

```
mark@Fileserver:~$ ls -l /etc/udev/rules.d/
total 12
-rw-r--r-- 1 root root  727 2011-08-28 22:58 70-persistent-cd.rules
-rw-r--r-- 1 root root  605 2011-08-28 22:40 70-persistent-net.rules
-rw-r--r-- 1 root root 1157 2010-04-19 05:30 README
lrwxrwxrwx 1 root root   13 2011-08-29 16:56 z80_user.rules -> ../user.rules
```

How did z80_user.rules get there? You must have done something.

Anyway, I think the remount option in the /etc/fstab line for /media/Stuff may be a problem. Try this. From a terminal:

```
gksudo gedit /etc/fstab
```

You will see this in the gedit text editor:

```
/dev/fd0                                   /media/floppy0  vfat  noauto         0  0  
UUID=3c64c76a-5c12-481d-952b-4c3b105e4454  /media/Stuff    ext3  [color=red]remount[/color],users  0  0  
UUID=0f56150f-0984-45a7-ac7d-9b3948e5d777  /               ext4  defaults       0  0  
UUID=50378997-de74-46f7-b153-e9d166d057d6  /               swap  sw             0  0  
```

Be very careful. If you make an error editing this file you have the potential to make your system unbootable. Now edit the file so that it looks like this:

```
/dev/fd0                                   /media/floppy0  vfat  noauto         0  0  
UUID=3c64c76a-5c12-481d-952b-4c3b105e4454  /media/Stuff    ext3  [color=red]defaults[/color],users  0  0  
UUID=0f56150f-0984-45a7-ac7d-9b3948e5d777  /               ext4  defaults       0  0  
UUID=50378997-de74-46f7-b153-e9d166d057d6  /               swap  sw             0  0  
```

There is only one word to change: remount -> defaults. And I've highlighted them in red to make it plain for you. Save the edited file and close gedit. Now:

```
sudo umount /media/Stuff
sudo mount -a
```

If you get any errors, simply reboot. Does that help?

---

### Post by ExTruckie on 2011-08-30
I got your post. I will do the things you ask later as I must be off to work. 
I uninstalled mountmanager since we started and I used PySDM to create the Mount Stuff. 

I was trying to fix the problem on my own. I cannot remove the More Stuff either 

Thanks for all your help so far and I hope my poking around didn't muck things up.

---

### Post by coffeecat on 2011-08-30
> **ExTruckie said:**
>  
I uninstalled mountmanager since we started and I used PySDM to create the Mount Stuff. 

Aaaarrgghhh! Out of the frying pan; into the fire. :(

**EDIT**: :sigh: :wink: I suppose we'd better see what nonsense pysdm has been getting up to. Post the output of:

```
cat /etc/udev/rules.d/z80_user.rules
cat /etc/udev/user.rules

```

The two should be identical, but I'd like to be sure.

When we've solved this, remind me to give you a little homily on how:

1 - Out of the box, and with no tweaking, Ubuntu will automount USB drives and will mount internal partitions on an as-needed basis.

2 - If you need to mount internal partition on bootup there is no substitute for learning how to edit /etc/fstab manually.

3 - There are a number of 3rd-party mounting applications in the repos. They are mostly developed by only one person and are often unmaintained. Some (all?) are bad news. The bad news ones that I know about (based on the number of users of them that have needed rescuing from them) are pysdm, ntfs-config and usbmount. I'm sure we could add to this list.

:wink:

---

### Post by ExTruckie on 2011-08-30
:lolflag:
I be home now.
Here is the output of the code  you sent me to try.

```

mark@Fileserver:~$ cat /etc/udev/rules.d/z80_user.rules
mark@Fileserver:~$ 
mark@Fileserver:~$ cat /etc/udev/user.rules
mark@Fileserver:~$ 

```

---

### Post by ExTruckie on 2011-08-30
Ok good news

I ran the codes you gave me to unmount and remount the drive and all is well.:)

I rebooted the machine and it booted normally without any errors.  :guitar:

My windows boxes on the network can see the drive that I was having trouble with. :popcorn:

Yes now I know a good talking too  about playing with setting you know nothing is due. 
Then again how is one to learn.  In the 3 years I have been using Ubuntu for my file server I have had more trouble with 10.04 than anything. 

Thanks Alot

---

### Post by coffeecat on 2011-08-30
> **ExTruckie said:**
> Ok good news

I ran the codes you gave me to unmount and remount the drive and all is well.:)

I rebooted the machine and it booted normally without any errors.

I'm glad to hear it! It must have been the remount option that was the problem. I've never seen it in /etc/fstab before. I believe it should only be used with the mount command from the terminal, so it's odd that mountmanager added it.

> **ExTruckie said:**
> 
Here is the output of the code  you sent me to try.

```

mark@Fileserver:~$ cat /etc/udev/rules.d/z80_user.rules
mark@Fileserver:~$ 
mark@Fileserver:~$ cat /etc/udev/user.rules
mark@Fileserver:~$ 

```

Wonderful! Pydsm creates a new udev rules file for you and doesn't put anything in it! Which is just as well, I suppose. :) Udev is used for automounting devices. Creating your own rules is quite OK but I was concerned that pysdm had muddied the water by creating rules which would interfere with what we were trying to achieve in /etc/fstab.

About 3rd party mounting apps, particularly those that edit /etc/fstab for you. I agree that there is a real need for a reliable GUI app to do this but as far as I can see there are plenty of apps, but not reliable ones - as you have seen! If you want to know more about editing /etc/fstab, this is a good place to start:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Good luck. :)

---

### Post by ExTruckie on 2011-08-30
One more thing 
How do I remove the /media/Stuff and the /media/More Stuff?  I don't need any more confusion that I already have.

---

### Post by coffeecat on 2011-08-30
> **ExTruckie said:**
> One more thing 
How do I remove the /media/Stuff and the /media/More Stuff?  I don't need any more confusion that I already have.

You don't want to delete /media/Stuff. That's the mountpoint for your Stuff partition, sda1 or sdb1 or whatever it's calling itself today. If you remove it you'll get an error on bootup because the system won't be able to mount the partition to the mountpoint defined in /etc/fstab.

The folder /media/More Stuff is doing no harm and is only taking up a handful of bytes on the drive but if you really want to remove it:

```
sudo rmdir /media/More\ Stuff
```

Yes, that's correct. You have to "escape" the space with a backslash.

By the way, mountpoints are simply empty folders/directories.

---

### Post by ExTruckie on 2011-08-30
Thanks again   
Everything is working fine now..

---

