---
title: "Restoring XP MBR from XP gui after Grub pb"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by emeurant on 2009-12-09
I have found a solution for my problem specific :
 
1- the problem
2- the solution
 
 
**1- The problem**
On my acer aspire One , I have XP on the HD and Unbuntu 9.10 on a SSD card. I use the f12 menu to boot from the HD or from the SSD.
 
Since last update, grub has installed itself to the mbr of the HD, replacing the XP mbr. But it seems that the grub files are on the SSD.
 
My problem is that grub gives an error if the SSD is not present. 
 
I have to restore the XP mbr to the HD. This should be ususally done booting a windows XP setup disk and running the recovery console then Fixboot + fixmbr. On the AAO, booting the XP setup disks runs into a blue screen (BSOD).
 
With the SSD inserted, I still can boot Windows XP so a looked for a tool to fix the MBR within XP and found one.
 
**2- The solution:**
on [http://www.sysint.no](http://www.sysint.no) , there is a free tool called mbrfix that do the job.
 
download the zip file and extract to c: (2 exe + one help file html)
 
at the command prompt type (if you have only one disk, else read the manual further, there are lot of samples) :
 
*c:\mbrfix /disk 0 /fixmbr yes*
 
this solved the problem for me.
They seem to be able to handle vista mbr also but I have not used.
 
 
 
Hope this will help those who use ubuntu on a "not always present" external USB or SSD drive.

---

### Post by darkod on 2009-12-09
> **emeurant said:**
> 
Hope this will help those who use ubuntu on a "not always present" external USB or SSD drive.

Further help, when installing ubuntu on multiple drives system ALWAYS CHECK where grub2 will get installed. Even for internal drives you have to do this because you need to know which drive to set as first boot option in BIOS.
If you put grub2 on the SSD problem 1 wouldn't exist. :) Anyway, glad you sorted it out.

---

### Post by emeurant on 2009-12-09
It was working correctly before today upgrade of ubuntu, so I never asked the linux system to put grub on my HDD.
 
When installing ubuntu, it was whithout the HDD connected. So At install time, it was impossible to put anything on it.
 
I 'am afraid grub takes decision whithout asking me. Or maybe I missed something...:rolleyes:

---

### Post by darkod on 2009-12-09
> **emeurant said:**
> It was working correctly before today upgrade of ubuntu, so I never asked the linux system to put grub on my HDD.
 
When installing ubuntu, it was whithout the HDD connected. So At install time, it was impossible to put anything on it.
 
I 'am afraid grub takes decision whithout asking me. Or maybe I missed something...:rolleyes:

Hmmm, in that case very strange. And it's better not to unplug drives when installing ubuntu (if you did that on purpose) because grub needs to know how many drives are there and it creates hd0, hd1, hd2, etc. When you plug in the drive later it confuses the names associated by grub. That might have been part of the problem. But it's very strange, definitely.

---

### Post by emeurant on 2009-12-09
I use this very often. It is like if you install linux on a usb key and take in your pocket and plug in the first available computer.

I never Had any problem doing that and this should not write anything to the local HD.

I'am sure in that case that the auto-update of grub did not asked for the location where the grub files were and what drive to update the mbr on.

---

