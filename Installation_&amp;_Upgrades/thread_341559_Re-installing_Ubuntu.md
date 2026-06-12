---
title: "Re-installing Ubuntu"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by lettherainbeyourapplause on 2007-01-18
I am trying to re-install Ubuntu 6.10. 
I am running Ubuntu now but when I put in the CD Ubuntu won't read the .exe file. I also have Windows installed on a separate partition. I know there is probably an easy solution. 

I am very new to Linux. Can someone help me out?

---

### Post by wpshooter on 2007-01-18
Are you running Ubuntu under/as a function of M/S windows or do you have it installed as a separate O/S on it's own partition ?  If it is the latter, you just need to have the Ubuntu in the CD-rom drive when you boot your computer and if you have your CD-Rom as the first boot device in BIOS, your computer will boot to the Ubuntu CD, the CD is a bootable device.

Let me know if I am not correctly understanding your problem.

---

### Post by lettherainbeyourapplause on 2007-01-18
It is installed on a separate partition. It is not running under Windows.

So if i boot with the CD in I can trash the current copy and install a new one?

---

### Post by lettherainbeyourapplause on 2007-01-18
Thanks for the help.

---

### Post by meng on 2007-01-18
Yes you can overwrite the old Ubuntu partition/installation. You will lose any settings or data on that partition.

---

### Post by Sef on 2007-01-18
> I am trying to re-install Ubuntu 6.10.
I am running Ubuntu now but when I put in the CD Ubuntu won't read the .exe file. I also have Windows installed on a separate partition. I know there is probably an easy solution.

1) Do you have your files on a home partition?  If so, then you won't lose any information when you reinstall, but **back up** your files.   There are no 100% guarantees.

2) If it is the same disk that you used for the install, then the disk may be bad now.   

3) If the computer doesn't pick up the disk upon boot, then check the BIOS and make sure the CD-ROM/RW is set to boot first.  

4) The only partitions that need to be reformatted are root and swap.

---

