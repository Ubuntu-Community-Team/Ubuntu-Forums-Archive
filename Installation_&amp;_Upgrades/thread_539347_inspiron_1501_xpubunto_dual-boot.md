---
title: "inspiron 1501 xp/ubunto dual-boot"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by 8ballkrnrpkt on 2007-08-31
First off, I'm very new to Ubuntu and trying to set up dual booting so i really have no idea what i'm doing.  I currently have xp installed on 60gb of my 120gb hard drive and am trying to get ubuntu installed as a dual boot.  I was trying to follow the guide at [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) 
I originally had the hard drive partitioned as:
1.  60gb ntfs (for xp)
2.  30gb ext2 (for ubuntu)
3.  extended
4.  4gb linux-swap
5.  (the rest) fat32

I have the ubuntu-6.06.1-desktop-amd64.iso (laptop has amd 64 athlon x2) burned to a disc and went into the "run or install ubuntu."  It booted up fine and a clicked the "install" that shows up on the desktop.  I selected the language/timezone/keybaord layout and filled in the name and login stuff but at step 5 (Select a disk) it just sits there thinking forever until I hit cancel and quit the setup.

I've tried going through the install with the hd partitioned as 60gb nfts and the rest unpartitioned and I have the same problem.  I have no idea what I can do to fix this.  Any ideas?

Thanks in advance,
-Andy

---

### Post by ajgreeny on 2007-08-31
A few points worth making.

1  Your 30GB ext2 would be better as ext3 which is the default for ubuntu, and better than ext2.

2  You are most unlikely to need 4GB of swap.  Perhaps you have 2 GB ram and have read that swap should be twice the size of that, but this really relates to times gone by when ram was expensive and no one had more than about 256MB.  You can probably safely reduce your swap size to 2 or even down to 1GB, unless you know you will definitely need huge amounts of ram and/or swap.

3  The extended partition is usually just there to act a partition to contain the swap.

3  The remaining fat32 is a good idea for using as data storage for both systems, though bear in mind that linux can now read/write ntfs, though ntfs can not do the same the other way.

4  Finally, I think it would be easier for you as a linux newcomer to use the 32 bit version of ubuntu rather than the 64 bit version, even though your machine can run the 64 bit.  There are some utilities and browser plugins that will be much easier in the 32 bit version, and are not even available as 64 bit.  You can get something working, using wine I think, but for most people it is not worth the trouble.

Have a good look at [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) which is a super guide to installing ubuntu with XP as a dual boot.

---

