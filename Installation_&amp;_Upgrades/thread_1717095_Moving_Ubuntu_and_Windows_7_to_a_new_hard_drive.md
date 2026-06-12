---
title: "Moving Ubuntu and Windows 7 to a new hard drive"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by avada on 2011-03-29
Hi!
I bought a new hard drive, and I thought that I'd move the OS-es there from my ageing HDD. I wanted bigger partitions for them so I copied all the files with a live cd, to the partitions I created on the new drive. I had some can't copy special file errors in /dev so I chose skip to all.
Anyway. When it was done I tried to boot with super grub disk. It only saw the linux partitions. It seemed to be booting fine, but at the end didn't load the login screen. I tried installing grub from command line, but that failed too with: "can't open /etc/sudoers: Permission denied"



What should I do now?

---

### Post by Sean Moran on 2011-03-29
Can you connect the two hard disks at once, with the new one as /dev/sda (hd0) and the old one as /dev/sdb (hd1)?  Then if you can, use the gParted on the Live CD to partition the new drive with 16Gb for Windows 7 on the first primary partition of the new disk.

Then shut it down and install Windows 7 from the DVD.

Now you've got Win 7 running on the new hard disk. After you've got Office running and all good, shutdown and boot back to the Linux Live-CD.  Create /dev/sda2 as an 8Gb (8192Mb) ext4 primary partition using gParted.

Create an extended partition as /dev/sda3 using everything except some space at the end, the size of your computer's RAM x 2. ie, if you have 2Gb RAM, make the extended partition everything minus 4096Mb at the end.

Now make /dev/sda4 your SWAP partition at the end.

Finally, you can create logical parttions as you like, for data ir for testing or for archives of mp3s or movies, or however you like to sort your data.  Keep a partition for FAT32 or NTFS especially for Windows data.

Congratulations!  

You have Windows 7 already installed, and your new hard disk is partitioned and ready ti install Linux.  Go ahead and install Ubuntu, and set the root partition (/) as /dev/sda2.  You'll only need half of the 8Gb.  You might also prefer to set one of your logical partitions as /home.  16Gb is more than enough, because you're going to make sure to sort out your data onto different partitions from now on, so all the latest stuff will be copied somewhere more particular at the end of the month.

So, at this point, take a look over your old hard disk on /dev/sdb and copy all the old data onto the most suitable partitions on the new hard disk, and Bob's your uncle!

---

### Post by coffeecat on 2011-03-29
> **avada said:**
> What should I do now?

Start over. Sorry.

You don't mention what happened with Windows but you can't clone a Windows installation by simply copying files and folders. You need to use an imaging application such as Acronis or Macrium Reflect Free from within Windows. I believe you can use clonezilla, but I've never used this myself.

For Linux, you can in fact do a simple file copy but you have to take certain precautions, particularly all the permissions and ownerships must be copied as is. The fact that you get  permission denied with /etc/sudoers suggests you didn't cover this point. If you run cp as sudo with the correct options, you can (almost) clone a Linux root fileysystem. Not clone it in the strict sense of the word, but near enough for practicality. If you run:

```
sudo cp -a
```...you'll get a recursive copy with permissions and attributes retained. But there's a big however. A BIG HOWEVER.

The destination partition will not have the same UUID as the source one. You will need to fix this because /etc/fstab will reference the old UUID. Also, grub will need to be re-installed and updated because it too will have the wrong UUID.

---

### Post by avada on 2011-03-29
> **coffeecat said:**
> Start over. Sorry.

You don't mention what happened with Windows but you can't clone a Windows installation by simply copying files and folders. You need to use an imaging application such as Acronis or Macrium Reflect Free from within Windows. I believe you can use clonezilla, but I've never used this myself.

