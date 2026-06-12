---
title: "Did a fresh install of 18.04 over 16.10 and Home folder is only 12 gb"
date: 2018-08-17
forum: Installation &amp; Upgrades
---

### Post by eddugo on 2018-08-17
Running Dell E5470 with dual boot Windows 10 and now 18.04.  After erasing 16.10 and installing 18.04 the home folder is only approx 12 gb.  Not sure what the partitions should look like - size wise.

Thank you in advance for help

Ed

---

### Post by Impavidus on 2018-08-17
Let's see some details. Could you run the following commands in a terminal and show us the output?```
sudo parted -l
df -h
```

---

### Post by eddugo on 2018-08-17
```
Warning: failed to translate partition name
Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  524MB  523MB   fat32           EFI system partition          boot, esp
 2      524MB   659MB  134MB                   Microsoft reserved partition  msftres
 3      659MB   151GB  150GB   ntfs            Basic data partition          msftdata
 6      151GB   151GB  1049kB
 9      151GB   173GB  22.0GB  ext4
 7      173GB   480GB  307GB   ext4
 8      480GB   490GB  10.0GB  linux-swap(v1)
 4      490GB   490GB  472MB   ntfs                                          hidden, diag
 5      490GB   500GB  9922MB  ntfs                                          hidden, diag


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdb: 63.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  63.1GB  63.1GB  primary  fat32        lba


