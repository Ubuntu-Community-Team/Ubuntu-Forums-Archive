---
title: "Help needed setting up PC with UBUNTU"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by HughsterRooster on 2008-06-05
Please, I am in DIRE need of some advice. 
I am trying to build a pc from scratch, and cannot work out what needs to be done to get an operating system on it.
I have a 2Core1333-2.66G cpu and a seagate 1terrabyte SATA hardrive, all brand new.
When I boot up with the Ubuntu 8.04 LTS cd I get the following error:

Installing Ubuntu onto a brand new machine with no o/s.
Get the error:
Code: Bad EIP value
EIP: [<31c00f01>] 0x31c00f01 SS:ESP 0068:f7c33f33
---[ end trace ca143223eefdc828 ]---
Kernel panic - not syncing: Attempted to kill init!


Do I need to format or partition the hardrive first?
How do i do this?

Any help appreciated
Thanks

---

### Post by jualin on 2008-06-05
what version of Ubuntu are you trying to install?. In theory the whole formatting and partitioning is done during the installation so that should not be the problem. Did you boot up the computer with the Live CD and then selected Install Ubuntu?

---

### Post by HughsterRooster on 2008-06-05
Ubuntu 8.04 LTS desktop version.
And yes, I booted from the cd and selected install Ubuntu.

---

### Post by wpshooter on 2008-06-05
BEFORE, you attempt to install the O/S you should check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.  Have you done that ?

---

### Post by HughsterRooster on 2008-06-05
Thought I had, but that was the checksum I checked.
Have just tried it and I get exactly the same message when checking the cd from the boot screen. 
Have tried 2 seperate install cds, same thing.

---

### Post by wpshooter on 2008-06-05
My initial thought would be, do you by chance have another SATA hard drive (of less capacity) laying around that you could try.  That would be my first troubleshooting step.

---

### Post by HughsterRooster on 2008-06-05
No other drives. Its a brand new Seagate drive. 
I can get to it via the command line and view the directory structure, but thats about it.

---

### Post by wpshooter on 2008-06-05
> **HughsterRooster said:**
> Thought I had, but that was the checksum I checked.
Have just tried it and I get exactly the same message when checking the cd from the boot screen. 
Have tried 2 seperate install cds, same thing.

Are these CDs that you burned or did you receive them from Ubuntu ?

Did you burn them at 4x or less ?

---

### Post by wpshooter on 2008-06-05
P. S. - Can you boot this system to a WIN98 bootable diskette ?

---

### Post by HughsterRooster on 2008-06-05
I burned them onto DVD discs at 2x speed.

---

### Post by wpshooter on 2008-06-05
> **HughsterRooster said:**
> No other drives. Its a brand new Seagate drive. 
I can get to it via the command line and view the directory structure, but thats about it.

Does this drive already have another O/S on it ?

---

### Post by twright on 2008-06-05
if you are using an ext3 partition try xfs instead

---

### Post by wpshooter on 2008-06-05
> **twright said:**
> if you are using an ext3 partition try xfs instead

Maybe I am misunderstanding this but I did not think he had Ubuntu or any Ubuntu related paritions installed at all on this hard drive yet.  Am I incorrect ?

---

