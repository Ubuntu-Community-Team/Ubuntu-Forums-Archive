---
title: "Windows drive will not mount"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2011-03-20
New 10.10 desktop installation on an Acer Aspire 5515 32 bit Vista Home Basic/ 3 GB RAM.  

There was no option during the Ubuntu installation to select the Windows partition/drive for access via the Ubuntu installation, and the drive does not now appear in "Places."

The reason I used 10.10 was because the 10.04 installation on the same machine also would not allow mounting of the Windows drive.  However, there was an option to select the Windows drive during the 10.04 install.

Couple of things I noticed that were "different."  

1) During the 10.04 installation (over which the 10.10 install now resides) there was an option to select either or both of the two user accounts - both administrative - in the Vista installation.  I hadn't noticed that before on previous installations.  I choose both accounts for later importing, but, again, there was no option to mount the drive upon the finished Ubuntu installation.

2) There could be an issue with what I did with the partition/naming on the Vista installation.  Upon restoring to factory settings, I deleted the (10 GB!) restore partition and resized Vista to occupy the newly opened space.  But the GRUB entry for Vista says "Windows Recovery Environment" instead of "Windows" or whatever it usually does.  

Everything else about this dual-boot installation system is just fine: everything boots and updates and so forth.  

But I really need that Windows drive to mount so that my friend's kids can import iTunes and other files from Windows to Ubuntu.  I also want to be able to run Avast scans on Windows from Ubuntu.

I did rummage around a bit by way of locating a solution for this problem, but I can't find anything which "works" or is on point.  

Thanks in advance,
Scott

---

### Post by Zimmer on 2011-03-20
What should be a quick fix is to right click on one of the Gnome panels (top or bottom)
 and add DISK MOUNTER.

This will display each partition with a drive icon and a left click on an icon will give you the option to mount/unmount the drive shown.

The other (long story) way is to look up how to alter your FSTAB file to mount these partitions at login...

---

### Post by vanadium on 2011-03-20
Adding the partition to /etc/fstab is the way to go in your case, and is not really that difficult. It is a three liner.

1) Make a mount point, e.g. /mnt/windowspartition
2) Look up the UUID of your partition in the output of "sudo blkid"
3) Add the mounting parameters as one additional line in your /etc/fstab
```

UUID=...  /mnt/fstab  ntfs  auto,fmask=111,dmask=000,utf-8  0   0

```

Now you can reboot, or immediately have the new mounting in effect with the command "sudo mount -a"

See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for some insights in /etc/fstab.

---

### Post by sks24 on 2011-03-24
Thank you both.

I looked at the fstab documentation.  

Uh, could I ask you to hold my hand on this?  

So, I opened a terminal and typed

```
sudo mkdir /media/windows
```

and then entered the password and then pressed "enter" and received no error message.

Here is the "sudo blkid" output:

```
sissy@sissy-desktop:~$ sudo blkid
[sudo] password for sissy: 
/dev/sda1: UUID="242CC0252CBFEFC2" TYPE="ntfs" 
/dev/sda5: UUID="0c8c6420-e3b4-4505-b993-b275be338faa" TYPE="ext4" 
/dev/sda6: UUID="e6db5ada-8967-4e36-9db3-aae40d19fead" TYPE="swap" 
sissy@sissy-desktop:~$ 
```  

Assuming I've done everything correctly so far,  . . . well, this is the part where I need the hand holding: what, exactly, would I need to type in the terminal to allow for mounting of the sda1 drive?

Thanks so much for your help.

SKS

---

### Post by areeda on 2011-03-24
My technique is to go use the Places menu to open the Windows partition and then 

cat /etc/mtab

I get:
/dev/sda2 /media/Windows7_OS fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

If I put that in fstab it will do it on startup.

Although I'd probably put the mount point at /windows or /home/joe/c instead of /meda/<something> for convenience.

Joe

---

### Post by vanadium on 2011-03-25
You could indeed try the trick of sks24, but it might be that you will not have write permissions on the drive if you do that.

Otherwise, it will work with this line
```

UUID="242CC0252CBFEFC2" /media/windows ntfs fmask=0111,dmask=0000,utf-8 0 0

```

To insert that line, first open /etc/fstab as root (system administrator)
```

gksudo gedit /etc/fstab

```
Supply your normal user login password.

Add the line to the bottom of the file, and save and exit the editor.

Mount the partition (and check whether all is good)
```

sudo mount -a

```
No output should appear. If there is no output, you will be able to access your drive navigating to /media/windows. It will be automatically remounted on each reboot.

---

### Post by sks24 on 2011-04-04
Thank you all very much for the assistance.  I'll be visiting my friend soon, so I'll give this a shot, and then get back to this wonderful forum with an update!

---

