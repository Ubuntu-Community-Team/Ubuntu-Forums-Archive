---
title: "Grub + Fasttrak100"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by Redscare on 2007-06-26
Hello all. I have sincerely tried everything I could before I came here. I am currently on a livecd from a Micron PC Millenia Desktop. It's pretty old (2001), but I can't just watch it sit and take up space, so I wanted to set up Ubuntu on it. I had already done this on my laptop and found it to be extremely simple, and I had high hopes for the PC. I used the same 7.04 live cd I used for my laptop (i386). It installed fine and prompted me to restart the computer. I removed the cd and the computer restarted. The regular bootscreen showed, after which fasttrak100 detected the IDE drives. Here is what happened after that:
```

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 2
```
I suspect it has something to do with the Fasttrak100 Ultra RAID/SCSI controller. Ubuntu itself is installed on IDE3 (hde). I have never installed anything on this computer before aside from windows me/2000/xp. Here are some (I believe) important specs:
```

Processor:AMD T-Bird Athlon 1.2GHz 266FSB 256K PGA(Socket A)
Memory: 16 x 64 128MB 266MHz DDR SDRAM DIMM 
Hard Drive: Western Digital 40GB IDE ATA100 7200RPM
Controller Card: Promise.FastTrak.100 Ultra ATA/100.RAID
```
The specs site is: [http://support.mpccorp.com/apps/complist.asp?SerialNo=2820091-0001]("http://support.mpccorp.com/apps/complist.asp?SerialNo=2820091-0001")
Please, I really want this computer to also boot Ubuntu. Also, if there is no direct solution is there at least a way to somehow get to Ubuntu? (maybe another bootloader?) By the way, I don't have any important data on this computer and don't mind experimenting (but don't really want to:) ).

---

### Post by Redscare on 2007-06-26
I think it would also be an important detail to know that the two drives are in what is called an array. If I don't have an array I am asked to insert system disks in an error before grub even loads (tried with no array before and after install). Also, Ubuntu is the only operating system currently on the computer.

---

### Post by logos34 on 2007-06-26
> **Redscare said:**
> Hello all. I have sincerely tried everything I could before I came here. I am currently on a livecd from a Micron PC Millenia Desktop. It's pretty old (2001), but I can't just watch it sit and take up space, so I wanted to set up Ubuntu on it. I had already done this on my laptop and found it to be extremely simple, and I had high hopes for the PC. I used the same 7.04 live cd I used for my laptop (i386). It installed fine and prompted me to restart the computer. I removed the cd and the computer restarted. The regular bootscreen showed, after which fasttrak100 detected the IDE drives. Here is what happened after that:

```
GRUB Loading stage1.5.
GRUB loading, please wait...
**Error 2**
```

I suspect it has something to do with the Fasttrak100 Ultra RAID/SCSI controller. Ubuntu itself is installed on IDE3 (hde). I have never installed anything on this computer before aside from windows me/2000/xp. Here are some (I believe) important specs:

[CODE]Processor:AMD T-Bird Athlon 1.2GHz 266FSB 256K PGA(Socket A)
**Memory**: 16 x 64 **128MB** 266MHz DDR SDRAM DIMM

> Grub Error 2 [from the GNU/GRUB manual]:

    2 : Bad file or directory type
        This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 

There is a problem loading grub, probably due to the raid controller.  You might download [SuperGrub CD]("http://supergrub.forjamari.linex.org/") and use that to try to boot ubuntu installation.  

I don't know how you managed to runt he live cd on that desktop.  May work fine on the lappy, but with only 128mb ram the going will be pretty slow.  You'd be better of with Xubuntu and the lighter Xfce desktop.

Didn't you read the system requirements on the download page?

> _Ubuntu 7.04 Release Notes_
These release notes document known issues with version 7.04 of Ubuntu, Kubuntu and Edubuntu.

_System Requirements_
The **minimum memory requirement for Ubuntu 7.04 is 256MB** of memory. With only the minimum amount of memory available, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed.


---

### Post by Redscare on 2007-06-26
Thank you for the answer. I think I upgraded the memory on the desktop, so that's about fine. I continue to get errors with the SuperGrub CD. I'll continue experimenting, but whatever I try there is an error having to do with invalid or not-found files. Thank you for the response, but please, can someone help me? If I use the alternate CD, is there a chance that will work?

---

### Post by Redscare on 2007-06-27
Please, I need this urgently. If this is not possible please say so!!!

---

### Post by Redscare on 2007-06-27
I have some more information: the single raid array is shown as two drives, so obviously Ubuntu looks past that. Is there a way to get it to recognize the raid array or to remove the array?

---

### Post by Redscare on 2007-06-27
Also, there is some sort of lvm vg drive. Please, someone help?

---

### Post by Redscare on 2007-06-28
Perhaps I have come to expect too much of these forums, but with all due respect the responses to this simple and seemingly fundamental question are few in number and not effective. I, once again, politely request an answer. Please, can someone help?

---

### Post by Redscare on 2007-07-07
Well thank you for the numerous replies to this thread. I ended up solving the problem by plugging the drive into ide2 and installing from there. No raid but it works.

---

