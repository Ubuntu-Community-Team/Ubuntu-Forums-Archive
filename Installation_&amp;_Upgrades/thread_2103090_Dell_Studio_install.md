---
title: "Dell Studio install"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by sandeep108 on 2013-01-09
I intend to install 12.10 using USB stick on my Dell Studio 15" with ATI graphics. At present the entire HDD is unpartitioned and used by Windows 7. As my memory goes, it is better for Ubuntu to have 3 partitions - Ubuntu, swap and /home. So how do I go about installing 12.10 on this laptop? There is not much data on Windows 7 anyway but I may need it occasionally.

a. Do I use Windows 7 to 'shrink' the existing partition first?

b. Do I use advanced options during the Ubuntu install?

Planning to use about 100 GB for Ununtu - 25-30 GB Ubuntu, 2GB swap and the rest for /home. Since Ubuntu can read the Windows 7 partition, I can always store some files there.

I know I need to do a chkdsk and defrag first.

Also when trying out Ubuntu, I found that the fan was always running on high. Do I need to worry about this or when it is finally installed, it will sort itself out.

TIA

---

### Post by d.atanasov on 2013-01-09
> **sandeep108 said:**
> I intend to install 12.10 using USB stick on my Dell Studio 15" with ATI graphics. At present the entire HDD is unpartitioned and used by Windows 7. As my memory goes, it is better for Ubuntu to have 3 partitions - Ubuntu, swap and /home. So how do I go about installing 12.10 on this laptop? There is not much data on Windows 7 anyway but I may need it occasionally.

a. Do I use Windows 7 to 'shrink' the existing partition first?

b. Do I use advanced options during the Ubuntu install?

Planning to use about 100 GB for Ununtu - 25-30 GB Ubuntu, 2GB swap and the rest for /home. Since Ubuntu can read the Windows 7 partition, I can always store some files there.

I know I need to do a chkdsk and defrag first.

Also when trying out Ubuntu, I found that the fan was always running on high. Do I need to worry about this or when it is finally installed, it will sort itself out.

TIA
Hi I also had Studio - 1537 The quites laptop I had ever seen. But I did not had the video card you have. 
I will recommend first to try to shrink the windows 7 (most of the cases I had were wiping out the windows :P). During installation of Ubuntu there is advanced option as you saw, where you can make new partition table for your harddrive.  (I assume you know what you are doing ;) and be careful ) The reading of the files from ntfs partition will be easy but in some cases you may need additional ntfs drivers. You can find them at the package manager of software sources (if not installed). The high speed of the fan: You will need to install additional drivers for your Video Card. Look for appropriate drivers on google.  
Good Luck..

---

### Post by sandeep108 on 2013-01-13
Well, after using a usb stick created by UUI and trying 12.10 out, I tried to install it. But subsequently now, it refuses to go past the Ubuntu 5 dots screen and shortly gets stuck. I used another USB stick and also a DVD-R to create a live disk. But they just simply get stuck on the 5 dots and refuse to go any further. I have checked the MD5sum on the iso used for the DVD and UUI and it is fine.

The DVD was verified by Windows 7 after burning and it reported successful. But neither the DVD or USB sticks work on any other computer as well. 

I then used another PC to create a fresh UUI stick, but that does not work either.

I am now quite stumped. Any ideas / suggestions will be welcome.

---

### Post by sandeep108 on 2013-01-13
I just tried the pendrive on my 3rd PC - it worked fine. So are there some issues on my Dell Studio or my older desktop PC? I also ran memtest on the Studio for several minutes and there were no errors. 

What could be the problem, especially since earlier the Studio ran quite fine from the USB pendrive.

---

