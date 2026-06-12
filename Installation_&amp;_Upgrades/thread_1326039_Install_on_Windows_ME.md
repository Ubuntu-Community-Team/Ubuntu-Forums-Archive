---
title: "Install on Windows ME"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by markpreston on 2009-11-14
I have an old laptop running Windows ME that I want to load Xubuntu on.  The problem is that the CD drive is out, and I can't seem to find a way to boot a NetLoader.  I have tried pretty much every method here: 
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

I do have a floppy, but I wasn't sure if I could do any good with that.  Any suggestions?

Thanks,

Mark

---

### Post by Herman on 2009-11-14
What other resourses do you have?
A USB drive of any kind?
The availability of a friend's computer who might be kind enough to share it?

---

### Post by Herman on 2009-11-14
If you have another partition in your hard disk such as a data partition or even a recovery partition with at least 700 MB of free space I think I have an idea.

You could download your .iso file for Xubuntu, (make sure it's a 'Desktop' Live/Install CD and not an 'Alternate' CD), and save it to or copy it to your other partition, or to a USB flash memory stick if you have one.
The main thing is it won't be in whichever partition you're going to need to resize when you partition to install Xubuntu.

GRUB2 can boot an .iso file in your hard disk, and GRUB2 can run from a floppy disc.
So you just need to get GRUB2 installed in your floppy disc and boot that, then give GRUB2 the correct commands to boot your Xubuntu installation .iso, and it will run the same as or better than a real CD. :D

---

### Post by markpreston on 2009-11-14
> **Herman said:**
> If you have another partition in your hard disk such as a data partition or even a recovery partition with at least 700 MB of free space I think I have an idea.

You could download your .iso file for Xubuntu, (make sure it's a 'Desktop' Live/Install CD and not an 'Alternate' CD), and save it to or copy it to your other partition, or to a USB flash memory stick if you have one.
The main thing is it won't be in whichever partition you're going to need to resize when you partition to install Xubuntu.

GRUB2 can boot an .iso file in your hard disk, and GRUB2 can run from a floppy disc.
So you just need to get GRUB2 installed in your floppy disc and boot that, then give GRUB2 the correct commands to boot your Xubuntu installation .iso, and it will run the same as or better than a real CD. :D

I followed the links on your post tag, and that looks like what I need, the only other question I have is how to create a floppy from an .img file on an XP machine.  I appreciate the help.

Mark

---

### Post by Herman on 2009-11-14
:oops: I forget how to write an .img file to a floppy disk in Windows.

It's easy from Ubuntu,
```
dd if=bootdisk.img of=/dev/fd0 bs=512 count=2880
```Where 'bootdisk.img' is the name of your floppy disk image file and it's located in your /home/username directory. Feel free to change the name of the file in the command as appropriate. Also if the file is in some other directory it would be best to copy it and paste it to the /home/username directory before running the command.

I think that should work, I don;t seem to be able to buy acceptable quality floppy disks anymore so I got frustrated with them and gave up using them a while back.

---

