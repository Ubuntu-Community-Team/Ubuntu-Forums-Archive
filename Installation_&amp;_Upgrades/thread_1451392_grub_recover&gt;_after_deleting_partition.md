---
title: "grub recover&gt; after deleting partition"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by Thomas Garman on 2010-04-10
I installed Lucid 10.04 on a 10 GB partition on my netbook just to test it out but actually it won't even start (all I get is a splash scree and then it hangs forever...) so I deleted that partition (it is now blank space on the HDD) but then when I restarted the grub goes straight into recovery mode and I can't boot anything.

So, can anybody say in an easy line or two how to install the GRUB2 back into the system so that it will detect the various partitions and boot again?

I am assuming that when I deleted the Lucid partition it deleted the GRUB/MBR that what installed on that partition?

---

### Post by nitstorm on 2010-04-10
Maybe this could help???

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by Thomas Garman on 2010-04-10
That seems rather complicated.  In that case I might as well just reinstall 9.10 from the liveCD and will just restore the GRUB to the way it should be...

I don't see why there isn't some sort of "install grub" and then "update grub" method of detecting the partitions that doesn't involve so many steps (that may or may not work).

---

### Post by oldfred on 2010-04-10
It depends on what version of grub your existing install has:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Thomas Garman on 2010-04-10
Well, I am marking this as solved because the easiest solution is just to "reinstall" the non-functional Lucid Beta 2 ISO on the 10 GB partition, and then boot into my 9.10 partition every time because anything else is a massive time suck that may or may not work.

---

### Post by Thomas Garman on 2010-06-04
> **Thomas Garman said:**
> Well, I am marking this as solved because the easiest solution is just to "reinstall" the non-functional Lucid Beta 2 ISO on the 10 GB partition, and then boot into my 9.10 partition every time because anything else is a massive time suck that may or may not work.


Actually after I wrote this I discovered another way to fix the problem...  I deleted my Ubuntu partitions with GParted and then  using my Vista Ultimate OEM installer disk (or it also worked with my Windows XP OEM installer disk) ran

bootrec.exe /FixMbr 

in the command line terminal.  This restored the Windows partition as the partition into which the computer boots and then I reinstalled Ubuntu and used AptonCD to put all the packages back into the OS.

---

