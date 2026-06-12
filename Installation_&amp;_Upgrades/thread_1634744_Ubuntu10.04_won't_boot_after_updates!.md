---
title: "Ubuntu10.04 won't boot after updates!"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by tlehmann on 2010-11-30
I've been using ubuntu 10.04 dual booted with Vista 64 bit for about a month now with no issues until tonight.  I downloaded the most recent uprates in the update manager by going to "update-manager -d"  in terminal.  When it told me to restart, I did.  Now when i try to boot by selecting ubuntu as the os, it says no wubildr found:1 no wubildr found:2 wubildr: (or something like that) then goes back to the os select screen.  It has always done that with no issues, but now I can't even reach the GRUB menu!  It also stopped vista from loading until I ran a diagnostics check and fixed some issues.  Any ideas?

---

### Post by wmb on 2010-12-01
I have the same problem.  I want to make sure everyone knows as much as possible, can you confirm yours went the same way?

The original install was started on Windows 7(64-bit), so I have a folder in "C:\" called "ubuntu".
When I boot, I have 2 choices Windows 7 (automatically selected if I don't press any key for 9 seconds), and Ubuntu.
When I select Ubuntu, there is a message that pops up..
Try(hd0, 0): NTSF5 : no wubildr
Try(hd0, 1): NTSF5 : 

After that displays, my computer reboots and eventually has the 2 choices again...


This is everything in my C:\ubuntu folder


C:\ubuntu folder:
disks (folder)
install (folder)
winboot(folder)
Ubuntu (icon)
uninstall-wubi (application)

C:\ubuntu\disks folder:
boot (folder) which holds boot (folder) which holds grub (folder) which is empty
root.disk (disk file)
swap.disk (disk file)

C:\ubuntu\install folder:
.fuse_hidden0000000400000001

C:\ubuntu\winboot folder:
wubildr (file)
wubildr.cfg (cfg file)
wubildr.mbr (mbr file)



I'm not trying to jack your post, I figured this might help find the problem...can you confirm yours holds the same?

---

### Post by Rubi1200 on 2010-12-01
Hi and welcome to the forums tlehmann and wmb :)

There are issues at the moment with GRUB updates and Wubi installs.

If you are able to boot Windows normally and the only problem is Ubuntu, see here for more information and fixes:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

The first post explains how to get Wubi/Ubuntu up and running again and the second how to avoid the problem for the future (as much as possible at least).

Good luck!

---

### Post by wmb on 2010-12-01
> **Rubi1200 said:**
> Hi and welcome to the forums tlehmann and wmb :)

There are issues at the moment with GRUB updates and Wubi installs.

If you are able to boot Windows normally and the only problem is Ubuntu, see here for more information and fixes:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

The first post explains how to get Wubi/Ubuntu up and running again and the second how to avoid the problem for the future (as much as possible at least).

Good luck!


Wow, I have been searching, for a few days, to find someone that had a similar problem.  I finally found a post that matched my problem and all I had to do was go to the sub-forum..lol.  This is a great site, with lots of valuable info, and very friendly people.  It will definitely be bookmarked for future problems.  I wish I had known to come straight here and search, who knows how much of my life I would have back if I had done that in the first place...:D

Thanks for the links.  I tried the copy/paste and that didn't work, so I guess I'm off to try the other steps... See you around.

---

### Post by hotsync on 2010-12-01
> **Rubi1200 said:**
> Hi and welcome to the forums tlehmann and wmb :)

There are issues at the moment with GRUB updates and Wubi installs.

If you are able to boot Windows normally and the only problem is Ubuntu, see here for more information and fixes:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

The first post explains how to get Wubi/Ubuntu up and running again and the second how to avoid the problem for the future (as much as possible at least).

Good luck!

Thanks.. this solved my problem too.

---

### Post by Rubi1200 on 2010-12-01
> **hotsync said:**
> Thanks.. this solved my problem too.
You are more than welcome :)

---

### Post by tlehmann on 2010-12-01
> **wmb said:**
> 
The original install was started on Windows 7(64-bit), so I have a folder in "C:\" called "ubuntu".
When I boot, I have 2 choices Windows 7 (automatically selected if I don't press any key for 9 seconds), and Ubuntu.
When I select Ubuntu, there is a message that pops up..
Try(hd0, 0): NTSF5 : no wubildr
Try(hd0, 1): NTSF5 : 

After that displays, my computer reboots and eventually has the 2 choices again...


This is everything in my C:\ubuntu folder


C:\ubuntu folder:
disks (folder)
install (folder)
winboot(folder)
Ubuntu (icon)
uninstall-wubi (application)

C:\ubuntu\disks folder:
boot (folder) which holds boot (folder) which holds grub (folder) which is empty
root.disk (disk file)
swap.disk (disk file)

C:\ubuntu\install folder:
.fuse_hidden0000000400000001

C:\ubuntu\winboot folder:
wubildr (file)
wubildr.cfg (cfg file)
wubildr.mbr (mbr file)


I have all those exact same files and the exact same message at the boot screen, except mine says no wubildr twice.  I assume that's because it is searching my D drive as well as C.  Also, about the links.  I don't have a "Live CD".  Can I create one using a 2GB flash drive, or do I need to order it?  I installed via Wubi, so I never had a cd to begin with.

---

### Post by tlehmann on 2010-12-01
Bumpity Wumpity...

---

### Post by wilee-nilee on 2010-12-01
> **tlehmann said:**
> Bumpity Wumpity...

In answer to the thumb drive yes download the equal distro installed and load it to the thumb with this.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

A standard Ubuntu ISO fits on a 700MiB cd so 2 gigs is more then enough it would fit on a 1 gig thumb.

If your still using Lucid here is a link.
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by tlehmann on 2010-12-02
And I just put that ISO in the software, right?

---

### Post by wilee-nilee on 2010-12-02
> **tlehmann said:**
> And I just put that ISO in the software, right?

Unetbootin is what you would use it is fairly straight forward, but may be the first time confusing. You just want to have unetbootin listing the ISO,There is a ISO button I believe and in the bottom pointed at the correct usb thumb. I generally go to computer and do a quick fat32 repartition of the thumb by right clicking. I believe Unetbootin will partition as well, but I have never used it.

Make sure you have it pointed at the actual partition so **if** the thumb is sdb chances are the partition is sdb1 that's where you would install.

---

### Post by tlehmann on 2010-12-02
So after I've pressed OK in the software and it's installed the bootloader, what's next?  I read that I should choose USB from the F12 menu at boot, but will this overwrite Windows and will I need the USB in every time I boot? Will all of my Ubuntu data from before be there?

---

### Post by tlehmann on 2010-12-03
I now have 10.04 up and running, and I think It is a true dual boot now since I didn't use Wubi.  However, when I boot now it takes me right to the GRUB screen without asking me which OS to boot to.  My C: drive still has all of it's content on it, but I'm not sure if Vista is still installed.

---

