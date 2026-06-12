---
title: "How can I add unalocated space to filesystem?"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by boywithsling on 2011-03-12
I am dual booting Ubuntu and Windows 7, I have just shrunk my windows partition and would like to add that extra space to the file system partition. I installed Gparted but it told me I need to unmount the file system partition manually. I would like specific instructions on how to do this, any help would be appreciated. Thanks

p.s. 
Hope this is the right place to start this thread.

---

### Post by kagerato on 2011-03-12
> **boywithsling said:**
> I am dual booting Ubuntu and Windows 7, I have just shrunk my windows partition and would like to add that extra space to the file system partition. I installed Gparted but it told me I need to unmount the file system partition manually.

You have the right idea; you need to repartition the drive to assign the free space to the relevant Ubuntu partition.  However, you can't do this from inside a system already running off that disk.  Instead, you need to boot a Live CD or similar environment from removable media and then start the partitioning program there.  In that case, none of the hard disk partitions will be in use and the modifications should apply fine.

You can use any halfway recent Ubuntu Live CD or DVD images to do this work; I believe they pretty much all have GPartEd or an equivalent program.  Or you could use a specialty boot disk like System Rescue CD.  It doesn't really matter so long as the necessary tools are available.

---

### Post by XsheepX on 2011-03-12
> **boywithsling said:**
> I am dual booting Ubuntu and Windows 7, I have just shrunk my windows partition and would like to add that extra space to the file system partition. I installed Gparted but it told me I need to unmount the file system partition manually. I would like specific instructions on how to do this, any help would be appreciated. Thanks

p.s. 
Hope this is the right place to start this thread.

Your machine is already using that partition, so you need to do it by using a live CD. Either use the Ubuntu CD, or try Puppy Linux, which comes with Gparted.

---

### Post by Hedgehog1 on 2011-03-12
> **boywithsling said:**
> I am dual booting Ubuntu and Windows 7, I have just shrunk my windows partition and would like to add that extra space to the file system partition. I installed Gparted but it told me I need to unmount the file system partition manually. I would like specific instructions on how to do this, any help would be appreciated. Thanks

p.s. 
Hope this is the right place to start this thread.

boywithsling,

You will need to resize/move the extended partition first, and then you can resize/move the Ubuntu partition that lives inside  if it.

[IMG]http://img703.imageshack.us/img703/5948/small48gpartedview.png[/IMG]

If you would like some detailed guidance on the process, please:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by boywithsling on 2011-03-13
You guys are awesome. I'm having problems booting from the cd, I have a netbook and it doesn't like to boot when my external cd drive is plugged in. I've changed the bios settings to boot from external devices first but still have the problem. I may need to use a usb flash drive.

---

### Post by kagerato on 2011-03-13
> **boywithsling said:**
> You guys are awesome. I'm having problems booting from the cd, I have a netbook and it doesn't like to boot when my external cd drive is plugged in. I've changed the bios settings to boot from external devices first but still have the problem. I may need to use a usb flash drive.

The BIOS may not recognize an external CD drive as a boot device (at all).  You'd have to consult the motherboard manufacturer and/or any relevant manuals to determine this.

What many BIOSes mean by an "external" device is usually either an external hard disk or external USB flash.

You may indeed be able to boot a Live CD image off a USB flash drive; that also depends on the BIOS support.  Some BIOSes also have arbitrarily limitations on what kind of USB drives they will boot.  For example, some only boot devices that are unpartitioned (just raw blocks with the filesystem on top), while others only boot certain filesystems (such as FAT32).  It's a case-by-case matter, and it may even differ with BIOS revisions to the same motherboard.

I would recommend using a tool like UNetBootin ( [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) ) to write the ISO image of the Live CD to an unpartitioned, FAT32 USB flash drive and see whether that boots as expected.

---

### Post by boywithsling on 2011-03-13
I've got it booting from a flash drive, but the "unmount" option in gparted is greyed out in the drop down menus for all of the partitions.

---

### Post by kagerato on 2011-03-13
> **boywithsling said:**
> I've got it booting from a flash drive, but the "unmount" option in gparted is greyed out in the drop down menus for all of the partitions.