For Linux, you can in fact do a simple file copy but you have to take certain precautions, particularly all the permissions and ownerships must be copied as is. The fact that you get  permission denied with /etc/sudoers suggests you didn't cover this point. If you run cp as sudo with the correct options, you can (almost) clone a Linux root fileysystem. Not clone it in the strict sense of the word, but near enough for practicality. If you run:

```
sudo cp -a
```...you'll get a recursive copy with permissions and attributes retained. But there's a big however. A BIG HOWEVER.

The destination partition will not have the same UUID as the source one. You will need to fix this because /etc/fstab will reference the old UUID. Also, grub will need to be re-installed and updated because it too will have the wrong UUID.
Thanks for the info! I didn't mention windows because it didn't appear in the grub bootdisk, so I couldn't even boot it. Now that I look at the files all the permissions were stripped, that can't be good. Also there is another problem. A few files were uncopiable when I copied them from under linux. Probably because of bad sectors. Which were not much of a problem under ubuntu, but seem to remember making windows useless when it hits the kind of thing. Anyway. I'll investigate the windows thing more.

---

### Post by coffeecat on 2011-03-29
If you've got bad sectors on the old drive that are not being reallocated by the HD firmware then you've got a failing drive. And you're not going to get a good clone if some of the filesystem is on bad sectors.

Even so, if you can run Windows from the old drive, here's the webpage for Macrium Reflect Free:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

I've used it; it's dependable; and it's free as in beer. Which is nice! :)

---

### Post by avada on 2011-03-30
> **coffeecat said:**
> If you've got bad sectors on the old drive that are not being reallocated by the HD firmware then you've got a failing drive. And you're not going to get a good clone if some of the filesystem is on bad sectors.

Even so, if you can run Windows from the old drive, here's the webpage for Macrium Reflect Free:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

I've used it; it's dependable; and it's free as in beer. Which is nice! :)
As it turned out I didn't have to use it. I got a missing or corrupt winload.exe error. Which I repaired with the windows 7 install disk. Even grub wasn't wiped. I also removed all registry keys from HKEY_LOCAL_MACHINE\SYSTEM\MountedDevices, and set the SystemBootDevice to an empty string in HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control and HKEY_LOCAL_MACHINE\SYSTEM\ControlSet002\Control in the copied registry file. Not sure this was actually necessary though, but it was recommended elsewhere.
After that I only had to fix the drive letters.

I also lost all permissions, probably because I copied the files under ubuntu. So I added proper permissions.

With linux I had no problems after using cp -a. Only one thing. I couldn't copy the files so that new root would have the same permissions as the old, so I did that manually with chown/chmod.

Thanks for the help!

---

### Post by Mark Phelps on 2011-03-30
Have you checked your activation status in Win7 since the move?  If it is a Retail copy, then it should reactivate automatically.  It might say something like three days left to reactivate -- at which point, if you choose the Activate Online option, it should reactivate OK.

If it was an OEM copy (came preinstalled on a PC), then it will most likely NOT reactivate, and since you can't legally migrate an OEM copy from one PC to another, if Win7 thinks that because this is a new HDD, it is also a new PC, you may be stuck.

If that happens, I would then suggest you go to the Windows 7 forums (sevenforums.com) and look through their Windows Upddates & Activation subforum for advice on how to proceed.

---

### Post by avada on 2011-03-30
> **Mark Phelps said:**
> Have you checked your activation status in Win7 since the move?  If it is a Retail copy, then it should reactivate automatically.  It might say something like three days left to reactivate -- at which point, if you choose the Activate Online option, it should reactivate OK.

If it was an OEM copy (came preinstalled on a PC), then it will most likely NOT reactivate, and since you can't legally migrate an OEM copy from one PC to another, if Win7 thinks that because this is a new HDD, it is also a new PC, you may be stuck.

If that happens, I would then suggest you go to the Windows 7 forums (sevenforums.com) and look through their Windows Upddates & Activation subforum for advice on how to proceed.
Thanks for the notification. Its an MSDNAA copy. It shows its activated, in the system settings, so it reactivated itself or stayed activated (if possible).

