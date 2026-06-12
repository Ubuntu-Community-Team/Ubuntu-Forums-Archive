---
title: "Want to start all over"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by knuttypk on 2008-06-24
So i installed ubuntu hardy heron and i like it but i want to completely start over and boot xp first. But now when i put in the xp cd it is saying i dont have any hard drives. what is the best way i can boot both xp and ubuntu

---

### Post by knuttypk on 2008-06-27
Bump. Can i get any help at all. I am a complete noob so i dont know anything. If yall can even tell me a better way of informing you of what my problem might be that would be awesome. would love to solve this problem

---

### Post by VMC on 2008-06-27
> **knuttypk said:**
> So i installed ubuntu hardy heron and i like it but i want to completely start over and boot xp first. But now when i put in the xp cd it is saying i dont have any hard drives. what is the best way i can boot both xp and ubuntu

What do you mean, you want to start over? Start over installing ubuntu? Or start over installing XP?

Okay, I see you want to delete all partitions and start with a clean slate. Is that correct? The XP won't recognized Linux partitions.

Just put in the ubuntu livecd and run "gparted". Then you can delete all the partitions that you want, using the gui interface. 

Then put the XP disk back in and it should now see unformatted hard drive. But you will have to run the recover cd, and the fixbmr command. To get XP to acknowledge the hard drive.

---

### Post by knuttypk on 2008-06-28
Ok so what is the difference between the live xp cd and the recover cd. i only have a burned iso image from a downloaded xp. and sorry i dont know what the fixbmr is? but thanx ill give it a try and delete everything at the partitioner

---

### Post by AlexBellisBrown on 2008-06-28
Try this and let us know how it goes ;)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by knuttypk on 2008-06-28
Yea this is where if first got the idea to dual boot (thanx stumble upon). But i got stuck when xp didnt recognize the HDD. Im off t work now but will work on it through the weekend. Thanx for the help so far :guitar:

---

### Post by knuttypk on 2008-07-01
So i went in and deleted the hard drive from the partition editor and then popped in the windows cd and still it is not recognizing the hard drives? so now i dont have any OS on the hard drive but it still wontwork wtf.

---

### Post by louieb on 2008-07-01
> **knuttypk said:**
> i only have a burned iso image from a downloaded xp.

Thats your problem - real MS XP isn't available for download.  No telling what you have. Theres some really ugly nasty hacked versions of XP floating around on the net. 

Think I'd just stick with Ubuntu.

---

### Post by VMC on 2008-07-02
Lets start with this. Boot computer from livecd and go to Applications-Accessories-Terminal. Open the Terminal and type this:

```
sudo fdisk -l
```

then come back with the results. It may not be as bad as all that.

---

### Post by knuttypk on 2008-07-02
Yea the version i downloaded is not one of the nasty ones. Ive had and used it for years and had no problems. Ok so i ran the sudo fdisk -l and came up with this 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9728 cylinders
units = cylinders of 16065 * 512 =8225280 bytes
Disk identifier: 0xed1f86f7
Device Boot  Start End  Blocks   Id   System

---

### Post by VMC on 2008-07-02
> **knuttypk said:**
> Yea the version i downloaded is not one of the nasty ones. Ive had and used it for years and had no problems. Ok so i ran the sudo fdisk -l and came up with this 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9728 cylinders
units = cylinders of 16065 * 512 =8225280 bytes
Disk identifier: 0xed1f86f7
Device Boot  Start End  Blocks   Id   System

Somethings wrong. No partitions shown. That output doesn't look right. 

Did you do any disk checking using Windows or Linux on your hard drive?

You see this above : "Device Boot  Start End  Blocks   Id   System"
Disk info should follow. Are you sure you copied the info correctly?

---

### Post by knuttypk on 2008-07-03
That is the only info that popped up on the screen. i coppied it letter for letter. oh and i was also not running any disk checker

---

### Post by wpshooter on 2008-07-03
Are you trying to recover anything that you MIGHT currently have on the drive or do you just want to start all over again with installing both XP and Ubuntu ?

---

### Post by knuttypk on 2008-07-03
I dont care for one single byte on the whole drive it can all be easily replaced

---

### Post by wpshooter on 2008-07-03
> **knuttypk said:**
> I dont care for one single byte on the whole drive it can all be easily replaced

Then get [www.killdisk.com](www.killdisk.com) and WIPE the drive completely clean and the install XP first (make sure you leave enough unpartitioned space for your subsequent installation of Ubuntu) and then come back and install Ubuntu from the ALTERNATE CD version.  Make sure you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

Good luck.

---

### Post by knuttypk on 2008-07-03
Completely cleaned the entire hard drive and still the windows is not recognizing the hard drives. Man this is frustrating

---

### Post by VMC on 2008-07-03
> **knuttypk said:**
> Completely cleaned the entire hard drive and still the windows is not recognizing the hard drives. Man this is frustrating

