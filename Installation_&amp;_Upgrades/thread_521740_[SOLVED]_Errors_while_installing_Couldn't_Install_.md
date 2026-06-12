---
title: "[SOLVED] Errors while installing: Couldn't Install Base System"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by Arhuma on 2007-08-09
Hi,

I’m new to GNU/Linux. I had Win98 and XUbuntu installed in dual boot on an old PII 350 mhz , 6.5 GB, 256MB RAM. As I wanted to give XUbuntu more space, I thought that re-installing would be a good idea but it wasn’t. When trying to install from a XUbuntu 7.0.4 Alternate I keep getting these warnings and errors:

“The target file system contains files from a past installation. These files could cause problems with the installation process and if you proceed, some of the existing files may be overwritten. Proceed with installation to unclean target?”

I say YES but then I get these errors:

Debootsprap Warning

file:///cdrom/pool/main/o/openssl/libssl..... was corrupt

I keep saying “continue” and getting similar errors, at the end it tells me it wasn’t able to install the Base System. 

I’ve tried searching the web for ideas but couldn’t find a solution. Could you please help?**[B][B][B][B][B][B][B]:mad:**[/B][/B][/B][/B][/B][/B][/B]:)

---

### Post by merlinus on 2007-08-09
You might use gparted live cd to format the partitions before trying to install:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by Arhuma on 2007-08-10
> **merlinus said:**
> You might use gparted live cd to format the partitions before trying to install:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin


How do I use gparted to prepare my HD for Xubuntu installation? I've read the guides but can't figure out. This is the info gparted gives me about my HD:

DEVICE INFORMATION

Model: Maxtor 90648D3
Size:   6.03 GB
Path: /dev/hda

Partition:      /dev/hda1
File System: fat 32
Size:            6.04 GiB
Used:          12.08 MiB
Unused:      6.02 GiB
Flags:         boot, lba

---

### Post by Arhuma on 2007-08-11
I used gparted and obtained this:

/dev/hda1  ext3  5.53 GiB
/dev/hda2 linux-swap  509.88 MiB

Then I downloaded again the file xubuntu-7.0.4-alternate-i386.iso (twice, once with utorrent, and a second time with Firefox from the  Xubuntu site). I burnt the immage at  l'immagine at 4x and 12X on five CD's. I used these CD's:

TDK CD-RW 4x-12x
TDK CD-R80 UP TO 52x Speed (this has a minimum of 12x)

And after all this, I still get the same errors as before:

- Unable to download packages (I'm not connected while installing)
- Unable to unpack
- Files are corrupted

MD5SUM check says CD-ROM is damaged for all 5 CD's. Even when I check an official Ubuntu CD it says it's damaged!

Please help. I need a GNU/Linux OS system in that machine for work.

Arhuma**[B][B][B]**[/B][/B][/B]

---

### Post by vexorian on 2007-08-11
The first error is about trying to install over another install, but

The important issue is that your CD appears corrupted to the installer.

What I reccommend is:
- Do a RAM check (using the live cd's memtest, it could be that a failed RAM chip is making your computer have hallucinations, this is a real treat, it happened to me)

- then "verify CD for errors"

---

### Post by Arhuma on 2007-08-12
> **vexorian said:**
> 
The important issue is that your CD appears corrupted to the installer.

What I reccommend is:
- Do a RAM check (using the live cd's memtest, it could be that a failed RAM chip is making your computer have hallucinations, this is a real treat, it happened to me)

- then "verify CD for errors"

I highlighted the memtest option, pressed enter and got this:

GNU GRUB version 0.95 (639k lower / 261056k upper memory)

Then I highlighted the check CD option and got the same risult. Maybe these options are not working?

Anyway the Live CD (Ubuntu 4.10) is working, I even go to the internet with it!

Any ideas?**[B][B][B]**[/B][/B][/B]

---

### Post by kelvin spratt on 2007-08-12
you need 2  partitions formatted ext3, 1 for root, 1 for home, and a small partition formated ext2 linux swap, to load Linux on you hard drive i don't think you have a ram problem as you are running the live disc Ok. you can partition and format off  the live disc.if you need help with partitioning just shout and somebody will give you help or a link to step by step walk through.

---

### Post by vexorian on 2007-08-12
> **Arhuma said:**
> I highlighted the memtest option, pressed enter and got this:

GNU GRUB version 0.95 (639k lower / 261056k upper memory)

Then I highlighted the check CD option and got the same risult. Maybe these options are not working?

Anyway the Live CD (Ubuntu 4.10) is working, I even go to the internet with it!

Any ideas?**[B][B]**[/B][/B]
normal behaviour of mem test and cd check is pretty different from it. So I got no idea what's going on...

You may try doing memtest from grub instead of live CD or from 4.10 's CD

---

### Post by Arhuma on 2007-08-12
> **vexorian said:**
> normal behaviour of mem test and cd check is pretty different from it. So I got no idea what's going on...

You may try doing memtest from grub instead of live CD or from 4.10 's CD

I've downloaded Xubuntu 7.0.4 Desktop and I'm doing the Memtest with that. In fact it's completely different from what I had before under Ubuntu 4.10. Now it's working! It's been running for 4 hours now and it's arrived at 45% of the test. It will probablu take all night or so. But at least I will know if I have a memory problem. Sorry, not me, the pc :)

---

### Post by vexorian on 2007-08-12
If it goes all right with the new cd it could have really been a CD issue. But it is always good to make sure RAM is all right although it does take a lot of time to do the test.

---

### Post by Arhuma on 2007-08-12
> **vexorian said:**
> (...) although it does take a lot of time to do the test.

I've just realized that once it has finished all tests (from test #1 to test #10), it starts all over again. Do I have to stop it myself? How? I can't see any option to stop it on screen!

---

### Post by vexorian on 2007-08-12
You can safely reboot, memtest does no changes or mount hard drives or anything so its exit command is just rebooting it.

  in theory it is good to repeat the test at least twice, but I don't really think that's so required. Then the conclusion I can come to is that your CD had issues.

---

### Post by Arhuma on 2007-08-13
> **vexorian said:**
> You can safely reboot, memtest does no changes or mount hard drives or anything so its exit command is just rebooting it.

  in theory it is good to repeat the test at least twice, but I don't really think that's so required. Then the conclusion I can come to is that your CD had issues.

Ok. After more than 5 hours running the test, I have this:

ERROR SUMMARY

Test 0: Errors: 0
Test 1: Errors: 0
       2:        : 0
       3:        : 133
       4:        :
       5:        : 29428
       6:        : 19519
       7:        : 1136
       8:        : 0
       9:        : 0
      10:       : 0

What's all those errors about? Is it my HD damaged? Or my RAM? Is there anything I cand do apart from throwing my pc out of the window?

---

### Post by Arhuma on 2007-08-13
The problem was a damaged  128 MB RAM memory module. I opened the case, removed the piece of RAM and everything returned normal. I have my Xubuntu installed now.
:)

---

