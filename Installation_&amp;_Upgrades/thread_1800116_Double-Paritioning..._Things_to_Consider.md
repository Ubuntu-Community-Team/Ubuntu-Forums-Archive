---
title: "Double-Paritioning... Things to Consider?"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by Valkyr333 on 2011-07-08
Hi, all...

I'm planning to add Ubuntu to the hard-drive of an older computer currently running MS Windows XP Professional. I'll eventually be phasing out Windows completely, but I'd like to be able to use Ubuntu on that computer in the meantime. I'm planning on clearing out all the old stuff in Windows that I don't use anymore in order to make room for Ubuntu before performing a true Double-Partitioning. My question is, what would you say I should include as basic parts of this process? I have in mind already that I'll be finding external storage to back up all the stuff I want to keep from Windows in the event that something went wrong, and that I'll need to calculate in advance the amount of space needed to keep my Windows partition running comfortably before I start installing Ubuntu. Is there anything else I should be considering? If so, what?

Thanks,

-Val

---

### Post by Blasphemist on 2011-07-08
Defrag windows within an inch of it's life. Then try to use windows disk management to shrink itself. You'll know how much you need to leave for it by knowing how much you are storing after your planned cleanup. You may get lucky and not need Linux to get this done.

I couldn't get win 7 to move certain files from the end of its partition no matter how much I defragged it. Because of that it couldn't shrink its partition sufficiently. I then turned to GParted, you can run this from a live Ubuntu CD or you can download a GParted iso. I used GParted to shrink the windows partition. In my case the extended partition that my original Ubuntu install created immediately followed the win 7 primary partition. I used GParted to expand the extended partition into the newly available space.

I then created the partitions I wanted in the available space in the extended partition, using GParted. I ended up with a bunch of partitions for Linux distro's and a swap for all of them to use at the end of the disk.

I then installed all of my new disto's and did manual partitioning where I chose to use the partitions I had created. I told each distro to use it's partition for the / (root) mount point, formatted that partition to ext4 and labeled the partition with the distro name for clarity.

I hope this is clear but ask if there are questions.

---

### Post by Bucky Ball on 2011-07-08
Only use Windows disk management to shrink the drive and yes, defrag several times. There is another one that is more thorough than the defrager that comes with Win but I can't remember the name of it ...

Dual-booting rather than double partitioning. My laptop has about nine partitions. Nontuplet-partitioning! I always use several partitions with Windows. ;)

---

### Post by oldfred on 2011-07-08
If you have XP, it does not have any tools to shrink its partition built in. Defragging will speed up the process. You can use gparted but want to leave about 30% free space in the NTFS partition for windows to work well. At 10% free it just about stops working.

If you are going to use XP & Ubuntu for a while it is best to create another NTFS "shared" partition for all data you may want in both systems. Then you do not have to write from Ubuntu into the XP partition. Windows often does not like excessive writing from a foreign system. Shared partition can also be inside the extended as a logical as windows will read it just fine. Only the first windows install has to be a primary partition to allow windows to boot.

---

### Post by Valkyr333 on 2011-07-14
@Blasphemist - Gparted looks complicated. If it offers the best chance of success, that'll be what I'll do. Just so I'm prepared, though, is it any more straightforward than it looks by the image? Or, is it just a matter of being familiar with the terminology?

Excellent username, btw. =)

@Bucky Ball - I'm not sure what you mean by "partition several times."? The way I understand partitioning, it just means creating a separate space to be occupied by another OS.

@Oldfred - Thanks, I'll keep that in mind. I'm planning on only making the Windows partition big enough to house the basic things that make it work fluently and the few programs I use whose operation requires Windows, but I imagine the percentages of space needed for safe use still stay the same.

---

### Post by Bucky Ball on 2011-07-14
> **Valkyr333 said:**
> 
@Bucky Ball - I'm not sure what you mean by "partition several times."? 

Sorry, my mistake. I meant 'defrag several times'. The more thorough defrager is Power Defragmenter:

[http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml)

That will crunch things better than the default Win defragmenter.

---

### Post by Blasphemist on 2011-07-14
GParted is really quite straightforward but yes, you do need to get the terminology figured out for it to turn on the light bulb if you know what I mean. Look at your system in GParted and read the sequence of what I did. I promise, the light bulb will come on.

---

### Post by Valkyr333 on 2011-07-16
Okay, thanks. =) I'll take that all into account when the time comes to make this partitioning thing happen. If it works out, I'll mark the thread as "Solved." If not, I'll ask questions.

All the be(a)st. \m/

---

### Post by dino99 on 2011-07-16
install guide

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

