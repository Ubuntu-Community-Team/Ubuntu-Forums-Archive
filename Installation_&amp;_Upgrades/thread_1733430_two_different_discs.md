---
title: "two different discs"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by ozonora on 2011-04-19
Hi, I've got a question.

I've installed Ubuntu several times on my Desktop computer which has a single 500 GB hard disk. I have always had problems, because I use the computer a lot for several purposes, including research, so I have many partitions. I have several Windows intallations.

The problem is that I also format the Windows partitions from time to time. The thing is that Ubuntu installs the GROOB loader, but when I reinstall Windows on another partition GROOB gets lost.

Summing it up, as I format Ubuntu and/or Windows usually, I have always had problems.

My question is this: If I use two independent hard disks, and I use the BIOS to choose from which of them start, and I use one disk for Windows partitions and the other for Ubuntu partitions, would each disk have its own loader (the first, the Windows loader, and the second, GROOB), so that I would stop having my problems?

Thank you guys.

---

### Post by Quackers on 2011-04-19
Yes that can work well.
Be sure to install grub to /dev/sdb (or whatever designation your Linux drive uses during the installation. Otherwise the installer will put grub on /dev/sda.

---

### Post by ozonora on 2011-04-19
> **Quackers said:**
> Yes that can work well.
Be sure to install grub to /dev/sdb (or whatever designation your Linux drive uses during the installation. Otherwise the installer will put grub on /dev/sda.
What are /dev/sdb and /dev/sda? The two different physical disks?

---

### Post by Quackers on 2011-04-19
Those are the designations that Linux will give your two drives (if they are the only two in use).

---

### Post by ozonora on 2011-04-19
Thank you very much.

---

### Post by Quackers on 2011-04-19
You're welcome.  Good luck  :-)

---

### Post by oldfred on 2011-04-19
Herman has lots of detail on installing to a second drive. Not as complex as it may look since he is explaining so much.

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

