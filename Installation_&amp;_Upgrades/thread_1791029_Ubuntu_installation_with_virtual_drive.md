---
title: "Ubuntu installation with virtual drive"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by ktp.kti on 2011-06-26
I had to recently reinstall my Ubuntu due to some wireless connectivity issues. I ran into a problem while doing so.

I had downloaded a 32bit version of Ubuntu. Initially i had burnt a CD with the .iso file and installed Ubuntu with it inside windows 7. It was just a cakewalk. I was taken through multiple windows during the installation like installation size, keyboard setting, time zone, user name, password, etc.

Now, during the reinstallation i did not have the CD with me. So i tried multiple other methods, but none yielded results as good as the CD. I am listing the methods i tried below:
1) I just opened the .iso file using winrar and double clicked on the wubi.exe file. The installation started but midway during the installation it started downloading the entire .iso file again.
2) I created a bootable USB flash drive using the universal USB installer as advised by the Ubuntu website. Then i opened the USB using windows and clicked the wubi.exe file. Again i faced the same problem as above.
3) This time I booted from the flash drive. But the process shut down midway citing some error.
4) I created a virtual drive using slysoft virtual clone drive and mounted the .iso file in the drive. It installed smoothly this time, but i ran into some new problems. 
- The installed ubuntu has copied my username and password from windows. I was never asked to create a new user name and password. (It seems that ubuntu had copied my documents and settings from windows)
 - during installation it did not give the option for automatic upgrade (It did last time). This cretated problem with some of my drivers.
- There were new partitions in the file system. (I originally have a 250GB hard disk. 50GB for C drive and 200GB for D drive for other storage. During my initial installation with CD, this was maintained and ubuntu was installed within the C drive. This time although i had clicked 'c-drive' during installation, it seems that a new partition has been created within the C drive so that now i have 3 file systems in ubuntu 150, 50, 50. (I had used a ubuntu installation size of 15 GB)
- During ubuntu boot up i used to have 3 options, 'generic', generic recovery mode and one windows 7. (Sorry if i am wrong! I am not a computer wizard and am not remembering them well) Now i have 2 options in addition to the above, both had 'dev' in it. When i clicked on them, ubuntu did not boot up. I had to force shut down and restart again. 

Why is this happening. Am i doing something wrong!

What i finally want is to have my ubuntu sit within my c drive alongside windows (without creating new partitions), to have it ask me for username and password during installation. How can i do it?

---

### Post by jerrrys on 2011-06-26
maybe this will help

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

as for name and password during install, just hit 'enter'.   that usually works

---

### Post by varunendra on 2011-06-26
For running wubi installation normally as before, this is the method you've to use (copied from above link by jerrrys, but also personally tested by myself a few months ago):
> If you do not have a CD, try to find a computer with  Internet access, and download both Wubi.exe and the required Desktop ISO  from the same location (the release has to match)....
....

Copy both files into the same folder on the machine with no Internet access and run the Wubi executable.

So just extract the wubi.exe file as you did with winrar, and place it and the iso in the same folder (preferably place the folder in the root of some drive like D: or E:,.. - to avoid pathname issues), then run it. Installation should go just like it did from the CD.

And yes, don't forget to completely remove (uninstall) the previous installation before proceeding with a new one. Make sure the currently installed files/folder have been removed.

---

### Post by ktp.kti on 2011-06-28
> **varunendra said:**
> 
So just extract the wubi.exe file as you did with winrar, and place it and the iso in the same folder (preferably place the folder in the root of some drive like D: or E:,.. - to avoid pathname issues), then run it. Installation should go just like it did from the CD.

And yes, don't forget to completely remove (uninstall) the previous installation before proceeding with a new one. Make sure the currently installed files/folder have been removed.

Solved! Thank you varunendra!:D

---

### Post by varunendra on 2011-06-28
You're welcome!

---

