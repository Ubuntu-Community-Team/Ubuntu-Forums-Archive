---
title: "Unable to detect existing partitioning"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by chezz on 2010-02-28
I found quite a few threads on problems similar to this but they weren't exactly the same. Also, I'm new here so I didn't really get what they were saying. Anyway:

I currently have 1 HDD with 2 partitions (C:,D: ) and on C: I have Windows Vista Home Premium (32-bit) installed, which I use frequently. On D:, I have Windows 7 (64-bit) Release Candidate installed. Since the RC is expiring soon, I wanted to install Ubuntu cleanly over that partition.

I used a 9.04 Ubuntu disk and when it came to the partition choice menu, I got this message.

[[IMG]http://i186.photobucket.com/albums/x57/huanyanqi/th_IMG_0225.jpg[/IMG]](http://i186.photobucket.com/albums/x57/huanyanqi/IMG_0225.jpg)

Then when I clicked on Specify Partitions Manually, I got:

[[IMG]http://i186.photobucket.com/albums/x57/huanyanqi/th_IMG_0226.jpg[/IMG]](http://i186.photobucket.com/albums/x57/huanyanqi/IMG_0226.jpg)

There are 2 issues here:
1. It detects Vista (sda1,sda2), but doesn't detect 7 (sda3,sda4)
2. It doesn't detect the current C:,D: partitioning.

Can someone please help? Thanks.

---

### Post by darkod on 2010-02-28
According to this, you don't have 2 but 4 partitions. Have in mind that some partition might not show in Computer in windows. It's always best to check in Disk Management.

You can create a 5th partition, not like this. But if you want ubuntu to be installed instead of win7, no problem. And also no need to worry why 7 is not detected, you'll delete it anyway.

You can boot vista, delete the win7 partition, and leave that space as unallocated. DO NOT create any partition from it, not as ntfs from windows.

Then just boot the ubuntu cd again, start the installer, and in step 4 you will have one more option, Use Largest Available Free space. That will install ubuntu into the unallocated space you left.

My guess is that the 1GB /dev/sda1 partition is actually the boot partition from win7, although it gets wrongly recognized as vista loader. Ubuntu looks for the boot files, not your actual system partition. But even if this is correct, it's not stopping you doing the above.

If you really want to take a better look, you can run the boot info script from the ubuntu live desktop. The instructions are here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

PS. I just remembered. Windows usually combines the boo files if you have 2 versions installed. After deleting win7 system partition, try to boot vista few times. If it doesn't boot correctly, you might need to repair the boot process first using the vista install dvd and instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by chezz on 2010-02-28
> You can boot vista, delete the win7 partition, and leave that space as unallocated. DO NOT create any partition from it, not as ntfs from windows.


Just wondering, how do I delete the Win7 partition? :(

---

### Post by darkod on 2010-02-28
> **chezz said:**
> Just wondering, how do I delete the Win7 partition? :(

In windows in Disk Management. Easiest way to open it, hit windows button + R, type diskmgmt.msc, hit Enter.

You should be able to right-click the partition and select Delete. MAKE SURE you delete the correct one!!!

---

### Post by chezz on 2010-02-28
> **darkod said:**
> PS. I just remembered. Windows usually combines the boo files if you have 2 versions installed. After deleting win7 system partition, try to boot vista few times. If it doesn't boot correctly, you might need to repair the boot process first using the vista install dvd and instructions here

By the way, when I opened the Disk Management Utility, I found that under C: (which is the Vista partition), it says "healthy, system, boot, page file, active, crash dump, primary partition", while the Win7 Partition only says "primary partition". Does that mean that the boot files are located in C?

> **darkod said:**
> According to this, you don't have 2 but 4 partitions. Have in mind that some partition might not show in Computer in windows. It's always best to check in Disk Management.

As you mentioned, I noticed 2 unnamed partitions in Disk Management. Is it ok to ignore them? 

Thanks~!

---

### Post by darkod on 2010-02-28
> **chezz said:**
> By the way, when I opened the Disk Management Utility, I found that under C: (which is the Vista partition), it says "healthy, system, boot, page file, active, crash dump, primary partition", while the Win7 Partition only says "primary partition". Does that mean that the boot files are located in C?



As you mentioned, I noticed 2 unnamed partitions in Disk Management. Is it ok to ignore them? 

Thanks~!

Yes, it would mean 99% that it's OK to delete the win7 partition and the boot files are on the vista partition.
But even if you can't boot vista after deleting the win7 partition, don't panic. Have the ubuntu cd at hand and because it offers the Try Ubuntu option you can load the live desktop and work on it, even browse on internet, etc.

Just for information, instructions to restore different bootloaders are here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ottosykora on 2010-02-28
>There are 2 issues here:
1. It detects Vista (sda1,sda2), but doesn't detect 7 (sda3,sda4)
2. It doesn't detect the current C:,D: partitioning.<


what I can see from the picture, all partitions are detected and are present.
The one with w7 is the 'blue' one or nr3 on the list. The first one is very small so you hardly can see it on the graphical bar display, it very small portion at begining, and so it the last one, it can not be ssen opticaly on the colour bar.

---

### Post by chezz on 2010-03-01
So what I have done is that I deleted the D partition in which Win7 was in, then I installed Ubuntu using the Largest Available Free space option. I dragged 

the slider such that the C partition remained roughly the same size, and Ubuntu took up the remaining space.

Installation was fine, but when it restarted and GRUB took over, there were 5 options on the list.

The first 3 were Ubuntu options, but I don't remember what they are. Anyway I tried the first one and it worked. 

The last 2 were both called "Windows vista [Boot Loader]" or something like that, and the first one loaded into vista but couldn't proceed when it got to the 

desktop. My desktop icons and stuff didn't appear anyway, and the wallpaper was the default wallpaper 

So I tried the other Vista option, and it gave me the Windows Boot Loader screen (The previous Vista option didn't give me any options at all). There were 

still 2 options, Vista and Windows 7. Choosing Windows 7 gives an error and nothing much happens, since I had already wiped it. Choosing Windows Vista loads 

it fine and my files are there too. However, in My Computer, I can only see the C partition where Vista is in and I cannot see the other partition where 

Ubuntu is in. However, when I boot into Ubuntu, I can see the Vista partition.

However, the problems are:
1. What are the 3 Ubuntu options and do I need to get rid of the other 2 Ubuntu options?
2. Why are the 2 Vista Boot Loaders? Where did the first one (that doesn't work) come from? 
3. How do I remove the Windows 7 from the Windows Boot Menu list? (I can't seem to find the boot setup .ini file)
4. How do I see the Ubuntu partition in Vista?

Thanks!!

---

### Post by darkod on 2010-03-01
1. You can have more than one ubuntu kernel in the list, like 2.6.31-14, 2.6.31-17, 2.6.31-19, etc. Then for every kernel you have the normal mode and recovery mode (which can help you troubleshooting if the normal mode fails).
Also it is recommended to keep at least one older kernel in case the latest one gets corrupted or something.
You can remove kernels in Synaptic Package Manager, in the search box type linux-image-2.6.31-xx and from the list mark it for Complete Removal. Make sure you remove just the kernel you want to remove and to leave at least one kernel, if you remove all of them you can't boot.
2 and 3. Grub will create menu entries for all boot files it finds. I guess one of the two smaller partitions is some kind of tools or repair partition and it has boot files or traces of them. So it shows as the first vista entry. The second vista entry is giving you the bootloader with vista and 7 because as we said windows combines the boot files in one for both versions.
You would have to boot vista and use bcdedit.exe to remove the 7 option. The file should be in C:\boot I think, and it's probably a hidden folder. But I don't know the syntax to use it, google it.
4. Windows can't see linux partitions by default. On the other hand, linux has no issues seeing ntfs. You could make ubuntu visible from vista but I'm not sure it's recommended. I wouldn't let windows touch the ubuntu root partition, you can't depend on it. If you really want to make it show, again try google.

Later on, when you get more experienced, you might want to have a ntfs partition to share stuff between them. In that case both vista and ubuntu will be able to see it, and that partition will not be a system partition for any OS.

---

### Post by chezz on 2010-03-01
Thank you for your help! :)

---

### Post by Anger 2 on 2010-03-01
Chez,
I am not familiar with Vista but with XP you can see the Linux partitions. I Click    Start/control panel/administrative tools/disk management.On mine the first partition is grub,the second the OS and the third is the swap.

---

### Post by -kg- on 2010-03-01
> 1. What are the 3 Ubuntu options and do I need to get rid of the other 2 Ubuntu options?

> 1. You can have more than one ubuntu kernel in the list, like 2.6.31-14, 2.6.31-17, 2.6.31-19, etc. Then for every kernel you have the normal mode and recovery mode (which can help you troubleshooting if the normal mode fails).

The third option will be a "MEM TEST" option.  This will run a test of system RAM for RAM integrity.

You should leave all these selections in place.  As darkod said, every time you upgrade the kernel, a selection is added to the GRUB menu which points (and boots) to each kernel present in the installation.  You should keep at least one of the previous kernels in case of problems, and you can delete any older kernels through Synaptic.

I was going to tell you to run "sudo update-grub" at first, but if you are installing Jaunty (9.04) instead of Karmic (9.10), you will be installing legacy GRUB and, after deleting an old kernel, you will need to edit /boot/menu.lst (you will need to use sudo) to delete the old kernel entry from the list.

---

