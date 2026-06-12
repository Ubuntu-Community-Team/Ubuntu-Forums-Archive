---
title: "Partition Nightmare Please Help!"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by Th3P4rk2 on 2010-09-17
Hiya all, thanks for looking in and I hope you can help me!

Right...I have just brought a new laptop, its a HP dv3-4050

It has a 500gb hdd and came setup as follows,

[Boot settings 100mb][Windows][HP tools][Hp backup]

I am currently creating a backup of the windows 7 partition so I can restore this to the new partition when its ready so no need for drive shrinking etc because I can format completely and start from scratch.

I want to multiboot windows 7 64bit, Ubuntu 64bit and Backtrack linux and have an area accessible by windows and linux I would think looking something like this.

[EXT4 Ubuntu 120gb][NTFS Windows 120gb][EXT 4 Backtrack 30gb][Fat 16/32? Shared area][Swap]

but this odviously isnt possible given a maximum of 4 primary partitions here are my questions.


1) does the bootloader have to have its own primary partition? 2) Should I keep the windows bootloader thats already there or install grub or similar?
3) Am I able to have or do I even need a Swap partition for linux?
4) What is the best way to do this? 

Thanks in advance,

Ant

---

### Post by sikander3786 on 2010-09-17
First of all install Windows 7, then Backtrack and at last Ubuntu.

Windows 7 install will create 2 partitions, one 100MB primary system partition and second custom sized primary partition. 2 primary partitions will be enough. So the table will look like,

{Primary}
[100MB System Partition]
[Custom windows 7 Partition]
{/Primary}

{Extended}
{Logical}
[Backtrack Root Partition]
[Ubuntu Root Partition]
[Linux Swap]
{/Logical}
{/Extended}

I have heard Backtrack is based on Ubuntu so it must also be using GRUB. If so you can either install Backtrack or Ubuntu as the last OS so it picks up the other 2 OS and lets you triple boot.

You can also have separate home partitions if you like to.

You can use a single Swap partition for both Ubuntu and Backtrack.

Regarding your question.
1. GRUB will install in the primary partition created by Windows.
2. I recommend that you install GRUB. Windows boot loader is unable to recognize Linux. If you need a Windows based boot loader, there is EasyBCD. Still GRUB is way better than that.
3. You surely will need some SWAP space.
4. The whole story above. :-)

---

### Post by srs5694 on 2010-09-17
You posted this exact same problem in [this thread](http://ubuntuforums.org/showthread.php?t=1576420) in the General Help subforum. Could a moderator please merge the threads?

---