How did you clean the entire hard drive?

Also, boot up using livecd, then to go gparted and see if it can see your hard drive. If it can make a NTFS partition and select active and then reboot with xp install disk and then see if it now can see hard drive.

---

### Post by knuttypk on 2008-07-03
Well i mean i ran that wipe program.

---

### Post by knuttypk on 2008-07-03
Nope no luck still. I tried the recovery disk and it was working for a minute then said there was an error and shut off before i could right it down

---

### Post by jnw222 on 2008-07-03
what do you see in gparted

---

### Post by knuttypk on 2008-07-07
Ok in gparted all i see is /dev/sda1 ntfs for the entire hard drive.. sorry i was afk for quite a while there was busy

---

### Post by wilbbe01 on 2008-07-07
When you are in gparted can you click on the spot that you say says /dev/sda1 and say delete (delete every partition you see).  After doing that click apply.  Once that says it has finished click on the new button in the top left corner.  Create a new partition in FAT32, you might as well use the whole drive.  See if the windows XP cd sees a drive now.

Also in your defense there are legal versions of XP which are available for download....for students of some universities and I'm sure for others as well.  So why doesn't everyone assume you have one of those legal versions you got from something like msdnaa.

---

### Post by knuttypk on 2008-07-08
Yea so same deal will not recognize the hard drive

---

### Post by simon_wrafter on 2008-07-08
Windows xp does not include drivers for sata hdds, try slipstreaming xp with the appropriate drivers or use a floppydisk. 

Intel based computers need this driver iirc:
[http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/16013/eng/f6flpy32.zip&agr=&ProductID=2101&DwnldId=16013&strOSs=&OSFullName=&lang=eng](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/16013/eng/f6flpy32.zip&agr=&ProductID=2101&DwnldId=16013&strOSs=&OSFullName=&lang=eng)

maybe that will help.

---

### Post by knuttypk on 2008-07-09
slipstreamming?

---

### Post by wilbbe01 on 2008-07-09
You can use nlite to slipstream.  It is a free download, and it can do what you need to with drivers.  The only thing is if the driver previously recommended does not fix your problem then you probably have to search and find a driver that maybe will work.  I suggest just putting the driver the last guy recommended on a floppy disk and pressing F6 when the windows install disk asks about it (it says something on the bottom of the screen about installing 3rd party drivers for your disks or something).  After you press F6 you can follow microsoft's directions and hopefully your drive shows up then.

One other thing, you mentioned a few posts back you have used this installation disk many times.  If you have done it many times and have not changed hardware since the last time you installed windows, this probably is not going to change anything with your problem.  If you got a new hard drive or pci controller card for your hd you will want those drivers and you can try that.  Hope you have luck now!

---

### Post by VMC on 2008-07-09
> **knuttypk said:**
> Ok in gparted all i see is /dev/sda1 ntfs for the entire hard drive.. sorry i was afk for quite a while there was busy
Okay it still sees a NTFS partition.
> **knuttypk said:**
> Yea so same deal will not recognize the hard drive
This conflicts with your above statement.

While using your Livecd and running gparted, click on the lone NTFS partition and then go up and click on delete. Then Apply. You should be faced with an unallocated hard drive.

Finally, how do you want all this to end up. Do you want XP AND ubuntu installed or just ubuntu. If both then, first do the steps above, and then insert your XP install disk and install XP and have it working first. I have a SATA drive and I didn't have to add any drivers for it to work.

---

### Post by knuttypk on 2008-07-09
Ok first i really dislike the idea of downloading  some file i dont know to fix a problem i dont understand. Second my posts do not contradict each other. I deleted the hard drive to ntfs then windows said i could not recognize the hard drive. Third my laptop only has a cd tray no floppy so i cant do the slipstreaming any way

---

### Post by wilbbe01 on 2008-07-09
If you have installed with the same windows cd on the same computer before then you for sure do not have to deal with any of the slipstreaming stuff.  Yes, I agree your posts do make sense, except I am a bit confused on one thing.  Windows says it doesn't recognize the hard drive or windows doesn't show the hard drive when prompted for a place to install windows?  We will figure out what is wrong here.

---

### Post by yipperzz on 2008-07-09
"windows said it could not recognize the hard drive"

When is it saying this?  During the install?  Does it go past the install and then gives you the error when rebooting?  Have you ever installed windows on THIS machine using THIS cd before?  Does the BIOS recognize the hard drive?  

I know that this is frustrating, but your answers are very short.  And if you want help from us, you're going to have to give us some more info on your system and what you're trying to do other than "windows can't find it, i deleted the drive."  Tell us how it couldn't find it.  What the error message is.  How did you delete it?

---

### Post by Ptero-4 on 2008-07-10
Does it say that it cannot find the drive and tell you to press F3 to exit the installer (this happens around the second screen)? or it shows the screen where you would select a partition, but the big selection form is empty?

---