ed@ed-Latitude-E5470:~$
```

---

### Post by Impavidus on 2018-08-18
And the output of```
df -h
```

The contents of /etc/fstab could be interesting too.```
cat /etc/fstab
```

What do you mean exactly by the home folder is only 12 GB? I don't see any partition of 12 GB.

---

### Post by eddugo on 2018-08-18
I hope I am thinking correctly.  Home (ed) contents plus available space.  oops actually 10.9 gb.  I have attached an image of the home folder properties.

```
ed@ed-Latitude-E5470:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           787M  2.1M  784M   1% /run
/dev/sda9        21G   13G  6.6G  66% /
tmpfs           3.9G  225M  3.7G   6% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0       15M   15M     0 100% /snap/gnome-logs/37
/dev/loop1      2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop3      141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop4       87M   87M     0 100% /snap/core/5145
/dev/loop5      3.4M  3.4M     0 100% /snap/gnome-system-monitor/36
/dev/loop6      1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop7      5.0M  5.0M     0 100% /snap/canonical-livepatch/42
/dev/loop2       21M   21M     0 100% /snap/gnome-logs/25
/dev/loop8      3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop9       87M   87M     0 100% /snap/core/4486
/dev/loop10      13M   13M     0 100% /snap/gnome-characters/69
/dev/loop11      13M   13M     0 100% /snap/gnome-characters/103
/dev/loop12     141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/sda1       495M   35M  461M   7% /boot/efi
tmpfs           787M   16K  787M   1% /run/user/120
tmpfs           787M   80K  786M   1% /run/user/1000
/dev/sdb1        59G  151M   59G   1% /media/ed/EXTRA DRIVE
ed@ed-Latitude-E5470:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=c2f18ff2-dd25-4013-8fb5-f78e5fae4fdb /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=FCA3-F88C  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
ed@ed-Latitude-E5470:~$
```

---

### Post by Impavidus on 2018-08-18
OK, we're getting somewhere. I'm guessing your 16.10 system had a root, /home and swap partition, but your new 18.04 has everything in the root partition.

You don't have a separate /home partition. Your entire system is installed in /dev/sda9, which is about 20GB. That's a decent size for a root partition. There's also /dev/sda7, which is currently unused and pretty big. It could very well be a /home partition. Did you have a separate /home partition while running 16.10? In that case all your documents are probably still there.

Have a look at /dev/sda7. Is there anything in it you still need? If not, you can wipe it clean. Then use this guide to convert your /dev/sda7 into a /home partition: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
If you want to keep some contents from /dev/sda7, merge it with the stuff you move from your /home directory, which will put it in your /home directory.

I also see you have a swap partition, but your 18.04 system uses a swapfile. It doesn't really matter which of the two you use, but currently the swap partition is just unused disk space. If you use the swap partition instead of the swapfile, you can delete the swapfile and reclaim some space in your /dev/sda9. I don't know the size of your swapfile, but getting the space back may come in handy.

And all of that can be done without changing any partitions.

If anything is unclear, ask it. Errors here can lead to data loss. The output of```
sudo blkid
```may help to give us specific instructions.

---

### Post by eddugo on 2018-08-18
Yes I did have a separate home partition for the 16.10.  About 2 AM this morning I realized that all this sounded very familiar so I got up and looked at my history with this forum.  Sure enough, this machine ( I use 3) when it was new Feb 2017, had the same problem - Olfred helped with it and we moved the home folder.

I do like your idea.  I checked the contents of partition 7 (/dev/sda7) and it is the home folder from 16.10.  I will wipe it clean as it's all backed up.  After I send this I will work on moving the home folder to /dev/sda7.

Don't know how to delete the swap file.

ed@ed-Latitude-E5470:~$ sudo blkid
[sudo] password for ed: 
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: LABEL="ESP" UUID="FCA3-F88C" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="83259681-f23b-41e9-9011-fe2d14fb3bed"
/dev/sda3: LABEL="OS" UUID="5E60A6A060A67E81" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="9da9ec5f-4983-4f02-b26d-1d95ea4e0072"
/dev/sda4: LABEL="WINRETOOLS" UUID="5A927A7D927A5E07" TYPE="ntfs" PARTUUID="8606b9c7-8059-4a17-93cc-6d91828c67f7"
/dev/sda5: LABEL="Image" UUID="2E627BA1627B6C89" TYPE="ntfs" PARTUUID="8bea1ed3-f40e-430a-8914-68d474029de7"
/dev/sda7: UUID="caf146c3-99b0-4d46-a9de-8686183a4788" TYPE="ext4" PARTUUID="a23244e4-c29d-4e1b-8cf6-716fd5b0bfbb"
/dev/sda8: UUID="713bc9fa-b2eb-4eaa-9c44-fab5d29dcd7c" TYPE="swap" PARTUUID="71ddb767-f547-44ff-af23-c49c1796e1c5"
/dev/sda9: UUID="c2f18ff2-dd25-4013-8fb5-f78e5fae4fdb" TYPE="ext4" PARTUUID="099a6287-1f63-403f-af48-533e1b561564"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/sdb1: LABEL="EXTRA DRIVE" UUID="2425-1F3D" TYPE="vfat"
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="2e574dc5-6007-4600-ad7b-36946c9fa921"
/dev/sda6: PARTUUID="0565ec34-bb96-4ae0-8286-99d057b08643"
/dev/sdc1: LABEL="FreeAgent Drive" UUID="349C1A0D9C19C9EE" TYPE="ntfs" PARTUUID="a4b57300-01"
ed@ed-Latitude-E5470:~$

---

### Post by eddugo on 2018-08-18
P.S. I went to delete the contents of the /dev/sda7 and I could not find a menu with "cut", "delete" or move to trash.  What is the best way to wipe that clean?

---

### Post by #&amp;thj^% on 2018-08-18
> **eddugo said:**
> 
Don't know how to delete the swap file.


```
sudo swapoff -a -v
sudo rm /swapfile
#back up /etc/fstab: if needed i just threw this in. ;)
sudo cp /etc/fstab /etc/fstab.bak
sudo sed -i '/\/swapfile/d' /etc/fstab
```

---

### Post by #&amp;thj^% on 2018-08-18
> **eddugo said:**
> P.S. I went to delete the contents of the /dev/sda7 and I could not find a menu with "cut", "delete" or move to trash.  What is the best way to wipe that clean?

If you have no further use for it then you could just reformat it:
```