That's completely fine (and expected).  It's gray because the partition isn't mounted, and you don't want it to be.  Ignore the previous message about needing to unmount it because that's inapplicable now, and continue on with what you were trying to do.

---

### Post by boywithsling on 2011-03-13
Thanks Kagerato, now how do I add the unallocated space to the file system?

---

### Post by Quackers on 2011-03-13
A screenshot of your gparted screen for the drive in question would be good.

---

### Post by kagerato on 2011-03-13
Knowing the exact partition layout would be useful.  The exact changes that need to be made are dependent on that.  (For example, what Hedgehog1 said applies if you are using a scheme with logical partitions.)

If all partitions are primary, though, it may be as simple as shrinking the Windows partition and then expanding the Ubuntu one.

Keep in mind that you can typically experiment a bit with your partition scheme without any data loss.  As long as you don't delete any partitions, resize them smaller than their used space, or overwrite the partition table with something totally nonsensical.

---

### Post by boywithsling on 2011-03-13
I can't connect to my network from the live cd so I can't show the screenshot

---

### Post by Hedgehog1 on 2011-03-13
> **boywithsling said:**
> I can't connect to my network from the live cd so I can't show the screenshot

boywithsling,

If your Ubuntu partition number is sda**5** or sda**6** or sda**7** (anything above sda**4**) it is a logical partition that lives in an extended partition.

So if the number is 5 or greater, you need to extend the sda**2** or sda**3** or sda**4** that is the extended partition first.

***The Hedge***

:KS

---

### Post by boywithsling on 2011-03-13
Right on Hedgehog1, but how do I extend it? when I right click on the extended partition, the only options not greyed out are "manage flags" and "information"

---

### Post by Hedgehog1 on 2011-03-13
Before move/resize:

[IMG]http://img837.imageshack.us/img837/3226/ubuntuonastickgparted.png[/IMG]

After Move/Resize:

[IMG]http://img571.imageshack.us/img571/7305/uoas01.png[/IMG]

In the above picture, I had to move/resize sdd2 **_FIRST_**, and then I could move/resize sdd5 & sdd6..

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-13
> **boywithsling said:**
> Right on Hedgehog1, but how do I extend it? when I right click on the extended partition, the only options not greyed out are "manage flags" and "information"

If these options are grayed out, then the partition is locked.  See the 'keys' on the top picture?  Unmount any partition that has keys.

**_Most likely_**, your swap partition is 'on'.  It does not show a 'key' (sadly).  Instead, right click on the swap partition and choose 'swapoff'.  When you are all done resizing partitions, you can go back to it and do a 'swapon' (it toggles between on/off).

***The Hedge***

:KS

---