---

### Post by avada on 2011-08-29
Hi again!
Since the damned exchange HDD is dying too. I had to copy the ubuntu partition again...
This time I had different problems.
There were some files that I couldn't copy because of I/O error. And it seems that some of the are related to the video driver because the desktop doesn't load.
These files weren't copied
> cp: reading `usr/lib/x86_64-linux-gnu/dri/libgallium.so': Input/output error
cp: reading `usr/lib/x86_64-linux-gnu/dri/libdricore.so': Input/output error
cp: reading `usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2': Input/output error
 
How can I determine which package they belong to and how do I reinstall them?

---

### Post by Mark Phelps on 2011-08-29
As you said, this time you had "different problems" ...

So, it would be best if you started a new thread for these new problems ... because, most likely, they're totally unrelated to moving Win7 to a new drive.

---

### Post by avada on 2011-08-29
> **Mark Phelps said:**
> As you said, this time you had "different problems" ...

So, it would be best if you started a new thread for these new problems ... because, most likely, they're totally unrelated to moving Win7 to a new drive.

Well, the thread is for both OS's...

---

### Post by westie457 on 2011-08-29
Hello.
Personally I would have used ```
dd if=/dev/sda of=/dev/sdb
``` running a terminal from a LiveCD Desktop.

This is a byte for byte copy to a new hard drive preserving HDD and partition IDs and all file permissions for the OSes.

After that any partitioning work to be done is done with Gparted also with a LiveCD.

Any changes to the Windows partition have to be checked by booting into Windows. Here chkdsk should run automatically.

I/O errors caused by bad sectors on the failing hard drive or even bad sectors on the new hard drive should be corrected automatically.

---

### Post by YesWeCan on 2011-08-29
+1
I use
```
dd if=/dev/sda of=/dev/sdb bs=64k conv=notrunc,noerror
```

see: [http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

and for copying:
```
cp -ax
```

---

### Post by avada on 2011-08-30
> **westie457 said:**
> Hello.
Personally I would have used ```
dd if=/dev/sda of=/dev/sdb
``` running a terminal from a LiveCD Desktop.

This is a byte for byte copy to a new hard drive preserving HDD and partition IDs and all file permissions for the OSes.

After that any partitioning work to be done is done with Gparted also with a LiveCD.

Any changes to the Windows partition have to be checked by booting into Windows. Here chkdsk should run automatically.

I/O errors caused by bad sectors on the failing hard drive or even bad sectors on the new hard drive should be corrected automatically.

Well, I didn't want an exact copy of a hard drive also, since I got fed up with sector errors (and the sluggishness of hard drives) I got an SSD. 

Anyway... Anyone on how to replace the missing files / reinstalling the packages?

---

### Post by coffeecat on 2011-08-30
> **avada said:**
> 
Anyway... Anyone on how to replace the missing files / reinstalling the packages?

If you made a note of every file that you got an I/O error with you could identify which package it belonged to and then chroot into the broken system from a live CD/USB session and re-install all of the packages.....

.... in theory!

Personally, I would back up any personal data and do a fresh re-install. You were copying from a dying hard drive. You don't know whether any files you copied that didn't give I/O errors were corrupted.

---

### Post by avada on 2011-08-30
> **coffeecat said:**
> If you made a note of every file that you got an I/O error with you could identify which package it belonged to and then chroot into the broken system from a live CD/USB session and re-install all of the packages.....

.... in theory!

Personally, I would back up any personal data and do a fresh re-install. You were copying from a dying hard drive. You don't know whether any files you copied that didn't give I/O errors were corrupted.

Since now I have considerable experience with dying HDD's I think its unlikely that other files are corrupted.

My main trouble is with figuring out to which packages the files belong. I also can boot to command line, so I guess I could reinstall the packages without the use of a live-cd.

---

