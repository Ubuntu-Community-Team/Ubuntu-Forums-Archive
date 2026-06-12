---
title: "Wubi Install Error Windows 7 32 bit"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Nicolice on 2010-05-02
Hello...after the new release of 10.04, I decided to give it a try, after using 9.10 on my other computer.

But the installer seems quite different than the previous 9.10, or before, where the option for "Use free space" isn't available anymore when I run the installer via boot from CD.

Afterward, I tried to use the Wubi installer, and everything went fine until there's error about bcdedit.exe, exactly like this person @ this post

[http://ubuntuforums.org/showpost.php?p=9035050&postcount=2](http://ubuntuforums.org/showpost.php?p=9035050&postcount=2)

I've followed all the steps necessary from the other threads, but nothing works...and why there's no more "use free space" option available from the menu like the previous version? I don't want to remove my Windows just to install ubuntu, or this was a bug or intended to? 

Also, when I choose manually configure the drive, I won't able to use the free space, as it mentioned "not usable"..even I've reformatted the drive to FAT32/NTFS or even delete the whole partition volume...

Any helps? Thanks...I guess I'll stick with 9.10 atm until these issues are resolved...

---

### Post by Nicolice on 2010-05-02
Finally found my problem after checking all the partition...all the disk stated as "Dynamic", that's why ubuntu unable to utilizes the free spaces :(

Don't know how the hell my disks were converted to dynamic...now I've to backup all my data and convert it back to basic :( ...

---

### Post by cariboo on 2010-05-03
Closed by request.

---

