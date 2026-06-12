---
title: "Help selecting partitioning options?"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by SSB on 2006-06-08
Ok, I'm at a spot in the installation that I have NO IDEA what to do.

I want my partitions used like this:

[http://img350.imageshack.us/img350/6012/screenshot9cb.png](http://img350.imageshack.us/img350/6012/screenshot9cb.png)

So what options should I put in the remaining partitions? They are all used by windows so I don't want to touch them..

---

### Post by aysiu on 2006-06-08
Yeah, unfortunately, the live CD installer *forces* you to select mount points for *every* partition, regardless of whether you want to use those partitions or not.

Just make up ones for them: /partition1 /partition2 /partition3 ...

You can always delete them from the /etc/fstab later and then ```
sudo rmdir /partition1
``` etc.

---

### Post by SSB on 2006-06-08
OK, I get this error:

The test of the file system with type fat16 in partition #1 of IDE1 master (hda) found uncorrected errors.

Then continue or go back.

---

### Post by aysiu on 2006-06-08
Can you do a Scandisk of that partition from Windows--fix those errors?

---

### Post by gerbman on 2006-06-08
[QUOTE=SSB]OK, I get this error:

The test of the file system with type fat16 in partition #1 of IDE1 master (hda) found uncorrected errors.

Then continue or go back.[/QUOTE]Got the same error on my FAT32 partition. I hit continue and everything went through okay. Back up important stuff if you have any on that drive.

---

### Post by SSB on 2006-06-08
huh.. i just continued through all the errors and it just. closed.

---

### Post by aysiu on 2006-06-08
[QUOTE=SSB]huh.. i just continued through all the errors and it just. closed.[/QUOTE] Well, the live CD installer is a bit obnoxious in that it forces you to mount all your partitions.

If you use the alternate installer CD, you can mount or not mount whatever you choose, and you can choose to not mount the FAT16 partition.

I still think you should try to correct those FAT16 errors in Windows.

---

### Post by SSB on 2006-06-08
ok.. you know that 128 GB partition that I didn't want linux to touch? I never selected to reformat it ANYWHERE.. now in Windows, the drive is no longer there. WHAT HAPPENED TO MY HARD DRIVE. ALL I DID WAS ADD 2 PARTITIONS :(

And to make it all wonderful, I can't figure out how to scandisk this crap in XP. I've googled it but their methods.. don't work! How surprising.

---

### Post by SSB on 2006-06-08
Back in linux.. the drive is showing up as a ton of unallocated space. This is wonderful.

---

### Post by aysiu on 2006-06-08
I feel your pain. I wish I could help.

So it got formatted... but not even with Ubuntu... just blank?

For ScanDisk, I think it's in Start Menu > All Programs > Accessories > System Tools > ScanDisk... I'm not sure, though.

---

### Post by SSB on 2006-06-08
It got formatted.. nothing on it. It's just unallocated. I'm looking for a hard drive recovery utility now. If I can't get it back I'll just start linux from scratch.

Also scandisk does not exist in XP. I got checkdisk, but not even that worked right. It detected one partition.

---

### Post by aysiu on 2006-06-08
[QUOTE=SSB]It got formatted.. nothing on it. It's just unallocated. I'm looking for a hard drive recovery utility now. If I can't get it back I'll just start linux from scratch.[/quote] These may help:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

I haven't used them myself, but I've seen them recommended by other Ubuntu users.

> 
Also scandisk does not exist in XP. I got checkdisk, but not even that worked right. It detected one partition. ScanDisk doesn't exist in XP? Weird.

---

