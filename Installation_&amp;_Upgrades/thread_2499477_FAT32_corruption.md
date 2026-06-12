---
title: "FAT32 corruption"
date: 2024-07-29
forum: Installation &amp; Upgrades
---

### Post by zanetto on 2024-07-29
i use win 10 and ubuntu dual boot system.
I have a fat32 partition and I use it with both operating systems
Sometimes I lost files

how can I do?
Thank You

---

### Post by Paddy Landau on 2024-07-29
There's little context in your post, so it's hard to diagnose your problem.

What do you use the FAT32 partition for? Is it for sharing data, or do you store your home folder there, or do is that where you installed Ubuntu?

If it's for sharing data, can you reformat it to NTFS? (Please **backup your data** before doing this!) NTFS is more resilient than FAT32, and can hold larger files.

Do Windows or Ubuntu ever crash, and you have to do a hard power-down?

---

### Post by zanetto on 2024-07-29
I use the partition for data
For example I modify an image with windows in FAT32 partition, then when I reboot to linux, the image is corrupted

---

### Post by Paddy Landau on 2024-07-29
> **zanetto said:**
> For example I modify an image with windows in FAT32 partition, then when I reboot to linux, the image is corrupted
I don't know why it's doing that. Use the Windows tool to check the partition for errors. It might find something.

But, if you can instead reformat to NTFS, you'll likely have a much better time. NTFS is more resilient and reliable.

---

### Post by zanetto on 2024-07-29
does NTFS work with ubuntu?

---

### Post by Paddy Landau on 2024-07-29
> **zanetto said:**
> does NTFS work with ubuntu?
Absolutely, yes. Linux (not just Ubuntu) has had full support for NTFS for a long time.

---

### Post by Holger_Gehrke on 2024-07-29
The one thing missing from the support for NTFS in Linux is a program to repair the file system if it develops problem. There is no 'fsck' (**F**ile **S**ystem **C**hec**K**) for NTFS while there is one for most file systems Linux supports including FAT - fsck.fat exists and is quite complete. So NTFS should be avoided unless you're dual booting or have a second machine running Windows at hand so you can run 'chkdsk' on a file system when needed.

Newer versions of windows are known for not cleaning up file systems when they shut down because they don't actually shut down at all but do a kind of partial hibernation instead. There are ways to stop this behaviour but since I haven't used Windows since version 7 I haven't bothered to memorize them ...

Holger

---

### Post by Paddy Landau on 2024-07-29
> **Holger_Gehrke said:**
> The one thing missing from the support for NTFS in Linux is a program to repair the file system if it develops problem.
That is a good point. The OP has Windows, fortunately.
> **Holger_Gehrke said:**
> Newer versions of windows are known for not cleaning up file systems when they shut down because they don't actually shut down at all but do a kind of partial hibernation instead. There are ways to stop this behaviour but since I haven't used Windows since version 7 I haven't bothered to memorize them ...
I forgot about that! My notes for how to disable fast boot are out of date; they don't work for Windows 11.

---

### Post by TheFu on 2024-07-29
There is a kernel driver bug for some versions of the NTFS-3g driver when used in some ways.  I think it only impacts kernel 6.8.x, but I don't know.

FAT32 is the worst choice for sharing data on any type of storage and should be avoided unless there's no other choice. 

For SSDs and HDDs that much be accessible through a physical connection with an MS-Windows computer, then NTFS is the best option.  NTFS is journaled, which is a good thing for storage almost always.

For cheap flash storage, like a USB flash drive or SDHC/MicroSD cards, use exFAT which corrects limitations of FAT32, but is not journaled.  Journaling does use more writes to provide lots of extra data safety, but if the media only allows 1000 writes per cell before failure, it is usually better to use non-journaled file systems like exFAT or for Linux-only use, choose f2fs.  f2fs is specifically designed for flash storage and Linux with support for all the expected POSIX standards. It is also freely released without patents. The performance of f2fs compares well with other file systems as well, unlike exFAT and FAT32.

I use NTFS for 1 specific need.  A hardware video recorder only supports FAT32 or NTFS, so I choose NTFS.  About once a month, the NTFS file system becomes corrupted.  I think the NTFS implementation in the video recorder device (it doesn't have any OS) is substandard. When I first got the device, I used FAT32 and had dumb limitations like files are limited to sizes of 2GB and a partition over 64G cannot be used.  FAT32 was created in the 1990s and the limitations show that age which the replacement file system, exFAT completely remove.

But for HDD and SSD storage that must be shared with MS-Windows, choose NTFS.

---

### Post by zanetto on 2024-07-29
in win 10 I disabled fastboot
I turned off nv cache feature 
I still have the problem

---

### Post by Paddy Landau on 2024-07-29
> **zanetto said:**
> in win 10 I disabled fastboot
I turned off nv cache feature 
I still have the problem
Unfortunately, I don't know why.

If you can reformat as NTFS, I advise that you do so.

EDIT: Which version of Ubuntu do you have?

---

### Post by yancek on 2024-07-29
Did you boot into windows and run chkdsk to see if the device partition had problems.  Are you referring to photos when you say images?  If so, what specifically do you mean by corrupted when you boot into Ubuntu?

---

