---
title: "Cannot write to 2nd HDD, &quot;you are not the owner&quot;?"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by germanix on 2013-10-26
I just got a new laptop with 2 drives. (one normal HDD and one eSata SSD). This machine came without an OS installed. I installed Ubuntu 13.10 on the SSD and this went fine. I can see the normal HDD, I can open its window but I cannot create new files or use it. The owner seems to be Root. Under the drive properties window the drive is shown as a Folder (inode/directory), it shows this location: /media/jacques and under the permisions tab I get "you are not the owner and cannot change the permissions. I have named this drive "Data" And the idea would be to put all of my data there instead of on the SSD with symlinks to my home folder on the SSD.
I would very much appreciate any help to solve this problem. How can I take back the control over this drive?

---

### Post by coffeecat on 2013-10-26
It sounds as though you have one large partition formatted to a Linux filesystem. The fix is easy - you simply mount the partition and chown the mountpoint, which has the effect of changing ownership of the filesystem. But before describing how to do that, we need a bit more more information. You mention /media/jacques. That sounds like part of the path to the mountpoint if you mounted it from the file browser and your username is jacques. I would expect it to be /media/jacques/something-or-other.

Anyway. First question. Are you mounting the partition from the file manager or have you added a custom mount line in /etc/fstab?

Secondly, mount the drive/partition the way you have done when you get the "no permission" error and then run these terminal commands and post the output:

```
sudo fdisk -lu
sudo blkid
mount
```

---

### Post by germanix on 2013-10-26
Thank you for your response. The file seems to be automaticaly mounted on startup. I did not change anything in the fstab 
Here the output as requested:
jacques@jacques-ThinkPad-X230:~$ sudo fdisk -lu
[sudo] password for jacques: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e05a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   976773119   488385536   83  Linux

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dc206

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   233916415   116957184   83  Linux
/dev/sdb2       233918462   250068991     8075265    5  Extended
/dev/sdb5       233918464   250068991     8075264   82  Linux swap / Solaris
jacques@jacques-ThinkPad-X230:~$ sudo blkid
/dev/sdb1: UUID="3c9eae44-e031-4e11-8a01-2de49cb7713a" TYPE="ext4" 
/dev/sdb5: UUID="683d4293-1eb6-4079-bf5e-14fcdd46b727" TYPE="swap" 
/dev/sda1: LABEL="Data" UUID="9e97e491-92a2-452b-b1aa-17a8200d4544" TYPE="ext4" 
jacques@jacques-ThinkPad-X230:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=jacques)
/dev/sda1 on /media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
jacques@jacques-ThinkPad-X230:~$

The HDD appears in the dock. Left click opens the HDD which is still empty. Right click shows:
Type: Folder
Contents: nothing
Location: slash media slash jacques
permissions tag shows owner as Root

---

### Post by coffeecat on 2013-10-26
There are some things which are puzzling me at the moment.

> **germanix said:**
> The file seems to be automaticaly mounted on startup. I did not change anything in the fstab

I think you mean partition. It won't be automatically mounted at startup unless you add a line to /etc/fstab, at least in Ubuntu. In Ubuntu, you would need to mount it by clicking on it in the file manager -  or using the Disks utility, but the mount details below don't look like the product of Disks. Are you by chance using Kubuntu, or one of the other Ubuntu derivatives? I seem to remember there is another way of mounting partitions in Kubuntu, but I can't remember the details, as I don't use Kubuntu.

Your mount point is this:

> **germanix said:**
> /dev/sda1 on /media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544 type ext4 (rw,nosuid,nodev,uhelper=udisks2)

/media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544. Except that you've allocated the sda1 partition the label "Data":

> **germanix said:**
> /dev/sda1: LABEL="Data" UUID="9e97e491-92a2-452b-b1aa-17a8200d4544" TYPE="ext4" 

