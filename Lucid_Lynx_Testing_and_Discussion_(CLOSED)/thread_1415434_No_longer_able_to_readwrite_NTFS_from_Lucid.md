---
title: "No longer able to read/write NTFS from Lucid"
date: 2010-02-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robertjm on 2010-02-24
I'm having problems which have only crept up since doing some updates yesterday. I have a HDD with three partitions.

Partition A is NTFS w/W7
Partition B is NTFS data partition
Partition C is ext3 w/Lucid.

Up until yesterday,I was able to read and write just fine to the NTFS data partition from either operating system. However, something that was updated yesterday has changed the partitions somehow so I have no write permissions anymore from Lucid. I can read, write and manipulate files just fine on that partition from W7.

As of right now I'm hampered in accessing the web from the Karmic install since my data files for Firefox and Filezilla are located on the NTFS data partition, and cannot be opened due to whatever chaged.

Anyone else experiencing this problem? 

Robert

---

### Post by Ibidem on 2010-02-24
Haven't updated in weeks (besides having XP instead of Windows 7), so I have no idea.
What does mounting manually in the terminal output? (ie, if you mount on /windows, run 
sudo mount /windows
and note the errors)
That can happen if someone hibernates Windows.

If you post the output from attempting to mount manually with only the mount point specified, it clarifies what went wrong.

---

### Post by libihero on 2010-02-24
i've actually just developed this problem in karmic.... did the upgrade that just happened mess it up? usbs wont even be read either....

---

### Post by garvinrick4 on 2010-02-24
Lucid triple boot and windows 7 and karmic not under Places just Computer and cdrom0.
Cannot mount flash drives at all GUI or command line.

 Under karmic install can mount all and under Places all OS's and USB devices.

In Lucid Flash drive will be recognized in gparted under devices. 

Live CD is as expected all recognized.

---

### Post by Robertjm on 2010-02-24
Hi all,

Little update. I logged into the Karmic O.S. and then the fstab.

When I originally partitioned I didn't create a mount point myself for the NTFS, instead relying on Lucid to do it for me. As a result, it gave me some gobbledegook name (example: e3dd99222). Now when I check things out, that's the name of the mount point PLUS there is a _ added to the end of that  (example: e3dd99222_)

When I edit my fstab to get rid of the _ and then restart Lucid, I am able to launch Filezilla and Firefox just fine.

So basically, it looks like something changed what was perceived as the mount point somewhere along the way. I'm back over in W7 now, and will try Lucid again to see if it kept the "fix" or not.

Something odd did happen though. When I was opening my browser in the W7 partition I actually got a Blue Screen of Death!! I haven't seen of them since God knows when.

---

### Post by ranch hand on 2010-02-24
There is an easy fix for the BSOD and the ntfs problem.  I used it and no longer have any of those problems.

Delete all ntfs partitions and all MS products.  Problem solved.

---

### Post by libihero on 2010-02-25
what about if it wont detect usbs either :P

---

### Post by garvinrick4 on 2010-02-25
My lucid cannot mount flash drives or partitions anymore. Any idea's.

---

### Post by cariboo on 2010-02-25
What does dmesg say after you have plugged your usb devices in? Is the drive detected but but it isn't automagically mounted?

---

### Post by phillw on 2010-02-25
> **ranch hand said:**
> There is an easy fix for the BSOD and the ntfs problem.  I used it and no longer have any of those problems.

Delete all ntfs partitions and all MS products.  Problem solved.

One day, I'll get around to that - either that or try to rescue my very unhappy win partition (It wasn't cleanly un-mounted during one of the very few 'lock-ups' I've had with 10.04 -- 10.04 can see it fine, but, alas ... Poor Windows OS ;))

Phill.

---

### Post by libihero on 2010-02-26
on my karmic its not even shown
for example, when you open nautilus it should have generic multicard and the cd/dvd drive, even when they are vacant.  those just disappeared for me :S

---

### Post by linusr on 2010-04-11
> **cariboo907 said:**
> What does dmesg say after you have plugged your usb devices in? Is the drive detected but but it isn't automagically mounted?

In disk utility, drive is detected as 'unknown' drive

Will check dmesg log and update

---

