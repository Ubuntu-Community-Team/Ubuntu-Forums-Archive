---
title: "Help installing 13.04 alongside Windows 7 - Partitioning issue"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by ronan2 on 2013-09-03
hi all,

I have an old work laptop that I want to install 13.04 on alongside windows. 

The machine has a 320GB disk that is partitioned into the following

/dev
/dev/sda1 356MB (Windows 7(loader or something))
/dev/sda2 316GB (main C: drive)

I tried to install 13.04 using the basic installer where you use the slider to choose the partition. I chose 40GB on the 320GB drive, as I want extra space to insall games. The install failed with the 141 error. 

Do you think it has some issues with the permissions on the drives?

Many thanks,

Ronan

---

### Post by Mark Phelps on 2013-09-03
> I tried to install 13.04 using the basic installer where you use the slider to choose the partition. 

BAD idea -- very BAD idea!  IF you shrink the Win7 OS partition using the installer, you risk corrupting the Windows filesystem and rendering it unbootable.

The safest method for doing this is to open the Disk Management tool in Win7 and shrink the OS partition in there.

---

### Post by ronan2 on 2013-09-03
Why on earth would the developers include such a tool in the installer then?

There is an option to "install along side windows 7"

I can't run the Disk Management tool as I'm not an admin

---

### Post by oldfred on 2013-09-03
Many have used gparted to resize Windows, but Windows immediately needs to run chkdsk. You may need to be the Admin to run all the Windows repairs on resize.
Or if you do not have permission to install Ubuntu you should not.

If you have access to choose to boot USB, you can put a full install on a larger flash drive. But again you need to get into BIOS to change boot order.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by Mark Phelps on 2013-09-04
> I can't run the Disk Management tool as I'm not an admin 

Then basically, you should leave it alone.  Not having Admin rights will seriously affect your ability to make any repairs, should something go wrong.  And then, you'd be left with a nonworking PC.

---

