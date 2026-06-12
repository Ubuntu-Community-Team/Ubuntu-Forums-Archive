---
title: "Install on Windows system"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by himanshusanehi on 2011-03-06
Hello,
         I am using Windows 7 OS. I have 3 HDD partitions on my Compaq laptop.
C: 50GB (For Win OS)
D: 217GB (For storing everything)
E: 30GB (To install Ubuntu 10 as separate OS)

There's one more partition of 100MB which Win created.

I tried installing Ubuntu 10 using pendrive but got stuck at manual partition. I have 30GB partition formatted as NTFS on which I want to install Ubuntu as separate OS. I am not familiar with Ubuntu disk partition method. Can you please help me. I want Win 7 to remain unaffected.

Kindly help!

---

### Post by madeinwales on 2011-03-06
hi
i am fairly new to this, and do not know about install from flash drives but i do know the following from experience...
download the 'disc' from here...
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
turn off pc and reboot with disc in the drive, you will then be given options and instructions to create partitions etc WITHOUT affecting your windows installation.
then just choose on boot which OS to use.

hope thats of some help.
nev

---

### Post by Mark Phelps on 2011-03-07
You can't install Ubuntu natively to an NTFS partition.  Ubuntu needs Linux filesystem to work.

You can install to E: using Wubi, but you would be installing from inside Windows -- and personally do not recommend Wubi installations.

So, if you want to install Ubuntu to the 30GB space, you need to remove the NTFS partition and let the Ubuntu installer partition that space for you.

---

### Post by FoxEWolf on 2011-03-07
I would recommend that you use Wubi to install ubuntu. You seem to be needing to use Windows for your primary so use Wubi to install.

---

### Post by himanshusanehi on 2011-03-07
When I was at partitioning step, I deleted the 30GB NTFS formatted drive and formatted it as ext4 file system. Then I clicked 'Install' and it gave error msg that 'no mount point for root'. 

I read somewhere that a disk can be partitioned up to 4 drives only. I already have made 3 partitions in Win 7. Now while partitioning, I formatted the E drive as ext4 but installer gave error saying 'no mount point for root'.

I tried installing within Windows also. But at the end of the process it gave error "Exception: Cannot download the metalink and therefore the ISO"

---

