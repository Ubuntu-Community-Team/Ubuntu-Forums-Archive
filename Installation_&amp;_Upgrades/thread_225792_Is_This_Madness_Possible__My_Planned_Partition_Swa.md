---
title: "Is This Madness Possible?  My Planned Partition Swap?"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by AkiraXXX on 2006-07-30
I will not bore you with the standard "I've worked for weeks on my setup and I don't want to lose it" fare.  On second thought, "Oh sweet mother of mercy, pleeeeeeze don't let me lose my setup!"  Honestly, I realize that the majority of you know what I've gone through to make a tablet PC dual boot, work like a tablet in both operating systems, join it to a Windows domain and authenticate to active directory, etc.  It has been hell.  O.K., here's the deal...

I have a Lenovo X41 Tablet which dual boots to Windows XP.  I wish to try running my Windows applications from a VMWare machine.  I've had some limited success, but will only know for sure once I install a fully-configured virtual machine into VMWare.  My problem is that my XP VMWare machine will need to be about the size of all the available storage space left on my primary Ubuntu partition.  I've included a snapshot from QTParted taken from a live Kubuntu disk (I'm running Ubuntu 6.06 on the hard drive).

My goal here is to change the size of the Windows XP paritition and increase the size of the Ubuntu paritition (where have we heard THAT before?)  I know that I cannot change the size of the partitions from the front, so I was wondering if this would work:

1) Resize the Windows XP partition from 31.96GB down to about 16GB.  That is barely enough for Windows XP to run effectively with the current configuration.

2) Take the freed 16GB and make it a new Ubuntu data partition.

3) Move the current Ubuntu boot partition to the newly created Ubuntu data partition.

5) Make the newly created Ubuntu data partition the bootable partition.

6) Reallocate/resize the partitions so it will end up looking something like (numbers are, of course, approximate):

/dev/sda1 NTFS  16GB
/dev/sda3 ext3  34GB
/dev/sda4 swap  01GB
/dev/sda2 fat32 04GB

My trouble is this:  I have no idea what I am doing.  Apart from that, I think we're fine.  Really, I've never done this before so I'd love some input from those who have had some experience with this stuff.  The biggest questions raised here are:

1) Can I reduce the Windows XP partition and still have it boot?  (I think the answer to this one is "yes")

2) Can I reclaim the space saved from reducing the Windows partition into an Ubuntu data partition? (Again, I think the answer is "yes", but I'm starting to get concerned about the number of partitions)

3) Can I somehow move my current Ubuntu boot partition to the newly created Ubuntu data partition without resizing it since it would be about 2.5GB larger, but is only using about 4GB of space?

4) Can the newly created Ubuntu data partition be made the boot partition in such a way that GRUB will know it and it will work?

5) Can I then resize the new Ubuntu boot partition to reclaim the space of the previous Ubuntu ext3 partition so they become one large partition?

6) Will I ever stop asking questions?

I'm sorry to have gone on so long, but I wanted to be clear in what I am trying to do.  Any and all help is greatly appreciated.  

AkiraXXX

---

### Post by wieman01 on 2006-07-30
> **AkiraXXX said:**
> 1) Can I reduce the Windows XP partition and still have it boot?  (I think the answer to this one is "yes")

2) Can I reclaim the space saved from reducing the Windows partition into an Ubuntu data partition? (Again, I think the answer is "yes", but I'm starting to get concerned about the number of partitions)

3) Can I somehow move my current Ubuntu boot partition to the newly created Ubuntu data partition without resizing it since it would be about 2.5GB larger, but is only using about 4GB of space?

4) Can the newly created Ubuntu data partition be made the boot partition in such a way that GRUB will know it and it will work?

5) Can I then resize the new Ubuntu boot partition to reclaim the space of the previous Ubuntu ext3 partition so they become one large partition?

6) Will I ever stop asking questions?

I recommend to use Partition Magic under Windows to make the necessary changes. Great tool & very reliable.

Answers:

1) Yes, no problem.
2) Yes, also no problem.
3) Yes, in principle you can. But watch out, the HDD numbering as it appears in GRUB for booting your Linux partitions will change as a consequence. You need to be aware of it and change the settings in GRUB later on (with the live CD??). I have not done this before, but I am planning to do just that in the weeks to come in order to wipe out my Windows partition.
4) You will have to know what HD number is assigned to the new partition and change the GRUB settings accordingly. But yes, that is possible.
5) Again the answer is yes. Use Partition Magic to do it.
6) Hope you never will. :-)

Let me know if this helps and if you have more question. I recommend to get familiar with Partition Magic as it will all the mentioned changes much easier for you.

---

### Post by AkiraXXX on 2006-07-30
Alas, when I tried Partition Magic v8, all I got was an error message.  It thought there was a problem on my hard drive in a certain sector and asked if it could "fix it".  Well, I'm not that brave. ;)  I booted a Windows 98 disk to run Partition Magic so no drives would be mounted.  It has never been an issue in the past.

---

