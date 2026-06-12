---
title: "Unable to shrink Windows partition. Gparted error"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by bobnutfield on 2010-06-15
Hello Everyone,

I am trying to resize a 40GB drive with Windows XP on it to install Xbuntu.
I have done this dozens of times and have never encountered an error.  However, this time I am getting:

> ERROR: Extended record needed (1064 > 1024) not yet supported
              Plese try to free less space

I tried several different sizes.  The partition is currently 45.57GB with Windows having used up 20.21GB.  I wanted to shrink it to 23.0GB and give Xbuntu the rest.  But it continues to get this error.

Anyone know what this error means?  Google comes up with zilch for me.

Any help appreciated.

---

### Post by stumay on 2010-06-15
It won't work, you have too little space on 40GB.
 
Buy another Hardrive

---

### Post by bobnutfield on 2010-06-15
> **stumay said:**
> It won't work, you have too little space on 40GB.
 
Buy another Hardrive

Well, you may certainly be correct that it won't work, but I have done this before on a 40GB drive, giving Windows 25GB and 15GB for linux.  Of course, there is no swap partition, but it has worked for me before.  I am more interested in what this error is telling me exactly.

---

### Post by linux-hack on 2010-06-15
try the fsck command to see if your hdd has some bad sectors 

or try doing it in the command line and not with gparted but with fdisk (old but good)

---

### Post by bobnutfield on 2010-06-15
Thanks, I was suspecting bad sectors as the possible cause, but I am hesitant to run fsck on an NTFS partition.  This is a friends laptop who I have been trying to introduce to Linux and I don't want to bork his Windows installation.  If he could get on with Linux, he would eventually just run Linux, but he wants to keep Windows for now, so I thought a dual boot would be a solution.

---

### Post by ajgreeny on 2010-06-15
I think the problem is the 20.21GB used by windows.  In order for things like defrag to work at all, windows really needs about 20 -25 % free space compared with that already used, so will not allow a partition to be shrunk smaller than that used space + the 25%.  You may also find that the windows virtual memory, which by default is set by the system, but can be disabled before a defrag to improve things, is stopping the shrinking happening.

Either way, I think the answer is to get another hard disk.  You could then use that as a data partition/disk, formatted as ntfs, shared by both OSs, and just have the OS system files for both windows and Ubuntu, and if you want to, a separate /home partition for Ubuntu on the first disk.  Just make sure all your Ubuntu applications save their files to the second disk, not to /home, on the first.  With all your data files gone from the first disk there should now be more room available, which ought to allow you to defrag a couple of times and then hopefully shrink the windows partition more than you so far have been able.

---

### Post by bobnutfield on 2010-06-15
Thanks, your idea is a good one, but this is a laptop.  Only one hard disk.  I believe that on this occassion I am not going to be able to help him unless he wants to ditch windows altogether on this drive.  It is an old laptop with only 1GB memory.  If he doesn't want to get rid of windows, it's probably best to let this thing just die as it is doing now.  Windows is so corrupted on this laptop it takes at least 4 minutes to get to a desktop on boot.

---

### Post by rob45 on 2010-06-15
Hi...dont know if this will help ,but if all your problems are due to space,why not free up some by transfering stuff like pics/music and such to either saving to cd or ssdcard,most mobiles and dongles have ssd cards and there not expensive to buy and cd"s are dirt cheap.

---

