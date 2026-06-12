---
title: "Missing 32gb SSD"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by rabiabidabi on 2010-02-16
Hi,
I've had my eee 1000 for 1 year. Right before Christmas, I had a problem with my webcam crashing the computer. That was remedied, but since then my 32gb secondary SSD is not in the File System of the System Monitor. It is in the BIOS.

I found a shell command that, I think, checks the hard drives and this what I get:

robert@robert-laptop:~$ sudo fdisk -l
[sudo] password for robert: 

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00067983

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c7743

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3316    26635738+  83  Linux
/dev/sdb2            3317        3924     4883760    5  Extended
/dev/sdb5            3317        3924     4883728+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)


robert@robert-laptop:~$ cat/etc/fstab
bash: cat/etc/fstab: No such file or directory
robert@robert-laptop:~$ 


Does this tell me anything?

Thanks for your time,
Rob

---

### Post by prshah on 2010-02-17
> **rabiabidabi said:**
> 
Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c7743

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3316    26635738+  83  Linux
/dev/sdb2            3317        3924     4883760    5  Extended
/dev/sdb5            3317        3924     4883728+  82  Linux swap / Solaris

Your 32Gb is recognized, here. However, it may not be mounted. To check, give the command```
mount|grep sdb
```

To troubleshoot more, please post the output of the above command as well as ```
cat /etc/fstab
``` (Note the space between the cat command and the filename).

Can you also tell us about your setup? Eg, is Ubuntu installed on the 32Gb drive?

---

### Post by rabiabidabi on 2010-02-17
Good morning and thanks for your reply. I ran the 2 commands in the Terminal, the first gave me no response.

robert@robert-laptop:~$ mount|grep sdb
robert@robert-laptop:~$ mount|grep sdb
robert@robert-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7491cbba-c6f6-4871-b3c5-a66cb07f12d1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b8d411a9-5cc4-4197-9d45-28ae50dc00b1 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
robert@robert-laptop:~$ 


Ubuntu is mounted on the 8gb hard drive. I keep all my files on a WD 500gb external drive, which I purchased after I found that the 32gb was missing. Also, I have an external optical drive (Asus) and speakers and a wired mouse.

Thanks,
Rob

---

### Post by prshah on 2010-02-18
> **rabiabidabi said:**
> 
robert@robert-laptop:~$ mount|grep sdb
robert@robert-laptop:~$ cat /etc/fstab

Ubuntu is mounted on the 8gb hard drive. I keep all my files on a WD 500gb external drive, which I purchased after I found that the 32gb was missing.

OK your drive is recognized (as from previous post) but not mounted (as with above output). Try manually mounting it```
sudo mount -t ext3 /dev/sdb1 /mnt -o defaults,ro
``` If successful, there will be no message. Please check "/mnt" to see if your files are accessible. The drive is currently mounted read-only (ro), and you cannot make any changes/new files. If everything is OK, and you want to use it regularly, please post back for details on how to "integrate" the new drive in your /etc/fstab file.

Post back with error output if you run into problems.

---

### Post by rabiabidabi on 2010-02-18
Woohoo! There it is! Thanks  prshah, you deserve a hill of Ubuntu beans.

Yes, I would like to use the drive so I need instructionns on how to integrate it.

You are the man.

Rob

---

### Post by rabiabidabi on 2010-02-18
Well, I came home from work and turned on my eee, checked the system monitor and the drive was not mounted. I ran the commands again and the drive was mounted, restarted and the drive was again not mounted in the system monitor.



robert@robert-laptop:~$ sudo mount -t ext3 /dev/sdb1 /mnt -o defaults,ro
[sudo] password for robert: 
robert@robert-laptop:~$ /mnt
bash: /mnt: is a directory
robert@robert-laptop:~$ 

I have to admit, I am enjoying this. That 32gb drive has become my Holy Grail.

Thanks again,
Rob

---

### Post by prshah on 2010-02-18
> **rabiabidabi said:**
> 
Yes, I would like to use the drive so I need instructionns on how to integrate it.

