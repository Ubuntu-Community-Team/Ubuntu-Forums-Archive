---
title: "installed ubuntu on harddrive and erased data"
date: 2017-01-31
forum: Installation &amp; Upgrades
---

### Post by surielgabriel on 2017-01-31
Hi,
after trying Ubuntu on USB for a while I have decided to install it.
the PC had 3 partition:
1)boot (I do not remember the size): where I could get the pre-installed Windows 7 and install it when needed
2) C: (150 GB)--> where there was Windows 7
3) D: (150 GB)--> where I had DATA (all my documents, media..)

After installing Ubuntu with a lot of enthusiasm and less preparation, the computer has:
1) /dev/sda1
2)/dev/sda2 (extended) 300GB
       /dev/sda5 (lvm2 pv) mount point - ubuntu-vg - 300GB

I have lost all my personal data on D: I have no words about it...

My aim is to be able to have a list of the file in my old drive D: and being able to copy them somewhere (external hard drive). My aim is also to learn from my mistakes and back up next time...
I have found online an overwhelm of info and similar experiences in forum and they do not apply (or I am not able to apply them) and theoretically I have understood that testdisk is an outstanding tool: I have tried it and I have found different disks (more than the ones I have just listed), I have also found 5-6 red files at some point with some 'deep search', some file was very big in numbers (sectors???) but no particular friendly name.
My problem is that I have found lists of  data I cannot recognise, a grammar I do not know at all (ext4, sda2, dm-0, start with 3 numeric column, drwxr-xr-x) and I do not have a clue about what to do in practice next. I have managed to run testdisk from usb and now that PC is on only throu USB. I am stuck. Is there any graphical software I can use? Maybe from another computer?

I trust Ubuntu, the alternatives it offers, but I also need to learn a lot and I guess I need a lot of help from you.
Thank you in advance,
sg

---

### Post by TheFu on 2017-01-31
Before doing anything like installing, upgrading or repartitioning, always have a 100%-know-you-can-recover backup. Learn this, if nothing else.  Versioned backups solve over 1,000 problems that nothing else can solve. Mirrored backups solve about 50 problems.

Testdisk doesn't recover file names, just data and perhaps the extension based on the data, IMHO. There is no "GUI", just the TUI.

That "grammar" means something and the drwxr-xr-x is basic Unix permissions - extremely critical to understand on any Unix-like system. Did you choose encryption during the installation? Also, it appears you chose to use LVM, which is great when you understand what it means, but makes data recovery just a little harder for someone completely new.  LVM adds another layer of flexibility & complexity for how storage is managed on Linux. Server admins use it religiously, but for average desktop users it isn't used very often unless they specifically select it during the install.

It might be possible to get some Windows data back - just depends on how much was overwritten.  Any overwritten data is effectively gone, unless you have a backup.

If my wedding photos were on that disk, I'd start by getting another, new disk, and make a bit-for-bit copy of the {old disk} to the {new disk}, then perform all my data recovery touching only the new disk. Never touching the old disk until I'd completely given up.

As you will learn, having a backup is 10,000x easier than dealing with testdisk or photorec tools.  There are commercial tools for data recovery, but I've never known anyone to use them. Have friends in the data recovery and forensics industry. They can do amazing things using specialized software AND specialized HW, but they aren't cheap. They teach a 4 day class just in how to use the equipment, but expect nearly expert level knowledge about the 50 different file systems used today across the major OSes as a prerequisite.

Wish I could provide more hope.  Usually after I post this, someone will come along with hope and some ideas that might work. Cross your fingers.

---

### Post by DuckHook on 2017-01-31
Hello surielgabriel

Although there may be no guarantees, surely there is hope and most certainly there is encouragement.

