---
title: "Grub died after Partion Magic"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by sterne on 2006-11-09
After much playing around with different packages and keeping the ones that I like, I found that I was running out of space.  The disk usage analyser showed that most of my disk space was used in a single folder and I didn't really want to have multiple mount points in funny places, so I decided to try and **resize my root partition**.

Hmmm...  Probably a bad idea that...

I'm running a fairly old laptop in which the CD-ROM is broken, so I tried creating a bootable USB pen drive.  After much experimentation following the guides at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) with no luck I tried to resize the partition from Windows using Partition Magic (despite several posts on the forums saying how PM and Linux don't play well together).  Partition Magic reported a perfect resize with *no* errors.  However when I boot up and choose Ubuntu, I just get a single screen saying "GRUB".

Using Partition Magic I can browse the root partition and even copy things over to a large FAT32 partition (which has all my user data).
[B]
Is there any way to get back to a bootable Ubuntu, given that I don't have a CD-Rom, and it appears I can't boot off a USB stick?  I can however examine and edit files on the root partition[/B]

For those who want technical details:
Running a Toshiba Satellite 2450, with partitions as follows:
1 - Primary - NTFS - Windows XP (10 GB)
2 - Extended - 
      Logical - FAT32 - My Data (20GB)
      Logical - EXT3 - /boot (50MB)
3 - Primary - EXT3 - Ubuntu root partition (7GB)
4 - Primary - SWAP - (502MB)

I resized the data partition down, and moved the /boot partition with gparted, and all was well.
I'm using the Windows bootloader to start everything.  My Partion Magic is version 8.  Ubuntu had just been upgraded to Edgy.

On the one hand this isn't serious, I do have a working version of Windows, and can be productive etc.  On the other I was enjoying using Edgy, and was making a concerted effort to come over to the world of free software.

Any ideas?

Thanks for your time

     -Philip.

---

### Post by babooka on 2006-11-09
Do you have a floppy drive?

---

### Post by sterne on 2006-11-09
I have a usb floppy drive, pretty sure I can't boot off it.  But that is an idea, now to find a working floppy disk....

---

### Post by Sef on 2006-11-10
Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").  Only need a cd-rom/rw.

> Using Partition Magic....

PM and Linux don't mix well.  Use [GParted]("http://gparted.sourceforge.net/") instead.

---

