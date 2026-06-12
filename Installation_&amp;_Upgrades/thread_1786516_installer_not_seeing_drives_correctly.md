---
title: "installer not seeing drives correctly"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by Sanhime on 2011-06-19
I have 2 identical hard drives that was used as a RAID0, the raid array was removed, and confirmed the removal with the raid utlity. Bios settings are not set to raid.  So one hdd has WinXP occupying it, and I want to use the other hdd for ubuntu. For some reason, ubuntu installer still sees it as an array of both hdds. Gpart see them as both array and individual drives.  Does anyone know how to correct this? Maybe I missed something...

---

### Post by YesWeCan on 2011-06-19
What sort of RAID are you talking about? Was the RAID0 originally set up in Windows or in linux?

The HDDs still have "superblocks" on them (sort of array signatures) that the installer is detecting. So you have to delete them.

If this was a Windows RAID you need to run:
[COLOR="Navy"]sudo dmraid -E -r /dev/sdx[/COLOR]
Where x is the letter of the HD.

---

### Post by Sanhime on 2011-06-19
The raid was set up using the built-in raid utility in the motherboard, like after setting raid in bios, the post would ask to hit crtl+I to go into the raid utility to set up a raid stripe.  This was for a Win7 install.  But I have upgraded to SSD (for Win7) so I wanted to make the 2 hdds for WinXP and ubuntu.  I knew I had to remove the raid, so I went into the same raid utility to delete the raid and set them back to nornal non-raid sata hdds.  Both Win7 and Xp sees them as 2 separate drives, but not ubuntu.

I already have XP on one of the drives, if I use "[COLOR=Navy]sudo dmraid -E -r /dev/sdx", will that wipe out XP?

Edit:  I upload a pic

mapper/pdc_....  is the suppose raid
sdb is empty
sdd is XP

b and d were the 2 hdds that used to be raid.  So I'm guessing I should type [/COLOR][COLOR=Navy]"sudo dmraid -E -r /dev/sdb"?[/COLOR]
[COLOR=Navy] 

[/COLOR]

---

### Post by YesWeCan on 2011-06-19
sudo dmraid -E -r /dev/sdb
sudo dmraid -E -r /dev/sdd

Correct. This won't harm XP. You did indeed have what is called a "host RAID" or "fake RAID" system and linux' fake raid driver is called dmraid.

It is a really good idea to install Ubuntu on its own disk. Just be a little careful with the installer - it defaults to installing the Grub to the MBR of sda and this wont be the disk Ubuntu is going on. Make sure Grub is installed to the Ubuntu disk MBR (eg: /dev/sdb). Then you set the bios to boot this disk first to get the Grub menu and a choice of all your OSs.

---

### Post by Sanhime on 2011-06-19
yay, it work!  cheers!  thanks!

---