In Ubuntu, if you were to mount a partition which has a partition label "Data" with the file manager, the mountpoint will be /media/jacques/Data, not the mountpoint you are seeing which is using the UUID instead of the partition label. Which is why I wonder if you are using Kubuntu.

Assuming the mountpoint is still /media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544, run this terminal command:

```
sudo chown jacques:jacques /media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544
```

If sda1 is still mounted to /media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544, then it will be owned by you and you will be able to use it.

---

### Post by germanix on 2013-10-26
I am running Ubuntu 13.10 with Unity. 
This code did not do the trick: sudo chown jacques:jacques /media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544
I do not see this file in my home file:  /media/jacques. I did not create a media file?
Teh Partition/HDD appears in the Unity Dock on startup and is already mounted but will not let me use it. It opens in a window but belongs to root.
This partition is a primary partition with ext4. I did label it as data but when i open the partition it shows the name 9e97e491-92a2-452b-b1aa-17a8200d4544 in "properties"

---

### Post by coffeecat on 2013-10-26
> **germanix said:**
>  
This code did not do the trick: sudo chown jacques:jacques /media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544

So what error did you see when you ran this command?

> **germanix said:**
>  I do not see this file in my home file:  /media/jacques. I did not create a media file?

You won't see it in your home **folder** (not file) because it is not in your home folder. It is a system folder - /media/jacques.

> **germanix said:**
> Teh Partition/HDD appears in the Unity Dock on startup and is already mounted but will not let me use it. It opens in a window but belongs to root.