Read TheFu's post very carefully. It is very useful. The most important part in what he says is the following:> **TheFu said:**
> &#8230;I'd start by getting another, new disk, and make a bit-for-bit copy of the {old disk} to the {new disk}, then perform all my data recovery touching only the new disk. Never touching the old disk until I'd completely given up.This is so, so important. DO NOT use that old disk. For anything. Take it out of your computer right now so that you do not overwrite any more of that disk. Do not power it up again until you have a new disk, and then only power it up long enough to make a clone from it.

The following links will help:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[https://ubuntuforums.org/showthread.php?t=1958605](https://ubuntuforums.org/showthread.php?t=1958605)

Although the situation is dire, there is hope that you may be able to recover at least *some* of your data. The first link contains further instructions on just how to make a bit-for-bit copy.

We are cheering for you and wishing you good luck.

---

### Post by TheFu on 2017-01-31
DuckHook - The 2nd link is broken above.

---

### Post by DuckHook on 2017-01-31
> **TheFu said:**
> DuckHook - The 2nd link is broken above.Thanks.

…and fixed.

---

### Post by surielgabriel on 2017-02-01
THANK YOU SO MUCH FOR YOUR WORDS. I will have a look at the links as soon as I can.
Regards,
sg

---

### Post by TheFu on 2017-02-01
Ok - looking through that fixed link.  

Spinrite is for something else, not what you have. I own it. Never use it anymore. Something like badblocks and periodic data migrations (any method, but ddrescue works for those hard to read sectors just as well) does the same stuff that spinrite does (without all the marketing hype).  Not useful in your situation.

Haven't used the other tools. I'd go with the DataRecovery guide first.  But never touch the source disk. That is rule 1, 2, 3, 4, 5. Never touch the source. Always work from a copy.

---

### Post by surielgabriel on 2017-02-06
I have managed to get hold on a new external hard drive and I have been readying the following files, as prayers..
[COLOR=#000000]The following links will help:[/COLOR]

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[https://ubuntuforums.org/showthread.php?t=1958605](https://ubuntuforums.org/showthread.php?t=1958605)

I have clear idea about backing up next time and also I have worked only on Live USB. Now I would like to recover the partition. I would like to double check the steps before actually doing it:
1) working only from Live USB with internet connection 
2) using Testdisk or Parted or Gpart to find the guessed partition
3) create an image with DD rescue
4) save that image to an external drive
5) analyse the content of that image on external hard drive to rescue possible data

Is this work flow correct? Am I missing anything.

Thank you,
sg

---

### Post by DuckHook on 2017-02-06
[-X  No.

[https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive](https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive)

[LIST=1]
[*]The ***first*** step is to clone your drive. Use gddrescue as per above instructions. It produces an exact bit-for-bit clone. Other apps might call what they do "cloning", but they may not actually produce a bit-for-bit clone.
[*]Then disconnect your original drive. Only touch it again if you have to clone it again.
[*]All further attempts to retrieve data are done on the *cloned* drive, including restoring the partition table.
[*]If you mess up your retrieval attempt, simply clone the original again and start over.
[/LIST]
***!!Do not attempt to repair partition table on original drive!!***

---

### Post by TheFu on 2017-02-06
Nope.

**create an image with DDrescue is first.** Before everything else.
Only work on the new image. Nothing else.

Think you'll need to use other tools, not testdisk, if my memory if the issue is close, but it has been awhile and I could be wrong.

By the time you are 5% into this process, you will agree that having backups are much easier. That is how I learned that lesson - only after losing 80% of my data.

---

### Post by surielgabriel on 2017-02-07
Hi, thank you guys!
I am trying to prepare the external hard drive in order to save the original drive image.
From Gparted I can read that the original drive has /dev/sdc2 'extended' File System and a branch (the only one) dev/sd5  'lvm2 pv' File System
I was thinking to partition the external drive into 2 parts:
-partition 1 which will includes the image from the laptop drive (300Gb)
-partition 2 which will includes the file I save from the image

questions:

1) how do I format my external hard drive? 2 partitions on ext4? shall I use Gparted?
2) workflow question: after having the image on partion 1, I use something like Photorec to rescue data, right? Can I see the actual file or is it just a bunch of numbers? Can I copy what I need to partition 2?

