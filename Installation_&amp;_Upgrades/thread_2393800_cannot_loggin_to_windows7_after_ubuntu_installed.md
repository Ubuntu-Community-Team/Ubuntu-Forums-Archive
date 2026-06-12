---
title: "cannot loggin to windows7 after ubuntu installed"
date: 2018-06-08
forum: Installation &amp; Upgrades
---

### Post by ceng.meng on 2018-06-08
HI,

recently i am trying to install Ubuntu to my  HPZ220(Windows 7 installed).  it always fail. after some googling. i got a clue. 

i got 2 disks, one is SSD, which Windows 7 runs on that, one is normal disk.  I freed 100G on SSD(Disk C called in Windows7) and 200G on Disk D. 

firstly i am trying to install ubuntu on those free spaces. but it always failed in grub writing. checked bois, security boot, fast boot were all disabled.   


later, i got an idear, i split the 100G on Disk C to 2 parts, set one part as / during ubuntu installation, and the other small part as  efi. 
finnally ubuntn install is OK, and it can boot up normally.  but Windows 7 is missing.  even i tried boot repair, still not working. 


this is my report. 
[http://paste.ubuntu.com/p/c3ww4PQCBc/](http://paste.ubuntu.com/p/c3ww4PQCBc/)

later i try to add windows 7 in grub.cfg manually. not working because i am sure what need to input there in keyword "Set root=(hd0, MSDOS3)"??

can somebody help me on this,  i would think this is some configuration issue which can be easily fixed. thanks.

---

### Post by yancek on 2018-06-08
Your windows install is Legacy/CSM and you have Ubuntu boot files on an EFI partition.  You need both systems either EFI or Legacy/CSM.  You might try enabling Legacy/CSM in BIOS so you do not boot EFI as that will not boot windows 7.  It will be looking for windows files on the EFI partition and there are none.  You also have Grub in the MBR of the first drive where you apparently have your Ubuntu install so changing to Legacy/CSM in the BIOS and booting Ubuntu and running:  sudo update-grub might work.  Watch the output of the command to see if windows is detected.  The link below explains a lot about UEFI and dual booting and explains the basics of why you are having problems.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-06-08
Windows in BIOS boot mode needs boot flag on the NTFS partition with boot files. That is your sda1.
But UEFI boot requires the ESP - efi system partition to have boot flag for UEFI boot.
You cannot have two boot flags.

I would move boot flag back to sda1 and install a Windows BIOS boot loader into MBR on sda.
That will break the UEFI boot of Ubuntu.

You can add a tiny 1 or 2MB unformatted partition with bios_grub flag on sdb. I would shrink sdb2 by a few MB and put the bios_grub there.
Then with Boot-Repair in advanced mode, install grub2's BIOS boot loader, grub-pc to MBR of sdb.
Set BIOS to default boot sdb first, & sda second. Grub only boots working Windows, or Windows that is not hibernated.

And when (not if) Windows has issues, you may be able to directly boot sda. But still better to have Windows repair flash drive to make fixes.

---

### Post by ceng.meng on 2018-06-08
great thanks for your support, it works.  
thank goodness.

---

### Post by oldfred on 2018-06-08
Glad it worked.
You can change to Solved.

---

