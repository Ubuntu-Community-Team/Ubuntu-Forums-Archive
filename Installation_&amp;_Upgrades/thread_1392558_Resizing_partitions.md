---
title: "Resizing partitions"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Brett.Townsend on 2010-01-28
Hi, I setup my new laptop the other day to dual boot windows 7 x64 and ubuntu 9.04 x64 and when I did I gave ubuntu 50gb thinking eh I shouldn't need more than that. However after transfering my music collection to the new laptop and a few other things I realized wow i'm almost out of space on my partitions for nix! Bone head move on my part I rarely ever boot into 7 but would still like to keep it around. I would really like to resize the windows partition without deleting it any help would be greatly appreciated.

Thanks in advance.

---

### Post by darkod on 2010-01-28
Win7 Disk Management has option for resize. Windows button + R, type diskmgmt.msc, hit Enter.
After the resize boot win7 few times to allow disk checks and to make sure it's OK after the resize. BACK UP ANYTHING IMPORTANT BEFORE THE RESIZE.

Then you need to decide whether you want to use the unallocated space as separate ext4 partition or expand root partition. I'm no expert in that.
You can also have ntfs partition created in that space and both ubuntu and win7 can use it. That said, it's not necessary to shrink win7 partition, any data on it can be accessed from ubuntu but I try to avoid accessing the windows system partition regularly.
I would rather have separate ntfs partition that both OSs can use.

---

### Post by Brett.Townsend on 2010-01-28
Yeah, I thought about that I was just wondering if it could be done without booting into windows. Maybe i'll just get rid of windows altogether, I have only booted into windows once since I got the laptop. Who knows what I was thinking when I  setup my partitions. I guess I was treating it like my gaming computer and thought oh i'll leave extra space for my games...

Thanks for the inspiration.

---

### Post by darkod on 2010-01-28
You could do it with Gparted, from ubuntu. To be honest, I like Gparted much more. But some people prefer resizing vista and 7 with the built in tool (XP doesn't have it anyway). I have resized vista with Gparted and it worked fine, but that was actually Gparted LiveCD, not the one in ubuntu.
There some bug mentioned for ubuntu Gparted if resizing vista/7.

---

### Post by tommcd on 2010-01-28
If you plan to shrink Windows 7, then I would use the Windows 7 disk management utility as Darkod said. Then to expand Ubuntu into the newly created unallocated free space, you can use a Parted Magic live CD:
[http://partedmagic.com/](http://partedmagic.com/)
I use Parted Magic for partitioning tasks and it works very well. There is also GParted on the Ubuntu live CD.
If you delete Windows 7, you can do that easily from Parted Magic or GParted. Then you can make a separate /home partition for Ubuntu out of the unallocated space left after deleting Windows 7. Just format the space as ext3 or ext4 using GParted or Parted Magic, then to make it your /home directory follow this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Or you could just grow your current Ubuntu partition into that space and have one big partition for Ubuntu. Note that resizing partitions can take a few hours, so do it when you will not be using the computer.

---

### Post by Brett.Townsend on 2010-01-28
Yeah, I think i'm going to just delete the windows 7 partition and expand the nix partition for lots of space. Will have to get that started when I go home for lunch as i'm at work right now, Yay for working at the helpdesk. lol

---

