---
title: "Ubuntu Hangs During Installation"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by Qbert on 2011-03-26
I have a HTPC PC that I built.  The specs are"

Motherboard - Biostar MCP6P M2+
CPU - AMD Athlon x2 5050e
Memory - 2GB PC6400
Hard Drives - 2x2TB 5400RPM, 50GB OCZ SSD
Video - ATI 5450

I'm trying to install Ubuntu 10.10, but keeps hanging.  It runs fine from the disc.  Basically, it hangs at the part where you get to the point where pick the drive to install it on.  The first time, it let me pick the OCZ SSD, where I'd I'd like to install the OS, but then I got some weird error message and after that I could select one of the 2TB drives as the drive.

I don't know if this is a problem, but my board doesn't support AHCI mode.  I had some trouble with this installing Windows too, but once I got the nVidia storage drivers installed, everything worked fine in Windows.  Has anyone else seen this before or have a possible solution?  Thanks for any help.

---

### Post by mörgæs on 2011-03-26
Have you tried adding boot options? 

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by Qbert on 2011-03-27
Thanks mörgæs.  No, I've not tried the boot option because I don't know what they are or how to use them.  I think and I could be wrong my board doesn't support AHCI, which is why it's having trouble seeing my SSD.  I need to figure out if possible how to get it to work.  Would it be possible to make an install partition with say gparted and install it that way?  I'll poke around the boot options to see if I can find anything.  Thanks again.

---

### Post by Rubi1200 on 2011-03-27
From the LiveCD, post the output of this command:

```
sudo parted -l
```

(lowercase L not 1)

Once pasted here, highlight all text and click on # from the toolbat to wrap with code tags.

Thanks.

---

### Post by Qbert on 2011-03-27
Thanks Rubi.  Here's what it says:

Model: ATA Hitachi HDS5C302 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary  ntfs         boot


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sdb: 50.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  50.0GB  50.0GB  primary  ntfs


Model: ATA Hitachi HDS72202 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

---

### Post by Qbert on 2011-03-28
I did find [this]("http://ubuntuforums.org/showthread.php?t=1595809&page=4") via google.  It would seem I'm not the only one having this problem.  It says in there this can be fixed by adding pci=nocrs to the kernel boot options.  This unfortunately would be beyond my level of ability.  Is there an easy way to do this?  Thanks for any help.

---

### Post by mörgæs on 2011-03-28
Did you read the links in my posts above? Really, it is not difficult.

---

### Post by Qbert on 2011-04-01
I did figure out how to get that option at boot, but it didn't seem to help.  I'm going to try to install the beta of Natty Narwhal to how that goes.  Thanks for the help.

---

### Post by Rubi1200 on 2011-04-01
Natty is in beta, that means bugs and other issues. Unless you like testing and don't mind having to fix broken installs I would recommend you try 10.04 instead.

---

### Post by Hedgehog1 on 2011-04-01
> **Rubi1200 said:**
> Natty is in beta, that means bugs and other issues. Unless you like testing and don't mind having to fix broken installs I would recommend you try 10.04 instead.

+1 on loading 10.04 LTS - it is stable and polished.  You have enough issues to resolve without having to guess if every error is your hardware or the beta-OS.

***The Hedge***

:KS

---

### Post by Qbert on 2011-04-02
Thanks for the replies.  11.04 has the same issue as 10.10.  It won't see my SSD when I go to install it.  I tried 10.04.  It boots up with the Unbuntu logo with the dots underneath.  When it finishes that, it stops outputting signal to the monitor.  It just says no signal.  At this point I don't know what to do.

---

