---
title: "ALERT! /dev/disk/by-uuid/xxxx does not exist. Dropping to a shell!"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by jsirotto on 2009-11-22
Problem:  

Gave up waiting for root device. Common Problems: 3860b6c7e1a
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did system wait long enough?)
  - Check root= (did the system wait for the right device)
- Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/0caf0984-6932-46ab-8d54-d3860b6c7e1a does not exist. Dropping to a shell!




Hi, Im sorry if some of my questions sound stupid as Im new to ubuntu.  Ive had 9.04 running since June 09, I upgraded to 9.10 about a week after it came out.  Up until this morning, I havent had any problems.  I was using ubuntu last night no problem, I shut it down, woke up, and now it doesn't seem to boot up. (I didnt use the update manager or anything).

Im dual booting with Windows Xp (and that still seems to work no problems)
Ive tried Recovery Mode at the startup selection, same problem.
Ive tried running the older kernal from the startup selection screen, same problem.
I downloaded the 9.10 Installation CD and am currently running from the cd.

Ive also seen a lot of threads on here with similar or the same problem, but there seems to be so many different solutions, and I dont want to mess anything up even more.

I ran "sudo fdisk -l" in the Terminal and this is what I got:



Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xccb4ccb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8601faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60427   485379846   83  Linux
/dev/sdb2           60428       60801     3004155    5  Extended
/dev/sdb5           60428       60801     3004123+  82  Linux swap / Solaris




I was thinking of reinstalling, but I read that it will overwrite my existing ubuntu OS and I will lose all of my settings, firefox bookmarks, files, ect, so Im leaning away from that solution.

Any help would be appreciated.
Thanks

---

### Post by macu on 2009-11-23
I have the same problem since this morning. I tried edit linux boot options in grub by presing "E", then I have deleted UUID and wrote the way to my partition... for example for you

... /dev/sdb1 ro quite splash
then I presed Ctrl+x to boot this kernel and it was good...

but this is the temporary solution, because you must edit it everytime you are booting kernel

---

### Post by jsirotto on 2009-11-23
I didnt mention before, the 82GB HD contains Windows XP and the 500GB HD has Ubuntu (9.04 Upgraded to 9.10)

Ok I think Ive narrowed my problem down to either Ubuntu 9.10, or my 500GB HD. I ran the LiveCD for Ubuntu 9.10, and could not find a way to mount my 500GB HD.  I tried in the terminal, and with Ubuntu's system admin tools, neither were letting me mount it.  When I tried running the LiveCD for Ubuntu 9.04, it automatically detected it and had it available from the Places tab on the desktop menu.

Not really sure what to do from here

---

### Post by jsirotto on 2009-11-23
Ok, so Ive booted up the LiveCD (9.04) so I can access my 500GB HD. But its not letting me delete files from there (I need to clean it up a bit so it fits on my external HD), It keeps telling me permission denied.  Could this be the entire problem is that my harddrive is somehow locked or something?

---

### Post by phillw on 2009-11-23
firstly, what version of grub are you using ?

recovering grub legacy (pre 9.04) is different to 9.10 with grub2

Phill.

---

### Post by phillw on 2009-11-23
For those with dual boot systems -- the how-to is over here -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You will need to know which Grub you're on. Basically, if you're on 9.04 and below, you're on grub legacy (v1), if you have upgraded 9.04 --> 9.10 and HAVE NOT updated grub, then you're still on grub legacy.

If you are running a fresh install of 9.10, then you're on Grub2

To recover Grub under Grub2 then you will need step 12 of [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Step 12 also links to a more in depth one, covering UID's etc for recovery that way.

As always, post back if you are still having problems.

Regards,

Phill.

---

