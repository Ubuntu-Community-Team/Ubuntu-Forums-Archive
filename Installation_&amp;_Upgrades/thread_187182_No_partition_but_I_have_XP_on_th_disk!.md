---
title: "No partition but I have XP on th disk!?"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by menola on 2006-06-02
I have 3 partitions for XP on my 60Gb disk in Toshiba Laptop Satellite A50-432 with Intel 855 chip, Pentium Mobile. I have also formated existing ext3 and swap on my harddrive. 

If I use desktop disk(live cd) or alternative disk 6.06(no RC) to install 6.06, I can only see an emtpy disk when I´m trying to install Ubuntu 6.06. What´s wrong! 

What shall I do to install 6.06?

menola

---

### Post by johnc4510 on 2006-06-02
Google this:gparted live cd
Download it and burn it to cd
Boot your computer from the cd and you should be able to see your partions and make new ones for Ubuntu to be installed on.

---

### Post by menola on 2006-06-02
But I can´t install ubuntu 6.06 with desktop cd or alternetive cd. I these cd defekt or is the ISO on the ubuntu site damage? 
The only thing i can see is emtpy harddrive but I have 3 partitions with NTFS for XP and I have swap and etx3 formatet with this cd, strange!?

What shall I do to install 6.06????

menola

---

### Post by aysiu on 2006-06-02
When you're using the desktop CD, the session is running off of your computer's RAM where a fake "installation" of Ubuntu is running. None of your hard disk partitions are mounted. If you click the installation button, you'll be walked through where you want to install Ubuntu and where to mount your partitions.

Read this for more details:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by mterlouw on 2006-06-02
I have the same problem. It seems like parted is choking and doesn't detect the partitions that are on the disk. fdisk -l shows that the partitions are there and detectable under linux, and trying to fix partition order in fdisk does nothing (partition order already correct). Tried with both the live CD and the alternative text mode installer CD, but still can't install Dapper.

---

### Post by G Kaya on 2006-06-03
I have a Windows partition and three ext3 partitions and none of them are showing...the entire hard drive is "unallocated space." Please help.


...Oops! Just needed to click forward one more time to get to the mount and format partitions screen. I guess I'm too used to other installers where that info pops up right away.

---

