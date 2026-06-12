---
title: "Acer Aspire booting Windows/Ubuntu instead of Windows/Android?"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Harry617 on 2011-04-28
Hi all. I wasn't sure where to put this. Sorry for the long title. 
Yesterday my brother was pestering me to install Ubuntu 10.10 

If it was an ordinary netbook I would have done this without a fuss. His netbook, however, was already dual-booting windows and android. He wanted me to install Ubuntu and remove android.
Here's the model:
[http://www.cnet.com.au/acer-aspire-one-happy-339307276.htm](http://www.cnet.com.au/acer-aspire-one-happy-339307276.htm)

I said no. After much pestering and complaining I gave in. I used Unetbootin to put the ubuntu iso on usb, booted into it, checked everything was working and installed. Here's where my problem starts.

I probably should have went to the forums before installing. When the installer got to the part on partitions I had a long look at it. On the simple partition creator thingo every thing seemed, well, simple. Until I saw the note below the picture depicting the size of the partitions. It said: "Three smaller partitions are hidden. use the advanced partition manager to..." (Can't remember the rest). So I went to the advanced partition manager thingo. There were four partitions there already. Three of them were formatted as ntfs, one was formatted as FAT32. I believe that two of the partitions were windows and android, and the others were boot managing things that were made by Acer. 
Confused I went bak to the simple partition thing and went ahead with the option it had as default, which looked right. 

Now Ubuntu is installed, but when he turns on his computer it boots directly into Ubuntu, without going to the list of things to boot from which it does on mine. Now he's telling me that he wants to use windows because he had some file on there (What a douche). I said I might be able to retrieve the file from Windows from Ubuntu, by opening the windows folders. But I couldn't find them.:confused:

I need to find a way to get the computer to boot windows 7 and Ubuntu.
Can someone tell me what's happened, and how I can get it to boot windows as well? I'm really confused.
Thanks in advance!

---

### Post by lynrock on 2011-04-28
Hi, got an Acer Aspire One D255 for Xmas and while I have no complaints about the hardware the software installation was awful. Mine came with the following: Primary Partition 1 - Windows recovery; Primary partition 2 - Android; Primary partition 3 - small boot partition; Primary partition 4 - extended; Logical partition 5 - Windows 7 Starter (Using the remainder of the disk).
The reason for the boot partition was because Windows won't boot from a logical partition, but then they could just have installed Windows on P3.
If your brother's was the same then I'd guess that the Ubuntu install either wiped the disk and started from scratch or created a new partition after Win 7, which would be Logical partition 6. Use the 'Disk Utility' in the System > Administration menu to check. If it has done this it would create a booting problem with none of the operating systems on primary partitions. Perhaps Grub could chainload to the boot partition but I don't know for sure.
On mine I repartitioned from the live Ubuntu before I attempted an install. I left the first partition (which shows up as 'PQ Service'), wiped the rest, then made new partitions, P2 30GB NTFS, P3 15GB ext4, P4 extended, P5 15GB ext4, P6 remaining space ext4 for data, P7 swap.
I then rebooted, was told that Win7 was missing would I like to recover it. Yes. The recovery process discovered the only available NTFS partition and reinstalled there. Then I installed Ubuntu on P3. Grub successfully found Win7 and added it to the menu. On a positive note Ubuntu 10.10 (standard desktop edition) worked flawlessly out of the box for me.

---

### Post by Harry617 on 2011-04-28
Thank you!:D
I'll go check the Disk Utility and come back.

---

### Post by Harry617 on 2011-04-29
Attached are a couple screenshots of the disk utility manager since I don't understand that stuff. :)

---

### Post by lynrock on 2011-04-29
Unfortunately that suggests your Windows install has been wiped. There is now just one large partition (with Ubuntu) and a small swap partition at the end.:(

---

### Post by Harry617 on 2011-04-29
Thanks. It's not that bad, it was only Windows 7 Starter. 
What's a swap partition?

---