It takes a lot, I am learning a lot, I feel like a snail, but I will not give up!

Thank you for the info and support.

---

### Post by TheFu on 2017-02-07
If the new disk is larger than the old one, use dd from the beginning to the end - that will copy all the bytes, including the partitioning and all formats. You don't need to format anything.
```

$ sudo ddrescue source target  /path/to/log/file
```

**source** would be the old drive device ... something like /dev/sdh - your value WILL BE DIFFERENT.
**target** would be the new drive device ... something like /dev/sdz - your value WILL BE DIFFERENT.
the log file needs to NOT be located on either device used for the source or target.  Also, boot off a flash drive, that would be where I put the log file.

---

### Post by surielgabriel on 2017-02-07
at the moment I am on ubuntu live usb trying to move the image from the laptop to the external harddrive and saving the logfile on a 2nd USB.
 is it what I am meant to do?


after 
$ sudo ddrescue source target
I have added
/path/to/log/file
which of course did not work. i have sorted out it needed a new path. So I have this extra USB /dev/sdd/ which I entered at the end of the command:
$ sudo ddrescue source target  /dev/sdd/ --force


or
$ sudo ddrescue source target  /dev/sdd/logfile --force

Please note that source and target have been changed accordingly. 
I have also added '--force' because it could not write otherwise.
Here the output
[IMG]https://drive.google.com/open?id=0B5LJ3HWCCY5ZNzRGVUFfdkZwV3NVcXlrNVBiME5JbG9YSzk4[/IMG] 
[https://drive.google.com/open?id=0B5LJ3HWCCY5ZNzRGVUFfdkZwV3NVcXlrNVBiME5JbG9YSzk4](https://drive.google.com/open?id=0B5LJ3HWCCY5ZNzRGVUFfdkZwV3NVcXlrNVBiME5JbG9YSzk4)
(not sure how to add pics from desktop)

At some point it asks to create the logfile, I guess, but there is an error
ddrescue : Error writing logfile'/dev/sdd/logfile': Not a directory 
Fix the problem and press ENTER to retry

or 

ddrescue : Error writing logfile'/dev/sdd/': Is a directory 
Fix the problem and press ENTER to retry

what's wrong?
please help

---

### Post by TheFu on 2017-02-07
Using force will probably wipe something you didn't intend. Bad idea, IMHO.

The /path/to/log/file ... needs to point to a real, mounted, filesystem location, not a device.  Something like /tmp/log.file provided that is on a different disk than the source or target.

It would be helpful if you always posted the EXACT command used.

And if you always use "code tags" , so it jumps out and lines up correctly.

---

### Post by surielgabriel on 2017-02-07
> **TheFu said:**
> Using force will probably wipe something you didn't intend. Bad idea, IMHO.

The /path/to/log/file ... needs to point to a real, mounted, filesystem location, not a device.  Something like /tmp/log.file provided that is on a different disk than the source or target.

It would be helpful if you always posted the EXACT command used.

And if you always use "code tags" , so it jumps out and lines up correctly.

Thank you for the 'code tags' recommendation. I do not know how to do it, but I am now reading on the forum FAQ how to do that properly.

I am not sure to understand the /tmp/log.file example you are kindly sharing.

You suggest not to have it in the source or target. So I have this spare USB (Gparted calls it /dev/sdd1), how can I instruct to save it there?

many thanks

---

### Post by DuckHook on 2017-02-11
> **surielgabriel said:**
> … So I have this spare USB (Gparted calls it /dev/sdd1), how can I instruct to save it there?In all 'nixes, you must first "mount" a device before it is accessible and can be written to. In your case, you might just do:```
sudo mount /dev/sdd1 /mnt/usbstick_log
```…then point your logfile to:```
/mnt/usbstick_log
```

---