### Post by boywithsling on 2011-03-13
okay I got the space moved, but when I save the changes, I get this error: An error occurred while applying the operations *if you want support you need th provide the saved details! see [http://http://gparted.sourceforge.net/larry/tips/save_details.htm](http://http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information* 
what should I do?

---

### Post by Hedgehog1 on 2011-03-13
> **boywithsling said:**
> okay I got the space moved, but when I save the changes, I get this error: An error occurred while applying the operations *if you want support you need th provide the saved details! see [http://http://gparted.sourceforge.net/larry/tips/save_details.htm](http://http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information* 
what should I do?

boywithsling,

I don't suppose you saved the error details?  That kind of data is rather useful...

However, I think I know the error.  If gparted finds any bad sectors on a disk, it 'undoes' the move/resize change.

If you would boot up in Ubuntu, and menu to System >> Administration >> Disk Utility, you can take a look at the status of the disk.

Here is an example of disk in ***REALLY*** bad shape:

[IMG]http://img30.imageshack.us/img30/26/diskfail02.png[/IMG]

[IMG]http://img225.imageshack.us/img225/7057/diskfail03.png[/IMG]

Now, in your case I expect it will just say 'Drive has a few bad sectors'.

_**Please check this and report back.**_

We can still give you more Ubuntu space, but it will take a few extra steps.

Also, if your drive does have a few bad sectors, ***lets talk about that***.

***The Hedge***

:KS

---

### Post by boywithsling on 2011-03-14
yep, says "disk has a few bad sectors", where do I go from here?

---

### Post by Hedgehog1 on 2011-03-14
The good new is you can still use the space. It will just be an additional partition for Ubuntu.
 
Go ahead and move/resize the 'Extended' partition and run the resize in gparted. The extended partition doesn't care about the bad sectors, so that will work.
 
Once that is done, create a new 'ext4' partiton in the empyt space. The will be sda**7** or sda**8 **(Whatever partiton number is next).
 
Once the new partition is built, you can mount is as part of the Linux files system. Depending on the size of the new partition, you could have it become the new '/home' and leave the current Ubuntu partition for root ('/' & SWAP).
 
Here is a link with some pictures that gives you a rouhg idea of how the **fstab** file allows you to make large Linux files systems with many partitions, or even using many disks: [**http://ubuntuforums.org/showthread.php?t=1705788**]("http://ubuntuforums.org/showthread.php?t=1705788")
 
So lets get the new partition made and formatted ext4, and then we can figure the best way to mount it.
 
***The Hedge***
 
:KS
 
p.s. **The bad sector count, once it starts, will grow**. ***You will need to replace your disk drive before too long***. We can walk you though this so you don't have to reinstall anything at all (as long as the new drive is the same size or larger than the old drive).
 
Do your finanaces allow you to replace your hard drive in the next few months? Is it still under warranty? It is not a big rush yet, but it is better to head these things off before it is critical (like the pictures in the previous post!)

---

### Post by boywithsling on 2011-03-15
wow, wouldn't you know my warranty ends today. :( Does anyone else think they put some sort of self destruct timers on computers? I'm a little surprised since It is just one year old. Dell used to make quality PC's.

---

### Post by Hedgehog1 on 2011-03-15
Hard drives are consumables (like ink for the printer and CDs/DVDs for the burner).  I work mine hard; some last a 5-6 years, others 12 months.  Luck of the draw.
 
Keep an eye on the number of bad sectors.  Check once a week.  If the number doesn't grow, you are OK.  If it starts growing, time to do a little hard drive shopping.
 
Is your computer a laptop, or a desktop?  It is a little easier to swap drives in a desktop, but it is doable either way.
 
***The Hedge***
 
:KS

---

### Post by boywithsling on 2011-03-18
It's a netbook (10" laptop), thanks, I'll keep an eye on the bad sector count.

---

### Post by boywithsling on 2011-03-20
I did what you said and created a new partition under "extended" but I got the same error, the error detalis are attached.

---

### Post by Hedgehog1 on 2011-03-20
OK, you did the right thing posting it.

Here is the bad news:```
[B][COLOR="Red"]Bad cluster: 0x1d78748 - 0x1d7874f (8)
ERROR: This software has detected that the disk has at least 85 bad sectors.[/COLOR][/B]
****************************************************************************
* WARNING: The disk has bad sector. This means physical damage on the disk *
* surface caused by deterioration, manufacturing faults or other reason. *
[b][COLOR="DarkBlue"]* The reliability of the disk may stay stable or degrade fast. We suggest *
* making a full backup urgently by running 'ntfsclone --rescue ...' then *
* run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize *
* NTFS safely by additionally using the --bad-sectors option of ntfsresize.*[/COLOR][/b]
****************************************************************************
```

You can try the steps suggested in blue, but my ***Hedgie-Sense*** is telling me you may need a new (and BIGGER) hard drive here real soon.  We can help you copy the data to your new drive when you are ready.

Sorry,

***The Hedge***

---

### Post by boywithsling on 2011-03-21
Looks like I've been pushing it a wee bit too much. Do you think it would help if I just uninstall windows and let it run just Ubuntu? Or should I try to avoid doing to much to the disk?

---

### Post by Hedgehog1 on 2011-03-22
> **boywithsling said:**
> Looks like I've been pushing it a wee bit too much. Do you think it would help if I just uninstall windows and let it run just Ubuntu? Or should I try to avoid doing to much to the disk?

If you don't run Windows any more than you have to, you don't need to uninstall it.  That way it is there to copy onto your next hard drive.


***The Hedge***

---

### Post by boywithsling on 2011-03-22
Ok, than I think I'll just leave it as is until I get a new hard drive. Thanks to all of you for your help.

---

