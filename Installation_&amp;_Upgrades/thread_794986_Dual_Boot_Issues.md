---
title: "Dual Boot Issues"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Krusnix on 2008-05-15
I realize that there is an overwhelming amount of issues running around here, but any help would be appreciated. I'm a newbie so forgive me.

I just recently reformatted my hard drive and installed xp, soon after hardy heron came out so I decided to install that as well. I've split my 500gb hard drive into two partitions one for windows, and one for linux, and I also have another hard drive that I use solely for media. 

The problem is when I start my computer the dual boot program (grub it's called?) doesn't load, instead windows loads up as if ubuntu had never existed. I've looked around the forums, and there are talks of re-installing grub, and doing some other things but I'm not sure of anything.

Here's any relevant information that may help:

```

Specs:
Microsoft Windows XP
Ubuntu Hardy Heron
Intel DR33TL Motherboard
Intel Q6600 Processor
4GB DDR-800
1 x 500GB 
1 x 120GB
No Graphics card.. (for now :P)
```

```
 sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ee57ee5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cda2cd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30862   247898983+   7  HPFS/NTFS
/dev/sdb2           30863       60801   240485017+   5  Extended
/dev/sdb5           30863       59582   230693368+  83  Linux
/dev/sdb6           59583       60801     9791586   82  Linux swap / Solaris

```

Thank-you! (I got the above information through the LiveCD don't know if it is still relevant..)

---

### Post by forestpixie on 2008-05-15
If you installed in this order - ubuntu, xp - you are right you need to reinstall grub. Not painful - you'll need you're livecd adn this page should do you nicely

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Pumalite on 2008-05-15
Did you partition before installing anything? Did you install Windows first in sda?

---

### Post by Krusnix on 2008-05-15
I had Windows installed first, and then through the partition manager in Ubuntu I partitioned the 500gb hard drive around 50/50 then installed Hardy Heron in the newly made partition. Thanks for replying guys :P

---

### Post by Pumalite on 2008-05-15
I would like to know if you achieved dual booting through Grub with that method of partitioning.

---

### Post by Mrtim!3x on 2008-05-15
i too am having the same issue. i am trying to install 8.04 and have dual boot to XP media center (my OEM OS). an i installed it but i never get grub, and i have reinstalled it. my specs are:

Dell E-510
2 X 500GB SATA II HDD
1 X 160GB SATA II HDD - this drive has; windows OS partition, recovery partition, and dell utility partition, is also where i put 8.04
4GB RAM
2.8 GHZ CPU

could it be the Dell partition(s)?

also in win xp i have found the Boot and recovery options TXT (under system properties, advanced, start up and recovery, manually chance options), here they are 

"[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Media Center" /fastdetect /NoExecute=OptIn"

as you can see it looks at only partition 2 (as default) on the HDD can this be changed or does something else need to be done. Does this matter?

---

### Post by Krusnix on 2008-05-15
> **Pumalite said:**
> I would like to know if you achieved dual booting through Grub with that method of partitioning.

Well, that is precisely the issue here. I can not reach the grub menu at all, as I mentioned before unfortunately when I start up it just goes straight to windows, and ignores ubuntu. Last year around this time this is how I had Gutsy installed, the only difference was I didn't have the 500gb hard drive, but instead split the 120gb hard drive. So I know it can work, but I'm not too sure how to go about it, thank-you for helping me with this.

---

### Post by Pumalite on 2008-05-15
The reason I asked is that you have to use the Vista partitioner. You cannot use the Ubuntu CD to partition; otherwise you'll never achieve dual booting through Grub.

---

### Post by Krusnix on 2008-05-15
Why is it that I did not have to do this with Gutsy? Because last year I just let the live cd installer just split my hard drive and install ubuntu. Sorry, I'm just trying to understand the situation a little better. I use Windows XP, so would I just format the partition that the live cd created and install ubuntu in there or something? Sorry if this doesn't make sense..

---

### Post by Pumalite on 2008-05-15
If it's XP, you should have no problems. I thought you were using Vista.

---

### Post by Krusnix on 2008-05-15
Ah for once I wished I use Vista, haha. Well this is quite unfortunate..

---

### Post by Pumalite on 2008-05-15
Try changing the boot order of the hard drives in BIOS.

---

### Post by Krusnix on 2008-05-15
Sir,  I do believe that we have fixed the problem. I changed the boot order of the drives, and I was able to boot into ubuntu. This is great! I appreciate the time, and effort of you helping me with this.

---

### Post by Pumalite on 2008-05-16
You are welcome. Good luck.

---

