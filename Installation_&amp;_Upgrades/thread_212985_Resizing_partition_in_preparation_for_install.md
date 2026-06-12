---
title: "Resizing partition in preparation for install"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by mssever on 2006-07-10
After installing Ubuntu on my desktop and loving it, I want to dual boot my laptop with WinXP and Dapper. My problem is that Windows has scattered files all over my disk, leaving most of my free space in the middle of the disk. The old Win95 defrag would move everything to the beginning of the disk, but not so with the XP defrag. Are there any tools that I can use to move the files? Otherwise, I'll be stuck with an intolerably small Linux installation.

---

### Post by john_spiral on 2006-07-10
you will need to boot from a CD or floppy to run a partition tool like gnu parted or straight parted from a floppy.

---

### Post by mssever on 2006-07-10
Two questions:
1. Is GParted (as provided on the install CD) equivalent to GNU parted and regular parted?
2. Is parted actually capable of moving files on NTFS filesystems? I thought it could only resize partitions.

---

### Post by john_spiral on 2006-07-10
looks like gparted is good for NTFS filesystems:

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

I think GParted & GNU parted are one and the same?

---

### Post by mssever on 2006-07-10
My guess is that GParted is the GTK+ frontend for GNU Parted. I know it's GTK. Given the large number of people in this forum who talk about dual booting, I'm sure it does support resizing NTFS partitions, given that NTFS is the default filesystem for Windows XP.

However, the question I have is not about merely resizing partitions, but actually moving the files on my partition so that I am able to utilize my free space. I have ~30 GB free on my disk, but since there are some files in the last quarter (approx.) of my drive, I doubt if I could get more than 10GB for Linux by resizing my NTFS partition.

Once my backup completes, I'll try GParted to see if it can acutally move files, but unless it is significantly different from the tools I used several years ago, I doubt if it will be successful.

---

### Post by john_spiral on 2006-07-11
Moving files from one ntfs partition to another ntfs partion/drive is best done within windows.

---

### Post by mssever on 2006-07-11
I'm not tryig to move files between partitions. I'm trying to move them on the *same* partition, in order to free up enough space at the *end* of the partition so that I can resize it. I only have one partition right now.

---

### Post by Malac on 2006-07-11
You could try booting into safe mode in Windows and running defrag from there. This should mean most programs accessing the data will not be runnning and files should be moved.
When I installed Ubuntu for the first time I had to defrag my drive 3 times rebooting in between each to get the files to go where I wanted them.

Hope this helps.

---

### Post by mssever on 2006-07-11
Thanks for the suggestion, Malac. I'm trying it right now. I'll post the results.

---

### Post by Herman on 2006-07-12
When I used to use Windows, I found it needed hours of repeated runs of Windows defrag utility sometimes. The partitioner in the 'Alternate CD' might refuse to do anything if Windows needs defragging first.
I found the following linked how-to excellent advice on defragging Windows, [http://www.geekgirls.com/windows_defrag.htm](http://www.geekgirls.com/windows_defrag.htm)  , especially the bottom part titled 'Step-by-step: Efficient defragging'.Step-by-step: Efficient defragging.

I believe GParted, either in the 'Desktop' Live/Install CD or on a standalone GParted LiveCD, will defrag Windows quite safely and a whole lot faster than Windows own utility. I think it does so automatically, the user doesn't need to tell it to. But it's up to you of course. 
Regards, Herman

---

### Post by mssever on 2006-07-12
Herman, thanks for the link.

I defragged many times in safe mode to no avail. The XP defragmenter simply doesn't work like the Win95/98 defragmenter. So I booted the Live CD, thinking that I'd try to make do with what I could. At the partitioning screen, the installer by default offered to resize the partition in a way that I knew would give Linux more space than was available. I clicked the forward button to see if the partitioner would check the situation more thouroughly. Every other disk partitioner I have ever used has required some form of user confirmation before actually making changes to the disk, but not this one. It immediately resized the disk without a single confirmation dialog.

I consider this to be a critical bug because none of the documentation I was able to find mentioned that the partitioner was able to move files in the process of resizing. Earlier partioners that I've used would refuse to continue in such a situation. This issue is compounded by the fact that NTFS support in Linux is considered experimental. Therefore I didn't want to trust the partitioner with writing files on an NTFS system. I haven't booted windows yet to try to determine if I've actualy lost data (I probably haven't). But there needs to be some sort of confirmation that clicking OK or Forward will result in the partition table being changed and isn't undoable. (Technically, it is, I guess, but it's more complicated than merely hitting the back button.)

---

