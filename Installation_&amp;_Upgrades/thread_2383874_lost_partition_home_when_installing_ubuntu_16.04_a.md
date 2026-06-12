---
title: "lost partition /home when installing ubuntu 16.04 alongside xubuntu 12.04"
date: 2018-01-30
forum: Installation &amp; Upgrades
---

### Post by serghiey on 2018-01-30
Dear Ubuntu Community,

I always find interesting questions and relevant answers in your forums, and this is the first time I really need to ask for more specific help.

I used for many years xubuntu 12.04 and I tried to install ubuntu 16.04 alongside in another partition: I did not want to touch 12.04, until I was sure my hardware was working in 16.04, and the installation instructions let me think that I would preserve my data/pictures/etc, and I would be able to select the previous system.

Hence I have started my 64-bit pc from a USB stick. To do this I had to explicitly go in the BIOS and select the UEFI boot for this device (other options were failing to boot).
When asked, I let the system unmount existing partitions. Updates were not downloaded during installation.

At the end, I encountered a problem similar to this: [https://ubuntuforums.org/showthread.php?t=2331567](https://ubuntuforums.org/showthread.php?t=2331567)

Anyway I was able to still restart the system with 12.04 without any data losses.

I did another attempt, wired connected to internet, I have enabled the download of the updates, including third parties software, and I turned off secure boot inserting a password.
Since there were already the partitions from the previous trial, I used the advanced tool to format those ones. I was carefully selecting only new ones, leaving untouched those existing from 12.04.
When asked, I assigned to one partition the mount point "/" and to the other "/home".

Before proceeding I was warned at a certain point that I might encounter difficulties in booting other installed linux versions. I did not see this message before, and I thought that this would affect only the most recent 16.04 installation, and I decided to proceed (the alternative was ending the installation).

Now I am in big troubles: I cannot start 12.04, since it seems it cannot load /home.
And I still cannot boot 16.04. Further attempts created only more partitions, but I hope to delete them once I have a working system.

I have created a Boot-Info report: [https://paste.ubuntu.com/26491528/](https://paste.ubuntu.com/26491528/)

My first most important question is: can I still recover the data in my past 12.04 /home ?

Next question would be how to get out from this mess, and have a working 16.04 installation that can boot, but first I want to backup all data, if this is still possible.

Any help will be appreciated,
kind regards,

---

### Post by yancek on 2018-01-30
Your Xubuntu appears to be on sda1 so boot your Ubuntu 16.04 and create a mount point for it (mkdir /mnt/sda1) then mount it (mount /dev/sda1 /mnt/sda1) and navigate to /mnt/sda1 to see if the folders/files you want to save are there and copy them to an external device.  Not sure what you have on sda7-sda12?  You appear to have 1604 installs on sda13, 14 and 15.  Boot Ubuntu and run df -h from a terminal and that should show you which partition you are using.  Your fstab file on Xubuntu shows that your /home partition was on sda10, mount that and see if your files are there.

---

### Post by serghiey on 2018-01-30
Thank you for the prompt reply.
I did mount it, and it seems that there are files in folders like "bin", "opt", "lib", "etc", but there are no files in folders as "boot", "lost+found", "usr" and unfortunately "home".
Running df -h shows:

```

ubuntu@ubuntu:/mnt/sda1$ sudo df -h 
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           767M  9.4M  758M   2% /run
/dev/sdg1       1.9G  1.5G  394M  80% /cdrom
/dev/loop0      1.5G  1.5G     0 100% /rofs
aufs            3.8G  184M  3.6G   5% /
tmpfs           3.8G  388K  3.8G   1% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           3.8G     0  3.8G   0% /sys/fs/cgroup
tmpfs           3.8G  1.1M  3.8G   1% /tmp
tmpfs           767M   80K  767M   1% /run/user/999
/dev/sdh1       955M  122M  834M  13% /mnt/usb
/dev/sda1        19G  2.9G   15G  17% /mnt/sda1

```

I tried to mount sda10, there is a "lost+found/" and a user folder, but it contains only an "examples.desktop" file. I believe these partitions sda7-12 were created in one of the 16.04 install attempts.

---

### Post by kansasnoob on 2018-01-31
I hope you had all of your data from 12.04 backed up.

What I can see is its /home was on /dev/sda10:

```
=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8f715daa-7568-413b-a98b-2fafba42cd25 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
UUID=78abf9d8-17e0-4621-b9b6-ca7aff22ea69 /boot           ext4    defaults        0       2
[B]# /home was on /dev/sda10 during installation
UUID=e95e5c01-0c3c-42e0-b8cf-61148bfbebc1 /home           ext4    defaults        0       2[/B]
# /tmp was on /dev/sda7 during installation
UUID=9b3bf10e-d228-4a45-9188-1fe2b5d68be6 /tmp            ext4    defaults        0       2
# /usr was on /dev/sda8 during installation
UUID=73791eb1-36d3-4192-b950-3f11031f291e /usr            ext4    defaults        0       2
# /var was on /dev/sda9 during installation
UUID=a2b36ff6-841a-4d4e-9ec7-6c86700c0650 /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=3cc17759-2691-45b3-b2f5-a8274c92dbcc none            swap    sw              0       0
--------------------------------------------------------------------------------
```

The UUID was  -------------------- e95e5c01-0c3c-42e0-b8cf-61148bfbebc1
But according to BLKID it's now - 4ce8b093-5fd6-48af-b213-7893265abd12

Since the UUID has changed it's safe to assume that you wiped out all of the data from 12.04 :(

If you did not have a complete backup you need to focus on trying to recover as much data as possible. I would start by using a live DVD/USB and just looking at each partition using the file manager to see what's there. If the data is indeed gone:

[https://www.cgsecurity.org/](https://www.cgsecurity.org/)

It's very important that you not make any additional attempts at installing until you recover as much data as possible.

---

### Post by serghiey on 2018-01-31
Thank you very much for spotting this and for your suggestions.
It seems I did not fully realize that I was touching a partition from the system already installed.
I must admit I do not feel very well after discovering this.

Tonight, when I have no child running around, I will try with TestDisk, hopefully I manage to recover as much data as possible.
I will probably format everything and install the 16.04 from scratch, as soon as I have done with it.

I keep you updated as soon as I have news.

---

### Post by serghiey on 2018-01-31
I tried to run TestDisk, and it seems a very powerful tool. Unfortunately I do not have a backup for data that was on disk.
I feel not comfortable in trying to play more. I will ask for assistance at a local data recovery business center to hopefully recover most of them.

---