sudo mkfs.ext4 /dev/sda7
```
This will format it to "ext4" just to be clear.

---

### Post by Impavidus on 2018-08-19
> **1fallen said:**
> ```
sudo swapoff -a -v
sudo rm /swapfile
#back up /etc/fstab: if needed i just threw this in. ;)
sudo cp /etc/fstab /etc/fstab.bak
sudo sed -i '/\/swapfile/d' /etc/fstab
```
That will indeed delete the swap file, but you may want to add the swap partition to your fstab. Maybe you don't really need it, but the swap partition exists already so there's not really any reason not to use it. After you deleted the swap file with above instructions, you can activate the swap partition with```
echo 'UUID=713bc9fa-b2eb-4eaa-9c44-fab5d29dcd7c none swap sw 0 0' | sudo tee --append /etc/fstab
sudo swapon -a
```That will add the quoted line at the end of your fstab, then activate the swap space.

> **1fallen said:**
> If you have no further use for it then you could just reformat it:
```

sudo mkfs.ext4 /dev/sda7
```
This will format it to "ext4" just to be clear.
Note that this may change the UUID of your /home partition, so use sudo blkid again to find its UUID before putting it in your /etc/fstab according to the instructions in the guide I linked earlier.

---

### Post by eddugo on 2018-08-20
In the link, under Setup Fstab;  Is the date code wrong?  What should that look like?

ed@ed-Latitude-E5470:~$ sudo blkid
[sudo] password for ed: 
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: LABEL="ESP" UUID="FCA3-F88C" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="83259681-f23b-41e9-9011-fe2d14fb3bed"
/dev/sda3: LABEL="OS" UUID="5E60A6A060A67E81" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="9da9ec5f-4983-4f02-b26d-1d95ea4e0072"
/dev/sda4: LABEL="WINRETOOLS" UUID="5A927A7D927A5E07" TYPE="ntfs" PARTUUID="8606b9c7-8059-4a17-93cc-6d91828c67f7"
/dev/sda5: LABEL="Image" UUID="2E627BA1627B6C89" TYPE="ntfs" PARTUUID="8bea1ed3-f40e-430a-8914-68d474029de7"
/dev/sda7: UUID="36f3fc96-524d-4aeb-a4ee-93df96de6760" TYPE="ext4" PARTUUID="a23244e4-c29d-4e1b-8cf6-716fd5b0bfbb"
/dev/sda8: UUID="713bc9fa-b2eb-4eaa-9c44-fab5d29dcd7c" TYPE="swap" PARTUUID="71ddb767-f547-44ff-af23-c49c1796e1c5"
/dev/sda9: UUID="c2f18ff2-dd25-4013-8fb5-f78e5fae4fdb" TYPE="ext4" PARTUUID="099a6287-1f63-403f-af48-533e1b561564"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="2e574dc5-6007-4600-ad7b-36946c9fa921"
/dev/sda6: PARTUUID="0565ec34-bb96-4ae0-8286-99d057b08643"
ed@ed-Latitude-E5470:~$ sudo cp /etc/fstab /etc/fstab.$(date +18-08-20)
ed@ed-Latitude-E5470:~$ cmp /etc/fstab /etc/fstab.$(date +18-08-20)
ed@ed-Latitude-E5470:~$ sudo gedit /etc/fstab 

** (gedit:692): WARNING **: 05:46:24.194: Set document metadata failed: Setting attribute metadata::gedit-position not supported
ed@ed-Latitude-E5470:~$

---

### Post by Impavidus on 2018-08-20
What they mean is exactly what they write:```
sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)
```You can also use```
sudo cp /etc/fstab /etc/fstab.2018-08-20
```which is exactly the same today. The $(date ...) thing runs the date command and puts the output (today's date) on the command line as part of the cp command. But it's not important, as this is just the name of the backup file.

BTW, never run **sudo gedit**. I know the guide says so, but don't. Running that can have nasty consequences, like making it impossible to login. There are several alternatives, either running gedit with some precautions or using a terminal-based text editor:```
gedit admin:///etc/fstab
sudo -H gedit /etc/fstab
sudoedit /etc/fstab
sudo vim /etc/fstab
...
```Running graphical application, acting as root user, requires some precautions to prevent the application from changing other files to root-owned. In the opinion of the devs, you simply shouldn't run graphical applications as root user.

---

### Post by eddugo on 2018-08-21
Sorry about the questions, but I am trying to do this right.  I have gotten into trouble before using the terminal.

When adding the line in text editor;

(identifier) Do I put in the entire output from sudo blkid ?

(some settings)  what do they want there?

---

### Post by Impavidus on 2018-08-21
For the identifier you use the UUID as given by blkid, for settings those given in the guide are good enough, unless you really know what you're doing. You use an ext4 partition, not ext3 as in the guide, change that too. So you can put this line in /etc/fstab:```
UUID=36f3fc96-524d-4aeb-a4ee-93df96de6760    /media/home    ext4    defaults    0    2
```
And later change /media/home to /home.

---

### Post by eddugo on 2018-08-21
Ok, after reboot, it still goes to the old home file - guess I did something wrong.  /dev/sba7 has almost all the home folder contents 31,269 items old home, 31,192 items on sba7.  It moved, but I must have fowled up changing sba7 to home.  i now have an icon shortcut for the sba7 on my desktop.

---

### Post by Impavidus on 2018-08-22
Did you follow the entire guide? Can you show us the contents of your /etc/fstab? Show output of these commands:```
sudo blkid /dev/sda7
cat /etc/fstab
ls /home
ls /old_home
ls /media/home
```Maybe we can see what went wrong.

---

### Post by eddugo on 2018-08-22
I thought I did.  Wonder if I missed a line??

ed@ed-Latitude-E5470:~$ sudo blkid /dev/sda7
[sudo] password for ed: 
/dev/sda7: UUID="36f3fc96-524d-4aeb-a4ee-93df96de6760" TYPE="ext4" PARTUUID="a23244e4-c29d-4e1b-8cf6-716fd5b0bfbb"
ed@ed-Latitude-E5470:~$ 


cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=c2f18ff2-dd25-4013-8fb5-f78e5fae4fdb /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=FCA3-F88C  /boot/efi       vfat    umask=0077      0       1
UUID=713bc9fa-b2eb-4eaa-9c44-fab5d29dcd7c none swap sw 0 0
UUID=36f3fc96-524d-4aeb-a4ee-93df96de6760    /media/home    ext4    defaults    0    2
ed@ed-Latitude-E5470:~$ 


ls /home
ed
ed@ed-Latitude-E5470:~$ 


ls /old_home
ls: cannot access '/old_home': No such file or directory
ed@ed-Latitude-E5470:~$ 


Hmm, looks like old home creation didn't work.

ls /media/home
ed  lost+found
ed@ed-Latitude-E5470:~$

---

### Post by oldfred on 2018-08-22
Your /home needs to be at start of partition, not a lower level folder.
If using an old install, you need to move /home to its own partition so correctly mounted.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by eddugo on 2018-08-22
Hi Olfred

I just did that and something went wrong.  Home folder is copied to /dev/sda7.   Where would I pick up on those directions to make it recognize the move.  or do I have to do the whole process over?? UPDATE:  Picked up on directiond right after where it copied the files and it worked - will mark "solved"

---

### Post by Impavidus on 2018-08-23
Right, you just forgot the final part of the guide (from "Preparing fstab for the switch").

Click thread tools&#8594;mark as solved to mark this thread as solved.

---

### Post by eddugo on 2018-08-23
Thanks to all for your help

---

