---
title: "clone issues using dd"
date: 2016-10-09
forum: Installation &amp; Upgrades
---

### Post by ken18 on 2016-10-09
For the past 2 years I've been faithfully cloning my dual-boot laptop HDD (Win 10 + Ubuntu 14.04) every few months using dd if=/dev/sda of=/dev/sdd bs=1M from an Ubuntu-Live USB.  Due to recent problems with Windows (won't boot after an update) I had my first occasion to perform a reverse clone (dd if=/dev/sdd of=/dev/sda bs=1M) from my most recent clone.

I can now boot Windows but get an error message every time (Scanning and repairing drive (\\?Volume{....}), but Ubuntu won't boot at all (just blank screen after I choose Ubuntu from the boot menu).

Is there anything obvious from the above explanation what I've done wrong and/or what I should do?

P.S. I've always had fast boot turned OFF

---

### Post by sudodus on 2016-10-09
If you clone (from one drive to another drive), the target drive must be of exactly the same size or larger. It means that if the target drive is larger, you should be able to boot from it without issues, but if you restore, it will be to a smaller drive, which will cause problems. These problems can be repaired, if no partition extends beyond the cutoff limit. I think you can do it with

- ***fixparts*** for a MSDOS partition table (MBR)

- ***gdisk*** for a GUID partition table (GPT)

-o-

I prefer the ***Clonezilla*** tool for this kind of cloning for backup. And I create an image (a directory with a set of compressed files). Clonezilla is smart enough to only clone the used blocks (and skip free blocks), which makes the process much faster. (Clonezilla also wants the target drive to be of exactly the same size or larger. But the drive where you store the images is not affected by this limit. I store several Clonezilla images on two external hard disk drives.

[clonezilla.org](clonezilla.org)

---

### Post by frostschutz on 2016-10-09
dd makes bit perfect copies. assuming nothing messed with either  device during the copy or afterwards, sda should look exactly like it  did before you created the copy. In theory there should be no problems. In practice there are some pitfalls to consider.

What is /dev/sdd? Is it attached at all times? Is there any guarantee nothing will try to modify it? Cloning devices like this is a huge problem: suddenly you have duplicate partition uuids, filesystem uuids, mounting will mount the wrong side of things, even Windows might be confused by it. If anything was mounted while making this copy or depending what happened any time you connected this device - the copy just might no longer be good.

Apart from that there is nothing wrong with cloning this way. There is no issue with disk size, unless sdd was too small to hold the copy in the first place, or you hit an read error with a bad sector, in this case you need ddrescue instead of dd.

---

### Post by ken18 on 2016-10-09
sdd is an external USB attached HDD the exact same size as the HDD I cloned.  It was only attached when I made the initial clone and was never attached again until I tried to restore.  Here are the steps I used to restore:

1. Started with complete shut down laptop
2. Inserted Ubuntu Live-USB device and booted from it
3. Once booted, attached source clone via USB
4. Use disk utility to confirm that that laptop hdd was sda and the usb hdd was sdd
5. Opened terminal window and issued dd command

Can I be sure the Ubuntu Live-USB system didn't alter something on sdd?  No, but I don't know what precaution I could have taken.

If this approach has so many problems, what is the right or recommended way to do it?

P.S. I remember a couple of years ago spending a lot of time evaluating different methods (dd, Clonezilla, Macrium Reflect, maybe one more) and at the time concluded that dd was the cleanest least error prone method of anything I tried.  I don't specifically remember what issues I had with the non dd methods, but it was the clear winner as I recall.  One of the things I really disliked about images was that my files were locked into a binary file and totally inaccessible to me).  Now, obviously, I'm having 2nd thoughts.

---

### Post by sudodus on 2016-10-10
It seems you cloned the drive with a good method, which should create no problems. Unless you are affected by a problem described by frostschutz, it should work.

- Please check again, if the source and target drives are of exactly the same size. Not only nominally, but exactly the same number of bytes.

- and check if the drives have the same sector sizes.

You can use ***parted***, for example 

```
sudo parted /dev/sdx unit b print
```

- and check if one of the drives has bad sectors (bad blocks). That can cause big problems. The drive must be **un**mounted.

You can use the program ***badblock*** directly for the whole device, but if you want to mark the bad blocks in the root partition (to avoid them), it is a good idea to use it via ***e2fsck***.

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number (for the root partition with an ext4 partition).

---

### Post by ken18 on 2016-10-10
Thanks for the replies.  Just for kicks I used dd to restore to an even earlier clone (before I upgraded to Win 10 but that shouldn't matter) and it worked perfectly.  Thus, there must have been something wrong with the first clone I used.  Fortunately, I've used two different clones in a round robin fashion.

I guess this just shows the danger of cloning, whether it be an image or a byte-for-byte clone.  You never know the operation is successful until you do a restore, which is a horrible time to find out it doesn't work!

---

### Post by sudodus on 2016-10-10
It shows, that you should always ***test your backup*** - at least the backup routines and methods, maybe not every instance. You cannot rely on a backup that is not tested. And you should test it by restoring to a 'third' drive. Do not take the risk to destroy the original drive by restoring from a bad backup.

It also shows, that it is a good idea to have at least two backups, which you have.

I'm glad you found a solution :-)

If you think that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

### Post by frostschutz on 2016-10-10
Maybe consider cloning to a file, instead of a raw disk, unless you want to be able to just pop the raw disks in where the original disk used to be... (saves you the time for copying back)

It's easier to protect files from tampering (chmod -w, chattr +i) than raw disks (which are mounted partitioned picked as install target and overwritten etc. nilly-willy by well-meaning live systems and install cds).

---

### Post by ken18 on 2016-10-10
Wow, this is bringing back all of the gyrations I remember going through a couple of years ago.  I understand the potential benefit of images vs raw clones, but the downside with images is my data is locked away in a binary file.  An obvious workaround is to periodically backup the data files separately from making clones/images.  Maybe not a bad way to go I suppose.


Re testing, the only way I can think to do it (other than removing the 20 screws on the rear cover of my laptop and physically replacing the HDD) is to modify the UUID of the clone so it doesn't conflict with the original (in the laptop) and see if it will boot when attached via USB.  Trouble is, this can't test the Windows boot!  Unless I'm willing to physically replace the hdd in the laptop, I don't see how testing can be done with a Windows-Linux dual boot system. 


In the end we need to choose a method that has a reasonable chance of working and not so onerous that we don't follow the strategy.  Maybe the right thing to do is to use images/clones ONLY to prevent a lot of potential work to rebuild a system after some catastrophe and hope/pray that it will work if you need it.  Data backup should be a totally separate activity that is done more frequently than imaging/cloning, which is basically what I'm doing right now.  Full circle.

---

### Post by sudodus on 2016-10-11
I agree. I backup my system like that, a complete clone to prevent a lot of potential work to rebuild a system after some catastrophe, and frequent backup of data files with another method. I use ***rsync*** and ***unison*** for that purpose, but there are many tools, that work well. Try a few of them, and stay with one that works well for you.

-o-

I think you are exaggerating :-D No computer that I have seen needs 20 screws to get into the hard disk drive bay. My Toshiba has only one screw, and my Lenovo has three screws. It is rather quick and easy to switch an internal drive in most laptop computers (except some very old ones).

---

### Post by ken18 on 2016-10-11
You got me! I did exaggerate.  There are only 14 screws.  It's a 3-year old Toshiba and I had the cover off for a month while I tested various backup/cloning schemes.  When I put it back together I was 3 screws short, which of course the local computer shop didn't carry.  So, now it's held on by 11 screws.  In the end I vowed to never remove the cover again.

---

### Post by sudodus on 2016-10-12
Strange that our Toshibas are so different! I bought my Toshiba in April 2013, so it should be about the same age, [satellite-pro-c850-19w](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w), and the lid of the drive bay has only one single screw.

---

### Post by ken18 on 2016-10-12
Mine is a low end model [https://www.amazon.com/Toshiba-P55-A5312-i5-4200U-1-60GHz-Windows/dp/B00XF0MBKO](https://www.amazon.com/Toshiba-P55-A5312-i5-4200U-1-60GHz-Windows/dp/B00XF0MBKO). The RAM bay has a 1-screw lid but the entire bottom cover needs to be removed to access the hdd.

Oh, I forgot to mention that each screw was hidden by an adhesive backed rubber plug that had to be pried out in order to access the screw.  Since the screws are on curved surfaces, the plugs have a continuously variable thickness around the circumference, so the orientation had to be just right when putting them back in.  Of course, about 1/3 of the rubber plugs would not stay in when I re-assembled.  Also, I think they weren't all the same size.  Lastly, somewhere along the way I cracked the cover either by prying it off too aggressively or by tightening one of the screws w/o seating the adjacent portion of the cover properly.  Thus, my one time disassembly operation resulting in 3 lost screws, several non-functional rubber plugs, and a cracked cover.

To wrap this up, I've come to the following conclusions:

1. My cloning strategy is sound
2. My choice of laptops make a critical step (i.e. testing the image/clone) impractical

---

