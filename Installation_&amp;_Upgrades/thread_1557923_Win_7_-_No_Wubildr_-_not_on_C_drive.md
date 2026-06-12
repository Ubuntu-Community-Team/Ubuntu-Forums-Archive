---
title: "Win 7 - No Wubildr - not on C drive"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by AlanCFA on 2010-08-21
I recently installed Windows 7 on my "C" drive and decided to install Ubuntu.  I used the Windows Installation version, rather than burning it to a cd.

When I installed, I chose to install Ubuntu on a separate physical drive.  It is now on my "J" drive.

When I boot and choose Ubuntu, I get the following:
Try hd(0,0): NTFS5: No wubildr
Try hd(0,1): 

The second line is as shown - nothing appears after the colon.  The keyboard does not work, I cannot hit the tab key to get additional partition info or even use ctrl+alt+del to reboot; I need to hit the reboot key on the computer to do that.

wubildr and wubldr.mbr are installed on my C drive.  Also, on my J drive, under this folder
 J:\ubuntu\winboot
is wubildr, wubldr.mbr, and wubldr.cfg

Is the resolution simply to copy those wubldr files to the root of the J drive?
Is the fix more complicated?
Or does Ubuntu need to be run on the same drive as Windows? (i.e. uninstall/reinstall)

System info:  Intel CPU E6700 2.67mhx, 4 GB RAM, 4 internal and 1 external drive.
The drive to which I am installing Ubuntu was empty with a 320gb capacity.  The C drive where Windows 7 resides is 500gb with about 150gb used.  Both Win 7 and Ubuntu are 64-bit 


Please advise.
Thanks,
Alan

---

### Post by dino99 on 2010-08-21
if you want to really try ubuntu, better to make a real install, follow this little help:

prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

note: wubi is not designed to work with anyway

---

