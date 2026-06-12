---
title: "error on wubi during uninstall to reinstall again"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by lorue on 2010-09-30
Hi Ubuntu friends!
As I was haveing some problems with my wubi installation, I decided to uninstall it and again reinstall. 
But when I was uninstalling the proccess show the next msg
Error:
Invalid argument removing c:/ubuntu/disks/home.disk
there is no log.
Then I try to delete the file manually, but I can not because the file has an error
Error 0x80070570 the file is damage.
What do I have to do to delete it??
could someone help me??
thank you & regards
Lorue

---

### Post by keljaden on 2010-09-30
Sounds to me like Windows corrupted your wubi install.  I highly recommend you dual boot instead.

Right click on my computer, go to manage> manage disks, shrink the partition so you will have 20 gigs of free space on the end.  Right click on the free space and delete it so it's registered as unallocated.  Pop the ubuntu disk in, boot into it, and install.  During install process select "use largest continuous free space" and it will partition everything for you.

It's a simple way to make a nice dual boot for starting Linux users.  Keep on using Linux.  It took me almost a year to get into it.  I finally made the full switch and I love it.

---

### Post by bcbc on 2010-09-30
Run chkdsk on your drive (or My Computer, right click on 'drive', Properties, tools, Check for errors, automatically fix).

Then you will probably have to reboot to get it to check, and you might have to retrieve any corrupted files from the folder FOUND.000 - these are hidden folders.

You might be able to loop mount and copy data from home.disk if it manages to fix it - just in case you need to.

---

### Post by lorue on 2010-09-30
Hi [keljaden]("http://ubuntuforums.org/member.php?u=664868"), thank you for your comment.
surprise!,:lolflag: windows has 4 primary partitions on the disk!!:confused: in this laptop, why??, only the MIBs know...., then unfortunately I could not install a dual boot:guitar:... only wubi.

Hi bcbc, thank you for your comment
I will start to work!!):P
Thank you and regards
Lorue

---

