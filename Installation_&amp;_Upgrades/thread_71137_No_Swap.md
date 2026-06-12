---
title: "No Swap"
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by cavaughan on 2005-10-02
Been using Ubuntu Hoary for a while now and have been frustrated whenever the system drags to a near halt. Last night, I suddenly realized, I don't think I have a swap. Looking at other linux boxes, if I do a top command I will see that for the swap there is so much memory available, so much being used, etc. But on my Ubuntu box everything is zero except the catagory "cached". So I looked at /etc/fstab and saw:

/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0

So there is a swap partition apparently. So then I did an fdisk and listed the partitions:

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18617     9382936+  83  Linux
/dev/hda2           18618       19485      437472    f  W95 Ext'd (LBA)
/dev/hda5           18618       19485      437440+  82  Linux swap / Solaris

WHAT? What is this /dev/hda2 partition? And while is it occupying the same cylinders? I tried deleting this partition and then reassigned the swap to /dev/hda2 made the changes to the fstab to reflect that and rebooted. But everything returned to the previous status. That is, through fdisk the partitions remained as above. And fstab was now pointing the swap to /dev/hda2. Still top showed basically the same information as before. 

What can I do to recreate a swap?

Curtis

---

### Post by odin on 2005-10-02
well the thing I see(if I'm wrong please tell me or if you dont understand a word of what I say I'll try to point you somewhere so you understand it better) is that /dev/hda2 is an extended partition which can be composed by several logical partitions.That's why your swap partition was in /dev/hda5 cause the partitions from hd?1 to hd?4 are for primary partitions.When one of those primary partitions is extended then every logical partition in it is named from hd?5.The reason why your hda2 and hda5 were in the same cilynders was because they actually were in the same place cause in a way they were the same.All this is useful if you need to have lot of partitions(for the diferent directories of your ubuntu for example) cause if all your partitions are primary you can only have four.

How do you solve this problem?I actually cannot tell you much more because I dont want to make the problem bigger.But sometimes knowing what the problem was it's easier to find a solution.

If you could post the output of this command "fdisk -l " then I can see how your partition table is right now and if i can help you.

---

### Post by cavaughan on 2005-10-02
On my Ubuntu box fdisk -l gave:

Disk /dev/hda: 10.0 GB, 10056130560 bytes
16 heads, 63 sectors/track, 19485 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18617     9382936+  83  Linux
/dev/hda2           18618       19485      437472    f  W95 Ext'd (LBA)
/dev/hda5           18618       19485      437440+  82  Linux swap / Solaris


However, I realized that when I used fdisk to try to remove hda2 and hda5 and make hda2 the swap, that I didn't issue the write command. So this time I did that, rewrote /etc/fstab to reflect the change and rebooted.

Now fdisk -l reads:

Disk /dev/hda: 10.0 GB, 10056130560 bytes
16 heads, 63 sectors/track, 19485 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18617     9382936+  83  Linux
/dev/hda2           18618       19485      437472   82  Linux swap / Solaris

So, it looks good. BUT! Nonetheless, top reads:

Swap:        0k total,        0k used,        0k free,    67392k cached

So, what have I still failed to do?

Curtis

---

### Post by odin on 2005-10-03
well as I told you your partiton table was fine before and it looks fine now so either I dont understand your question or I dont know the answer.... :D

what is it that makes you say that something is wrong? Please tell me because I also would like to know a bit more about this.

---

### Post by cavaughan on 2005-10-03
Ok, from the start....
I noticed that when I had many applications open at once my HD would be going crazy. Everything pretty much came to a halt. The only time I have heard such activity before was when the swap was full and the computer was caching to the primary partition (as there was insufficient swap). So I went and used top to see how the swap was. And I saw that there was 0 swap. Looking at the way the HD had been partitioned I thought that the problem lay there and that I just needed to put the swap on hda2 and everything would be OK. But despite that as you will see below, there is 0 bytes in the swap. So, apparently the swap is not being mounted, I think. How do I correct this situation.

Here is my top output:

top - 11:39:22 up 32 min,  2 users,  load average: 0.45, 0.41, 0.34
Tasks:  89 total,   1 running,  87 sleeping,   0 stopped,   1 zombie
Cpu(s):  9.6% us,  2.0% sy,  0.0% ni, 88.4% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    256728k total,   235600k used,    21128k free,     4916k buffers
Swap:        0k total,        0k used,        0k free,    60652k cached

---

### Post by cavaughan on 2005-10-04
Turns out that the answer is:


If "swapon -s" doesn't show any swap being used, I'd try:

mkswap /dev/hda5
swapon -a

---

### Post by odin on 2005-10-04
glad you found the soultion and thank's for sharing it,i didnt know about this....There's still many many many things to learn when I though it was only many....

---