Please see [this post]("http://ubuntuforums.org/showpost.php?p=8156948&postcount=5") for details on how to make an entry for your ext3 partition in the /etc/fstab file.

Please post back with details if you have any problems. (You probably will, with permissions issues, if you have installed/reinstalled Ubuntu with this drive "out-of-the-loop").

---

### Post by rabiabidabi on 2010-02-18
No luck. I can mount the device manually, as per your earlier posts, but it is not mounting with the #/dev/sdb1...command. 

This is everything I did:

robert@robert-laptop:~$ sudo blkid /dev/sdb1
[sudo] password for robert: 
/dev/sdb1: LABEL="HOME" UUID="14091da3-055d-401b-b93f-16dcd4d90360" SEC_TYPE="ext2" TYPE="ext3" 
robert@robert-laptop:~$ sudo mkdir /media/sdb1  sudo chown root:plugdev /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
mkdir: cannot create directory `sudo': File exists
mkdir: cannot create directory `chown': File exists
mkdir: cannot create directory `root:plugdev': File exists
mkdir: cannot create directory `/media/sdb1': File exists
robert@robert-laptop:~$ # /dev/sdb1 UUID=14091da3-055d-401b-b93f-16dcd4d90360   ext3   defaults,relatime,auto 0     1
robert@robert-laptop:~$ 




robert@robert-laptop:~$ sudo mkdir /media/sdb1
[sudo] password for robert: 
mkdir: cannot create directory `/media/sdb1': File exists
robert@robert-laptop:~$ sudo chown root:plugdev /media/sdb1
robert@robert-laptop:~$ # /dev/sdb1 UUID=14091da3-055d-401b-b93f-16dcd4d90360   ext3   defaults,relatime,auto 0     1
robert@robert-laptop:~$ sudo mount -t ext3 /dev/sdb1 /mnt -o defaults,ro
robert@robert-laptop:~$  # /dev/sdb1 UUID=14091da3-055d-401b-b93f-16dcd4d90360   ext3   defaults,relatime,auto 0     1
robert@robert-laptop:~$ 

When the dev wouldn't mount the first try, I manually mounted it, then ran the new command. I did not get an error, but the dev is not on my system monitor-file systems.

Thanks again,
Rob

---

### Post by rabiabidabi on 2010-02-18
How did those smilies get in there?

robert@robert-laptop:~$ sudo blkid /dev/sdb1
[sudo] password for robert: 
/dev/sdb1: LABEL="HOME" UUID="14091da3-055d-401b-b93f-16dcd4d90360" SEC_TYPE="ext2" TYPE="ext3" 
robert@robert-laptop:~$ sudo mkdir /media/sdb1  sudo chown root:plugdev /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
mkdir: cannot create directory `sudo': File exists
mkdir: cannot create directory `chown': File exists
mkdir: cannot create directory `root:plugdev': File exists
mkdir: cannot create directory `/media/sdb1': File exists
robert@robert-laptop:~$ # /dev/sdb1 UUID=14091da3-055d-401b-b93f-16dcd4d90360   ext3   defaults,relatime,auto 0     1
robert@robert-laptop:~$ 




robert@robert-laptop:~$ sudo mkdir /media/sdb1
[sudo] password for robert: 
mkdir: cannot create directory `/media/sdb1': File exists
robert@robert-laptop:~$ sudo chown root:plugdev /media/sdb1
robert@robert-laptop:~$ # /dev/sdb1 UUID=14091da3-055d-401b-b93f-16dcd4d90360   ext3   defaults,relatime,auto 0     1
robert@robert-laptop:~$ sudo mount -t ext3 /dev/sdb1 /mnt -o defaults,ro
robert@robert-laptop:~$  # /dev/sdb1 UUID=14091da3-055d-401b-b93f-16dcd4d90360   ext3   defaults,relatime,auto 0     1
robert@robert-laptop:~$

---

