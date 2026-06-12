---
title: "Fsck runs every boot?"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by movieman on 2010-10-26
So I just replaced the hard drive in my netbook with an SSD and did a fresh install of 10.10.

Does anyone know why it now wants to run fsck every freaking time it boots? And why, when it starts running fsck, it gets to about 40% and then the GDM screen comes up?

I don't know why it's running because it has been cleanly shut down and it's nowhere near the mount count to trigger an fsck; and it apparently never completes so it's just wasting time in any case. Which kind of defeats the point of putting a freaking SSD in there.

---

### Post by Herman on 2010-10-26
:) I suggest running a file system check on it yourself, either from the command line, or by right-clicking on the partition in GParted and choosing 'check'. Since it's a netbook, you probably have no optical disk drive, so you will need to do that from your Ubuntu installation Live USB I imagine. Never run a file system check on a partition while it's mounted.

---

### Post by movieman on 2010-10-26
Thanks, I do I have a USB DVD drive but I hadn't thought of booting from it to run fsck from there :).

I'm still confused as to why it never completes on boot, as then it would presumably fix whatever it's complaining about. And the disks it wants to check are apparently random, sometimes it's all three partitions, other times it's just one.

---

### Post by Herman on 2010-10-26
If it helps, you could make a list of all the possible causes you can imagine, and run through the list in your mind, thinking about which are more likely and which are less likely and then attack the most likely causes first.

You could divide the list into two broad categories, hardware problems and software problems.

Software problems may include the possibility that the file system really is dirty and actually does need a proper file system check. It could be that there's a problem the generic fsck isn't quite able to fix. Running a file system specific file system check manually might fix it, and if not at least it might give you valuable clues in the feedback it provides.
Since you say now that this is happening in more than one partition and at random, then there's a (remote) possibility that the kernel is failing to unmount these file systems cleanly on shutdown. That could mean there's a problem somewhere in your shutdown scripts, (something corrupted or misconfigured).
Another possibility that's not outside the realms of my imagination would be that something's corrupted or misconfigured in your startup scripts that's making the fsck program run un-necessarily and at random. 

Hardware problems could include anything from a flaky power supply or a bad connection at your new SSD drive power connector to loose or dirty sata connectors at the drive end or the motherboard end or a faulty sata cable. It's unlikely that your new ssd is faulty. but that also can happen sometimes, all factories make the occasional dud, and sometimes they manage to slip through quality control without being detected, that's what warranties are for. There might be some other faulty or overheating part somewhere else in your computer. 

You can probably think of more to add to both of those lists, but the next job is to use logic to try to pick out the most likely ones from the least likely, and sort from the easiest to fix to the more difficult.
Things like replacing the sata cable with a new one and making sure you have it plugged in properly are simple and only take a minute. Harder things, leave 'till later.
Then if the problem doesn't go away, you'll need to resort to running tests and experiments designed to find out which of the remaining problems it might be.

Usually, a proper file system check from the command line of another Ubuntu running from some other drive is a good place to start,is easy to do, and has been known to resolve issues like this many times in the past.
(Particularly when there's only one partition involved, although now you've said it's any or all of your partitions).  :)

EDIT: Oh, that's right, you said it's a netbook, so it's not likely a cable problem or connection problem, still, I'll leave that stuff there for the benefit of others who may read this thread in the future looking for ideas.

---

### Post by movieman on 2010-10-26
> **Herman said:**
> EDIT: Oh, that's right, you said it's a netbook, so it's not likely a cable problem or connection problem, still, I'll leave that stuff there for the benefit of others who may read this thread in the future looking for ideas.

Yeah, there is no SATA cable, the drive plugs directly into the SATA connector on the motherboard and is screwed down so it can't move. And given that taking the netbook apart and reassembling it took about an hour and a half I don't really want to open it up again to check :).

I'm guessing that perhaps something isn't unmounting the disk properly when shutting down, because I've found several people complaining about that on the web. I though perhaps the SSD might not be flushing its write cache, but apparently it doesn't have one beyond a few kilobytes to buffer a single write.

Plus I have the same type of SSD in the MythTV frontend and that doesn't seem to have this problem. But it's running 10.04.

I'll have to boot in verbose mode tonight and see what the OS is complaining about when it starts up.

---

### Post by movieman on 2010-10-26
So I could briefly see a message flash up on shutdown complaining about not unmounting some filesystem. Looking at the output on booting up with the splash screen disabled, it was checking /boot, which was configured as ext2: didn't seem any point making it journaled when it gets written to about once a month.

I changed /boot to ext3, and now it seems happy. Why, I have no idea.

---

### Post by Herman on 2010-10-27
That's strange, I wouldn't have thought of that as a possible problem. 
It's good if everything seems to be working properly now, for the time being at least. 
I hope it all keeps going well. :)

---

### Post by Herman on 2010-10-28
:) It's interesting that almost every web site author who writes about the need for a separate /boot partition also recommends the use of the ext2 file system for /boot.
I have never been able to understand the reason for that. I don't think file system journaling would slow down boot times, or at least not to an extent that can be measured. 
 Maybe the idea is to reduce file system overhead and save disk space in very small drives, such as when installing in a 4 GB USB flash memory stick or something like that, where every kb counts.

If the idea is to minimize file system overhead, and you take the time to examine the differences between various file systems you will see that as far as file system overhead goes, reiserfs actually takes up quite a lot less disk space than ext2. On that basis it seems to me the reiser file system is a much better choice for a separate /boot.
ReiserFS features 'tail packing' too, and that can save around 6% disk  space in the file system, at very little cost in speed, I certainly don't think you'll be able to measure any difference in your boot times. 
If you want  to pack your files into a smaller amount of disk space, delete the  'notail' option from your /etc/fstab line.
If you want maximum speed, just leave the 'notail' option as it is,  Reiserfs is up to 15 times faster than ext3 for small writes, and we can  easily turn off file system journaling in the ReiserFS too if we want,  simply by adding the mount option '*nolog*' to our /etc/fstab files.

I don't think it will make enough of a difference to warrant changing the file system if you already have ext3, but I now like ext4 even better than reiserfs for many reasons.
Personally I just use ext4 in my two SSDs, and several flash memory sticks and I haven't noticed any problems.
My boot times for Ubuntu Lucid Lynx in my OCZ Vertex are in the order of about 6 or 7 seconds, which is fast enough for me. 
If I took the time to unplug a few hard disk drives, I could probably reduce that to around 4 or 5 seconds, and if I make a special effort I could probably get it to boot in less than 4 seconds. I think 3.03 was my best boot time when I was trying, if I remember correctly. Oh, I found it, here's the URL for the boot chart from that, [http://members.iinet.net/~herman546/p1/ocz-lynx-lucid-20100430-18.png]("http://members.iinet.net/%7Eherman546/p1/ocz-lynx-lucid-20100430-18.png")  :)

---

