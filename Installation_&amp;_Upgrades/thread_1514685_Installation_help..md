---
title: "Installation help."
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by jordanlowe on 2010-06-21
After a good few months of using WUBI, I'm finally ready to make the jump to fully installing ubuntu. I've made a backup, and have a disc ready with the ISO on it, but I get slightly confused when it comes to partitioning.

I see that there is an option to install Ubuntu and Windows side by side, which is what I want really, but I'm worried in case I do something wrong and make the Windows side of things un-bootable and unusable. 

As I have an iPhone, I still have to use Windows to sync it with iTunes, and I also have various programs like Photoshop that I still need to use.

It would also be useful if I could access files from Windows from Ubuntu, which I have been doing in WUBI. Can someone help me out please? Do I have to make a seperate partition in windows, using the liveCD etc, or do I simply just need to load up the live CD, and hit "Install side by side"?

Many Thanks!

---

### Post by darkod on 2010-06-21
The side-by-side option is a bit misleading. What version of windows do you have?

For vista and 7, it's best to make a plan how much space you want to allocated to ubuntu, and shrink the windows partition first, to make that space.

1. First uninstall wubi, because it will free the space used for it.

2. If you need to shrink the windows partition, in vista or 7 use Disk Management to do it. Boot windows few times after that to do its disk checks. Unfortunately in XP Disk Management doesn't have the tool to shrink.

3. After you have created unallocated space with the shrink, leave it as such. Don't create partition(s) for ubuntu in windows, it doesn't work on ntfs anyway. Boot with the ubuntu cd and in the installer either use Use Largest Available Free space for an automated option, or use Manual Partitioning to create your own partitions. If you want separate /home which is advised, you have to use Manual Partitioning.

If you have questions, just ask. It's better to ask in advance. :)

---

### Post by jordanlowe on 2010-06-21
> **darkod said:**
> The side-by-side option is a bit misleading. What version of windows do you have?

For vista and 7, it's best to make a plan how much space you want to allocated to ubuntu, and shrink the windows partition first, to make that space.

1. First uninstall wubi, because it will free the space used for it.

2. If you need to shrink the windows partition, in vista or 7 use Disk Management to do it. Boot windows few times after that to do its disk checks. Unfortunately in XP Disk Management doesn't have the tool to shrink.

3. After you have created unallocated space with the shrink, leave it as such. Don't create partition(s) for ubuntu in windows, it doesn't work on ntfs anyway. Boot with the ubuntu cd and in the installer either use Use Largest Available Free space for an automated option, or use Manual Partitioning to create your own partitions. If you want separate /home which is advised, you have to use Manual Partitioning.

If you have questions, just ask. It's better to ask in advance. :)


Ahhh right! Thanks for clearing that up a bit! I'm using Windows 7, but when I try to shrink my partition, I am unable to shrink any MB, which is odd because I have around 120 GB free. After googling this, I learnt it was because of certain files that can't be moved and that defragmenting my Hard Drive would fix this. It didn't :( However, I noticed that I can shrink my Windows partition while in a Live CD session on Ubuntu, but I doubt this is wise seeming I can't do this already in Win7 :( I'd really appreciate some more help if you could! Thanks! :)


EDIT: Also, what is the benefit of (and, well, *what is*)a seperate /home? :)

---

### Post by darkod on 2010-06-21
I'll start from the second question. In linux every user will have its own Home folder, similar to My Documents, where you keep your personal files and also some programs put settings there that relate only to that user.
If you make the standard, minimum install of / + swap partitions, then the Home folders will be just a folder in /, in other words the location is /home as linux marks it.
However, if you create separate partition during the install, and set the mount point as /home, then from inside ubuntu it all looks the same, but in fact all user personal data and settings are on that separate partition.
So, at any time you can decide to do a clean install of ubuntu into the same / partition and format it, but your personal data is safe in /home. However, during the new install you still have to specify that you are using this separate /home but do NOT tick the format box.

Did it make sense?

If using separate /home, because most data will be there, for the / partition 10-15GB is plenty enough. Give it 20GB if you can spare it. The rest can go to swap, and all the rest to /home.
Swap can be as small as 2GB, but if you plan to hibernate regularly a size of 1.5 x RAM size is recommended. The rest remains for /home.

Yes, windows can be idiotic when shrinking. I suggest to search more for tutorials about shrinking win7 when it doesn't allow you to shrink much.

Another thing I have heard, but never needed to try it, is that disabling the restore option temporarily can allow it to resize. It seems the restore function is the one holding data at the end of the partition. But I have also read disabling the function deletes all current restore points, so think whether you need any of them (not likely).

But I'm not too experienced with this, so search and read more about it.

Using Gparted from live mode is the last resort. It can move the data when resizing but the big question is whether win7 will like that.

---

### Post by jordanlowe on 2010-06-21
> **darkod said:**
> I'll start from the second question. In linux every user will have its own Home folder, similar to My Documents, where you keep your personal files and also some programs put settings there that relate only to that user.
If you make the standard, minimum install of / + swap partitions, then the Home folders will be just a folder in /, in other words the location is /home as linux marks it.
However, if you create separate partition during the install, and set the mount point as /home, then from inside ubuntu it all looks the same, but in fact all user personal data and settings are on that separate partition.
So, at any time you can decide to do a clean install of ubuntu into the same / partition and format it, but your personal data is safe in /home. However, during the new install you still have to specify that you are using this separate /home but do NOT tick the format box.

Did it make sense?

If using separate /home, because most data will be there, for the / partition 10-15GB is plenty enough. Give it 20GB if you can spare it. The rest can go to swap, and all the rest to /home.
Swap can be as small as 2GB, but if you plan to hibernate regularly a size of 1.5 x RAM size is recommended. The rest remains for /home.

Yes, windows can be idiotic when shrinking. I suggest to search more for tutorials about shrinking win7 when it doesn't allow you to shrink much.

Another thing I have heard, but never needed to try it, is that disabling the restore option temporarily can allow it to resize. It seems the restore function is the one holding data at the end of the partition. But I have also read disabling the function deletes all current restore points, so think whether you need any of them (not likely).

But I'm not too experienced with this, so search and read more about it.

Using Gparted from live mode is the last resort. It can move the data when resizing but the big question is whether win7 will like that.

Ahh of course. I heard about the restore point thing. I'll give that a try. If not, i'll just give Gparted a try instead. Thanks again! :)

---

