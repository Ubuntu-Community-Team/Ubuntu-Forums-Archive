---
title: "GRUB Error 18 ... Grrrr"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by ryharv on 2006-06-08
Hello all,

I've been having problems with GRUB Error 18 after installing Ubuntu 6.06.

I was using 5.10 on an unparitioned 200 GB hard drive on an HP box circa 1997.  Everything worked fine.

Then I upgraded to 6.06 using the live CD, and when I try to boot, GRUB begins to load and then returns Error 18, so I can't proceed.

I tried to reinstall 5.10 and wipe the drive clean, and 5.10 gave me the same GRUB error.  So I reinstalled 6.06 again and still see the error.  So I'm stuck.

Here is the error:
```

Grub Loading stage1.5.

Grub Loading, please wait...
Error 18
```

Browsing around the forums, I've found these ways to fix GRUB Error 18 (none of them have worked for me):

1.  Reinstall Ubuntu and partition the hard drive with a small partition at the beginning of the disk as "/boot"

[INDENT]I repartitioned with /boot as the first 10 GB of a 200 GB drive.  Still getting the error.[/INDENT]

2.  Change BIOS settings so that the hard drive is configured as "Auto" versus "User." 
[INDENT]I flipped the setting to Auto and User, and neither works.[/INDENT]

Other threads on GRUB Error 18 are here:
[http://www.ubuntuforums.org/showthread.php?t=177966&highlight=grub+error+18](http://www.ubuntuforums.org/showthread.php?t=177966&highlight=grub+error+18)
[http://www.ubuntuforums.org/showthread.php?t=167106&highlight=grub+error+18](http://www.ubuntuforums.org/showthread.php?t=167106&highlight=grub+error+18)
(this person had the most similar problems to mine; his were solved by reinstalling 6.06 fresh, but that hasn't worked for me).
[http://www.ubuntuforums.org/showthread.php?t=158632&highlight=grub+error+18](http://www.ubuntuforums.org/showthread.php?t=158632&highlight=grub+error+18)
[http://www.ubuntuforums.org/showthread.php?t=155293&highlight=grub+error+18](http://www.ubuntuforums.org/showthread.php?t=155293&highlight=grub+error+18)

Any and all advice welcomed.  I sincerely appreciate it.  I'm not a total newbie, but I'm also not super fluent.

  Ryan

---

### Post by GameGod on 2006-06-15
I've basically done everything you have and tried the same solutions but am stuck with the same problem too... :(

---

### Post by ryharv on 2006-06-15
I was able to fix the problem by reinstalling Ubuntu 6.10 and you should be able to do the same.  When you get the screen asking you about drive partitions, you have to select the option to manually partition your drive.  Then, on the next screen where you lay out the drive partitions, create a small partition at the front of the drive (I made mine 3GB but I've heard reports that smaller partitions will work).  This has to be the very first partition in the drive.  It also has to be labeled as the "/boot" partition.  As far as I can tell, there is no way to assign a particular partition with the "/boot" label, but rather you must find your existing "/boot" partition, delete all the partitions before it on the drive, and then re-size it so it's small.  

If you end up with your very first partition labeled "/boot" and it's small, it should work.

---

### Post by GameGod on 2006-06-15
Ok, I was thinking about giving this a shot... I'll definitely try it now!
I'll tell you how it goes...
Thanks!

---

### Post by GameGod on 2006-06-15
It worked!!!

Thanks a TON ryharv, you just saved me a lot of time! :) :) :)

So just to recap what I did:
I did an "expert" install (netinstalled, booted off my USB key, lol), which let me do the partitioning by hand. I made a 1 gigabyte /boot partition at the front of the first drive, followed by your usual "/" partition (albeit 390 GB) and a 300MB swap partition.
After the installation, GRUB worked perfectly and Ubuntu booted fine! :)

Thanks again!

---

### Post by ryharv on 2006-06-16
Great!  Glad I could be of help.  This is really awesome, actually.  I have received help from many users of the Ubuntu forums, and this is the first time I've ever helped someone else fix a problem.  Happy to contribute to you, and to the community.

---

### Post by CameronCalver on 2006-06-16
i had a grub error when i used to use breezy i did a reinsall and never saw it again :p

---

### Post by tenoaks on 2006-09-27
hi,

I don't know if you guys come back, but I did as you said, which get rid of Error 18. Thanks a lot.

The thing is when I reboot, Error 2 comes up](*,) 

Any ideas?

---

### Post by cotcot on 2006-09-27
This is a quote from the grub manual to explain the reason of your problem :

> 18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

To be solved with a small boot partition. Small means some 100 MB. Over 1 GB is overkill.

---

