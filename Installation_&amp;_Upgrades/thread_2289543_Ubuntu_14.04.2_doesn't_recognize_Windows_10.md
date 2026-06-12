---
title: "Ubuntu 14.04.2 doesn't recognize Windows 10"
date: 2015-08-05
forum: Installation &amp; Upgrades
---

### Post by adam157 on 2015-08-05
I was wondering how to dual boot Ubuntu 14.04.2 with Windows 10. I downloaded Ubuntu, put it on a USB and booted into it. However when I went to install it, the option to dual boot it with Windows 10 wasn't there. The only option it gave me was delete everything and install Ubuntu. Any suggestions as to what to do?

---

### Post by ruzekle on 2015-08-05
You can partition Windows 10.

[http://www.partition-tool.com/resource/windows-10-partition-manager/resize-partition-windows-10.htm](http://www.partition-tool.com/resource/windows-10-partition-manager/resize-partition-windows-10.htm)

Go to your installer. Select the advanced installation (or "something else" when asked how you'd like to install). Format and install Ubuntu in the correct partition.

---

### Post by Vladlenin5000 on 2015-08-05
> **ruzekle said:**
> You can partition Windows 10.

Err... NO.

You can and should shrink the Windows 10 partition and for that the native Windows tools are enough. The purpose is to have unallocated space for the Ubuntu installer to create its own partitions, automatically or manually ("Something else").

Then you MUST reboot TWICE to allow Windows *chkdsk*to correct any logical errors resulting from the shrinkage.

Then you MUST disable fastboot in Windows. Otherwise Windows will keep its partitions hibernated (i.e. marked as "in use") and the Ubuntu installer won't be able to detect the other OS.


** DO NOT use any other than the Windows tools to shrink partitions used by anything newer than Vista. You have been warned. **

---

### Post by adam157 on 2015-08-05
So I disabled fastboot. You mentioned that I also need to shrink the Windows 10 partition to give space for Ubuntu. I went to Disk Management and there are currently three partions: System Reserved, Windows (C), and Healthy (Recovery Partition). Do I just shrink Windows (C) and if so what do I do after that?

---

### Post by yancek on 2015-08-05
>  Do I just shrink Windows (C) and if so what do I do after that? 		

When you have finished resizing the windows partition and running chkdsk as mentioned above, boot the Ubuntu installation medium and you should see unallocated space and you can then create a partition or partitions and format them.  Make sure you select the manual "Something Else" option under Installation Type.

---

### Post by adam157 on 2015-08-05
Okay, I allocated 50 GB to Ubuntu. However when I go to "Something Else" I have no idea what to do. Can you walk me through the steps? Also will Grub recognize Windows 10? The Ubuntu Installer on the Disk doesn't.

---

### Post by Vladlenin5000 on 2015-08-05
You only need to create two partitions, / and swap. If you have plenty of RAM you can even go without swap but better have it (small, 2GB) just in case. So...

1. Create a new partition with / as mount point, mark it to format as EXT4 (~48GB)
2. Create another partition in the remaining space and just select swap.

Confirm and proceed. Ubuntu will be installed in the partitions you just created.
It should recognize Windows 10, provided you disabled fastboot -and- did a shutdown (reboot overrides it). If not, there are a few things you can do but let's not think about it for now.

---

### Post by yancek on 2015-08-05
The link below has a very good, detailed tutorial on installing Ubuntu.  Scroll down to Disk Management and partitioning and review that first.  Further down on the page is a section for Installation, Step by Step.  Make sure you select the Installation Type option "Something Else".

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

One other important factor is are you using UEFI/GPT to boot windows 10?  If so, you need to install Ubuntu with the same method.

---

### Post by adam157 on 2015-08-05
I did what you guys said and I successfully have Ubuntu installed alongside with Windows 10. Thank you guys so much! Appreciate the help.

---

### Post by ghostdriver on 2015-10-24
Hi,

I have the same problem but the solution here do not solve the fact that Ubuntu 14.04.3 64bits do not recognize Win10 installation (even though, I have disable fastboot)

Any other suggestion to try?

---

### Post by Mark Phelps on 2015-10-25
> **ghostdriver said:**
> Hi,

I have the same problem but the solution here do not solve the fact that Ubuntu 14.04.3 64bits do not recognize Win10 installation (even though, I have disable fastboot)

Any other suggestion to try?

It is NOT fastboot -- that's a BIOS/UEFI option; instead, it is Fast Startup -- that is a Win10 hibernation option.  They are two different options.

---

### Post by Vladlenin5000 on 2015-10-25
> **Mark Phelps said:**
> It is NOT fastboot -- that's a BIOS/UEFI option; instead, it is Fast Startup -- that is a Win10 hibernation option.  They are two different options.

Exactly, my mistake. I stand corrected and thank you.

---

### Post by ghostdriver on 2015-10-26
Yes, I disable "Fast Startup" following this directions
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Then, reboot a couple of times and shut down the system. I start it up and load Ubuntu installer from the USB key. But I still encounter the same problem, Ubuntu installation do not recognize any OS in the HDD

---