Now I understand what you are doing. It appears in the Unity Dock but is not mounted **until** you click on it. It will then be mounted on /media/jacques/*something-or-other*. It's the same mechanism as mounting from the file manager.

My guess is that you had mounted it before you added the label Data to the partition, which is why the mount point you quoted included the UUID in the path. Now that you have added the label Data, it will be mounted to /media/jacques/Data and not to /media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544. In which case, try this:

```
sudo chown jacques:jacques /media/jacques/Data
```

---

### Post by germanix on 2013-10-26
This is what I get with both sets of the code you provided:
jacques@jacques-ThinkPad-X230:~$ sudo chown jacques:jacques /media/jacques/Data
[sudo] password for jacques: 
chown: cannot access ‘/media/jacques/Data’: No such file or directory
jacques@jacques-ThinkPad-X230:~$ sudo chown jacques:jacques /media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544
jacques@jacques-ThinkPad-X230:~$ 

So ithere is no error message with the first line of code but I still cannot use the partition.
by the way i realy appreciate your help.

---

### Post by coffeecat on 2013-10-26
It sounds as though the one with the long UUID worked since there is no error message, so we need to investigate why you still cannot write to the partition.

Post the output of this command:

```
ls -l /media/jacques
```

---

### Post by germanix on 2013-10-26
jacques@jacques-ThinkPad-X230:~$ ls -l /media/jacques
total 4
drwxr-xr-x 3 jacques jacques 4096 Okt 26 13:06 9e97e491-92a2-452b-b1aa-17a8200d4544
jacques@jacques-ThinkPad-X230:~$

---

### Post by coffeecat on 2013-10-26
According to that output, the ownership and permissions on that partition are saying you should be able to use it. What exactly do you mean by not being able to use the partition? What are you doing? What error messages do you see?

Click on the icon in the Unity launcher that corresponds to the partition so that a file browser opens. Try to copy a file to it from your home folder by dragging and dropping. Any file will do. What happens?

---

### Post by germanix on 2013-10-26
The drag and drop to this partion works. When I am in the file browser I cannot  create a new file or new document on that partition. I need to create files there which I then want to symlink to my Home on the SSD. Under "properties - "permissions" the owner is still Root

---

### Post by coffeecat on 2013-10-26
> **germanix said:**
> The drag and drop to this partion works. 

Then everything should be working as it should. 

> **germanix said:**
> When I am in the file browser I cannot  create a new file or new document on that partition.

Then you must be in the wrong place, or you are describing something else. If you can drag and drop to the partition, then you can create new files there. I don't really follow you. If you open the mounted partition from the launcher icon, you are in the file browser. Perhaps if you describe step by step what you are doing that prevents you from creating new files or documents, we will be able to see where the problem is.

I'll make one suggestion before we go any further. The blkid output that you posted earlier shows clearly that you have allocated the label "Data" to partition sda1. Since it is mounted to /media/jacques/9e97e491-92a2-452b-b1aa-17a8200d4544 you must have mounted it before you labelled the partition, otherwise the mount point would be /media/jacques/Data. It will make things a lot easier if it is mounted to /media/jacques/Data because then it will appear as "Data" in the left pane of the file browser and "Data" will appear when you hover the mouse over the launcher icon. 

Either... right-click on the launcher icon and choose "Unmount". Then left-click on the icon to remount it.

Or... Reboot and click on the launcher icon to mount it.

---

### Post by germanix on 2013-10-26
I did what you suggested and it now works. previously I could create files there as the option to do so was greyed out. After I have now unmounted and then remounted it, all is fine. I am very gratefull to you for helping me solve this problem. Perhaps you would also be so kind to explain to me how I can to create symlinks. I wish to have the bulk of my home files like Docs, pictures, music etc. on this partion that now works but with symlinks to the "Home"  partition on the SSD. Could I also move my "dropbox" file to the new partition?
Whatever you decide, you have been very kind and I thank you for all your help. Have a nice day.

---

### Post by coffeecat on 2013-10-26
Symlinks are a great way to achieve what you want, but there is one complication. For symlinks to work consistently, the sda1 partition must be mounted to the same mountpoint every time. Now that you have labelled sda1 as "Data", this will probably happen every time you click on the icon launcher, but another problem will be that if, after booting up, you open your home folder before you click on the launcher icon for Data (and therefore mount it) you will see a number of broken links. They will become unbroken once you mount sda1, but to get over this and to avoid the potential issue of sda1 being mounted to a different mountpoint, you need to add a line to /etc/fstab. I'll post back later with some suggestions for this, but first:

Symlinks. It's easy enough to do from the command line, but it's also easy in the GUI. Try this. Open the Data folder. Create a folder for whatever you want but for the moment avoid names of pre-existing folders in your home, such as Music, Pictures, etc. Let's say "Spreadsheets" for illustration - create a folder called Spreadsheets in Data. You can always delete it later if you don't want it. Once you have a folder called Spreadsheets in Data, right-click on it and choose "Make Link". It will create a link called "Link to Spreadsheets". Of course it's not much use yet as it's sitting in the same location as the target, but we're only half-done. Now open your home folder and drag and drop "Link to Spreadsheets" over to the home folder where it will be copied. You'll find, if you put some stuff in the Spreadsheets folder, that if you open Link to Spreadsheets in your home, it will open in Spreadsheets in Data. You can delete the Link folder in Data now and rename Link to Spreadsheets in home, perhaps to just Spreadsheets.

You can do the same with Music and Pictures and so on, but you'll need to delete the pre-existing folders in home if you want the links to be the same name. I don't know how to get the special icons that are on the home Music and Pictures folders onto the link folders.

I'll post again with some suggestions for /etc/fstab.

---

### Post by oldfred on 2013-10-26
I use symlinks a lot. From both my Linux formatted partition and my older NTFS formatted partition. I prefer /mnt/Data, so then mount does not show in Nautilus. If /media it will also show and can be confusing.

 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

 For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /mnt/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /mnt/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

      ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a


If you have any data in existing folders be sure to back that up. If name already exists link will not work.

 #from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/Data/Music
#Or link all folders with one command:
for i in `echo /mnt/Data/*`;do ln -s $i; done

---

### Post by germanix on 2013-10-27
Thank you very much coffeecat and oldfred. You have been a great help. Surely appreciate all your help. Got it up and running now. You all have a nice day. :lolflag:

---