### Post by rabiabidabi on 2010-02-18
I see it is the letter'p"   lol, too funny.

---

### Post by prshah on 2010-02-19
> **rabiabidabi said:**
> No luck. I can mount the device manually, as per your earlier posts, but it is not mounting with the #/dev/sdb1...command. 

```
/dev/sdb1: LABEL="HOME" UUID="14091da3-055d-401b-b93f-16dcd4d90360" SEC_TYPE="ext2" TYPE="ext3"
``` 

Easy things first: To prevent conversion of text into smilies, enclose the output in "code" tags, eg [code ] ...output... [/code ]

#dev/sdb1... is not a command. Those lines are supposed to be added into your /etc/fstab file.

However, a new point has cropped up. 

As per your output, the 32Gb was (is?) your /home directory (possibly). This is why I asked for more information about your setup; eg, have you recently reinstalled?

However, adding the lines to your /etc/fstab should not cause any harm. There is also no need to create the /media/sdb1 directory, because it already exists.

Post back if you still have problems, for a more step-by-step guide.

---

### Post by rabiabidabi on 2010-02-19
You are a very patient man, PRshah.

I added the code to the /etc/fstab in gedit and saved. No mount.

My eee came with 8.10 installed. I upgraded to 9.04 and everything was fine until my webcam crashed. I re-installed and everything was fine except the 32gb was not mounted. I recently replaced 9.04 with eeebuntu 3.0, which is, I believe, still 9.04. All my apps work and the eee hums along nicely with no problems, except the 32gb is still not mounted. I keep my files on an external hdd, and only need the 32gb for apps. I currently am using 3.8 gb of  the 7gb available on the primary hdd.

Rob

---

### Post by prshah on 2010-02-20
> **rabiabidabi said:**
> 
I added the code to the /etc/fstab in gedit and saved. No mount.

I re-installed and everything was fine except the 32gb was not mounted.

only need the 32gb for apps. I currently am using 3.8 gb of  the 7gb available on the primary hdd.


After saving the /etc/fstab, you need to reboot. If you did that, and it still didn't mount, please post the output of ```
cat /etc/fstab
mount|grep -E sdb\|home
```

I'm guessing that in your earlier setup, the 32GB drive was setup to hold "/home" which is where all your user created and user-specific files and settings are stored.

When you have reinstalled, you have defined a single partition of "/", which includes "/home". So, in your current installation, "/home" also resides on your 7GB (unless you have put "/home" on the external drive, which I doubt).  This information may be wrong, and may not be of any importance to you; I'm just giving it out for your knowledge for the future.

I don't see how you can use the 32GB for "apps", but let's not go there now. First, lets just focus on getting it mounted.

---

### Post by rabiabidabi on 2010-02-20
Yes, I reboot after adding to the /etc/fstab. No mount.

robert@robert-laptop:~$ cat /etc/fstab mount|grep -E sdb\|home
cat: mount: No such file or directory
/dev/sdb1: LABEL="HOME" UUID="14091da3-055d-401b-b93f-16dcd4d90360" SEC_TYPE="ext2" TYPE="ext3"
robert@robert-laptop:~$ 

When I had 8.10, and then, 9.04 standard installed, it used almost all of the 7gb hdd. So, when I tryout music players other than rythmbox, the downloads went to the 32 gb drive. That's what I mean by putting apps on the drive.

I have not put/home on the external drive. Also, I unmount the external drive before I perform the tasks you have assigned.

As always, thanks for your help,
Rob

---

### Post by rabiabidabi on 2010-02-21
Well, I think I have had success.

I entered the following in /etc/fstab:

# 32GB SSD Drive
UUID=14091da3-055d-401b-b93f-16dcd4d90360 /media/sdb1 ext3 defaults 0 2

The drive is mounted as /media/sdb1. The "HOME" icon appears on the desktop, which is new. Is that a problem?

So, unless the icon on the desktop denotes an error of some sort, I'd say this problem is solved.:D

Thanks again, PRshah, for all your help. 

Rob

---