### Post by jualin on 2008-06-05
how much RAM do you have, because if you dont have enough then you need to try the Alternate CD since the Live CD cant boot without enough RAM. How about trying the Alternate CD from [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/8.04/]("http://mirror.csclub.uwaterloo.ca/ubuntu-releases/8.04/") or from other Ubuntu Download Mirror found on the Ubuntu website [http://www.ubuntu.com/getubuntu/downloadmirrors]("http://www.ubuntu.com/getubuntu/downloadmirrors"). Maybe using the Alternate CD might be the solution for your problem.

---

### Post by wpshooter on 2008-06-05
> **jualin said:**
> how much RAM do you have, because if you dont have enough then you need to try the Alternate CD since the Live CD cant boot without enough RAM. How about trying the Alternate CD from [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/8.04/]("http://mirror.csclub.uwaterloo.ca/ubuntu-releases/8.04/") or from other Ubuntu Download Mirror found on the Ubuntu website [http://www.ubuntu.com/getubuntu/downloadmirrors]("http://www.ubuntu.com/getubuntu/downloadmirrors"). Maybe using the Alternate CD might be the solution for your problem.

He said this is a brand new build, surely he has enough RAM !!!

---

### Post by HughsterRooster on 2008-06-05
2 Gigs of ram. No operating system as its a brand new system. I don't know if there are any partitions yet(?)

---

### Post by jualin on 2008-06-05
Dude relax, I was just trying to help. You will be surprised how many people where I live try building a PC and then use little RAM because they dont know the purpose of it. But I guess you are right he should have enought RAM, maybe that is not his problem. I read in another post that the error that he is getting is hardware related so maybe there is something wrong with his Hard Drive, but that's just my guess.

*edit* ok i just saw it 2 GBs of RAM, that's enough RAM, you should not have any problem with the LIVE CD

---

### Post by wpshooter on 2008-06-05
Then humor me and try this.  Get [www.killdisk.com](www.killdisk.com) and WIPE that drive completely and then try to install Ubuntu afterwards on the completely clean drive and let me know if you still have the same problem.

Thanks.

---

### Post by wpshooter on 2008-06-05
> **jualin said:**
> Dude relax, I was just trying to help. You will be surprised how many people where I live try building a PC and then use little RAM because they dont know the purpose of it. But I guess you are right he should have enought RAM, maybe that is not his problem. I read in another post that the error that he is getting is hardware related so maybe there is something wrong with his Hard Drive, but that's just my guess.

*edit* ok i just saw it 2 GBs of RAM, that's enough RAM, you should not have any problem with the LIVE CD

Am relaxed, but not to many people that are going to use the equipment he stated and put 64mb of RAM in it !!!

---

### Post by HughsterRooster on 2008-06-05
Could it be something as stupid as the fact that I have burned the iso onto a DVD disc instead of a CD?

---

### Post by jualin on 2008-06-05
according to the ubuntu website you should use a CD, but i dont know if using a DV Dwould make a difference, maybe it will.

---

### Post by wpshooter on 2008-06-05
I think that theorically you can use either but my preference would be to use a CD-RW.

That way if some goes bonk, then you can just COMPLETELY/FULL erase it and then reuse the CD-RW over and over and over again.

---

### Post by twright on 2008-06-05
> **jualin said:**
> Dude relax, I was just trying to help. You will be surprised how many people where I live try building a PC and then use little RAM because they dont know the purpose of it. But I guess you are right he should have enought RAM, maybe that is not his problem. I read in another post that the error that he is getting is hardware related so maybe there is something wrong with his Hard Drive, but that's just my guess.

*edit* ok i just saw it 2 GBs of RAM, that's enough RAM, you should not have any problem with the LIVE CD
or buy the RAM but don't connect it all properly :)

i would do a bit of googling to check all of your hardware is supported and try another OS (or your motherboards diagnostics tools, if it has any)

---

### Post by Victormd on 2008-06-05
> **HughsterRooster said:**
> Installing Ubuntu onto a brand new machine with no o/s.
Get the error:
Code: Bad EIP value
EIP: [<31c00f01>] 0x31c00f01 SS:ESP 0068:f7c33f33
---[ end trace ca143223eefdc828 ]---
Kernel panic - not syncing: Attempted to kill init!


Bad EIP value can be related to hardware, when the kernel panics, as it is unable to detect or use the piece of hardware correctly using the base kernel modules. Most likely it is an issue with the kernel not being able to set the pci address. 

I would suggest you do a compatibility check between all your hardware, including RAM/Motherboard and any PCI cards you might have...

---

### Post by HughsterRooster on 2008-06-06
Thanks for all the advice, going to try install Windows Vista (*shudder*) tonight.

---

