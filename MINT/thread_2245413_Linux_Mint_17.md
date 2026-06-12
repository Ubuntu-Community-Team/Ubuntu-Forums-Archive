---
title: "Linux Mint 17"
date: 2014-09-23
forum: MINT
---

### Post by Thomas_Niccolai on 2014-09-23
Dear Ones:

I am working with two distributions Ubuntu 14.01.1 and Linux Mint 17. I currently have Mint 17 set up on a thumb drive. Is there a way to add some space so I can save documents to the thumb drive. I didn't get a chance to do this during setup and was wondering how I can add space after creating the thumb drive. This would be for Home file. I also need to set up fire fox and I don't know what to do to get it to connect. I would be asking Mint but have yet to figure out how to create a new post on their forum.


Sincerely


Tom

---

### Post by slickymaster on 2014-09-23
*Moved to the ***Other Operating Systems and Projects*** sub-forum*

---

### Post by Rob Sayer on 2014-09-23
Good luck with Mint support ... I've had mint installed on my netbook twice and had to come here to find someone who could answer my questions.

You do know that Mint is just a slightly older version of Ubuntu, right?

---

### Post by QIII on 2014-09-23
While it is true that Ubuntu is upstream of Mint, it is not accurate to say that Mint is just an older version of Ubuntu any more than it is accurate to say that Ubuntu is just a version of Debian.

Mint is *based *on Ubuntu, but it is a distinct distro.

@Thomas_Niccolai:  can you describe how you installed Mint?

---

### Post by Thomas_Niccolai on 2014-09-23
I installed mint on a 4GB Kingston thumb drive using a pen drive universal installer. It installed but I did not get the chance to set aside 1 GB of space for files. It boots and saves documents but when I log out and turn the computer off...When I go back in the document I just saved is gone so I have no space on the drive to save files to...I want to experiment and set up fire fox and email while I have the live thumb drive so I don't bother my windows 7 computer.


Sincerely


Tom

---

### Post by nerdtron on 2014-09-23
> **Thomas_Niccolai said:**
> I installed mint on a 4GB Kingston thumb drive using a pen drive universal installer. It installed but I did not get the chance to set aside 1 GB of space for files. It boots and saves documents but when I log out and turn the computer off...When I go back in the document I just saved is gone so I have no space on the drive to save files to...I want to experiment and set up fire fox and email while I have the live thumb drive so I don't bother my windows 7 computer.


Sincerely


Tom

Well, it's possible to add persistence after the initial thumbdrive install but it's a bit complicated for a beginner.
Since there is no persistence on the drive, I assume you won't lose any data. Just format the drive in FAT32 and reinstall again Mint 17 with persistence of 1 GB. It would just take a few minutes and you won't fiddle with the command line.

---

### Post by tgalati4 on 2014-09-23
Otherwise use gparted and see if you can reclaim any unused space and create an ext2 or fat32 partition and use that as a "data" partition.  Then you can mount that and make it a permanent mount in /etc/fstab.

But I agree with nerdtron, create a new boot thumb drive with the correct persistance in the disk creator.  It will make things much easier.  Don't expect the thumb drive to last very long.  Running off of a flash drive will shorten its life due to frequent, small writes.

---

### Post by ibjsb4 on 2014-09-23
This does not add up to me.

I just installed Mint then update and upgrade.  When I run 'df -h' I am told that 4.8G has been used.

This is virtualbox, so there is some overhead.

---

### Post by tgalati4 on 2014-09-23
I believe the LiveUSB is compressed with space allocated for user files and /etc (configuration files).  It is decompressed on the file when running a live session in RAM.  When I created a Linux Mint MATE 17 LiveUSB it used about 3 GB for system files with 1 GB for user files on a 4 GB stick.  

On a fresh, hard disk install with *google-chrome* and a few user files:

> 
gates@GNAS ~ $ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        70G  **6.0G**   60G  10% /


---

