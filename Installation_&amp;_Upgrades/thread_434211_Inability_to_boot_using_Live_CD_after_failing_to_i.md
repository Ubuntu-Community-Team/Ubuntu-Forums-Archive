---
title: "Inability to boot using Live CD after failing to install to HD"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Jugalator on 2007-05-05
OK, so here's my story, I'll try to condense it. :)

Long story short, my first impression with Ubuntu 7.04 is not great. :(

**Hardware:** I'm on a system with two hard drives; one 500 GB Samsung HD (mounts as 'sda') and one 160 GB Maxtor HD (mounts as 'sdb'). I have Vista installed on sda. I'm intending to install Ubuntu 7.04 on sdb.

Here's the **sequence of events**:

1. Boot up Ubuntu from the "Live CD" (actually using a DVD image of it because I had to use a DVD drive) using the standard "Start or install Ubuntu" option.

2. Everything works fine if I switch from VGA mode to something else. Apparently, a Geforce 8800 doesn't like Ubuntu-loader style VGA mode for some reason. It "should" support it though as it's a standard graphics mode, so it was a little strange.

3. OK, I'm now in the Ubuntu desktop, so I pick to Install Ubuntu to sdb by picking the appropriate "install on drive" option. It starts working for a while, and then fails with some sort of sdb mounting failure, or something of that order. (I fail to recall the exact message -- was it perhaps because sdb was already mounted? But shouldn't it in that case try to unmount if I install to the drive? Or maybe not? Hmm)

4. I'm forced to go back to the Partition Manager or "continue". Since continue was the scary option with a failure at hand, I chose to go back. Now all partitions seemed to start being detected really slowly. :/

5. I say to myself to stop waiting for all that and just boot into Vista that detects my partitions, including that semi-installed crapped out Ext3 partition in an instant, in comparison. I delete both (normal + swap) partitions on 'sdb' and start up Ubuntu again.

6. Now the Ubuntu loader starts giving me errors like this:
```
ata4.00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
(BMDMA stat 0x24)
cmd c8/00:08:40 ... <and a lot more text>
<... and, after a while ...>
Buffer I/O error on device sdb, logical block 8
Buffer I/O error on device sdb, logical block 9
Buffer I/O error on device sdb, logical block 10
Buffer I/O error on device sdb, logical block 11
Buffer I/O error on device sdb, logical block 12
```
And repeat, until I get bored and press Reset.

7. I thought maybe Ubuntu Live CD for some reason didn't like a hard drive with not even any partitions, so I create and format (skip Quick Format to be sure) the full physical sdb hard drive with a NTFS file system, i.e. pretty much like it was set up to be in the beginning.

8. I reboot with the Ubuntu Live CD and get identical errors like in step 6 above...

9. I have no clue of what's going on and why the start script even cares so much to have 'sdb' properly formatted and partitioned, much less what's *causing* the errors, because this 'sdb' drive is now working perfectly fine in Vista, along with 'sda' and everything else.

Where do I go after this, specifically, is there a way to make Linux "happy" about the sdb drive, whatever is going wrong that Windows doesn't detect as an error? Is it something with the partition table that Linux feels is very very bad? I have no idea and it's everything but user friendly at this point. :confused: At this point, I can't even boot Ubuntu from the CD anymore because those errors just pop up until I get fed up. :(

---

### Post by Jugalator on 2007-05-05
Hmm, I actually got through all those error messages while booting Ubuntu after 5+ minutes of waiting, and got into the desktop. So I tried to install Ubuntu again on my second drive, but ended up with the submitted error message about not being able to create the file system. :(

Can't Ubuntu just wipe the drive properly first, or what's the problem? I don't really see it -- the drive is physically working, I had ~100 GB of files installed on it earlier today before moving them to the other drive, and I can even create a functional NTFS partition on it as I tried just hours ago, but I just can't seem to install Ubuntu on that drive, and hardly even boot Ubuntu because of it (see above).

Edit: Btw, before I started doing this, the former files on that drive could also be successfully read by Ubuntu, and it didn't complain about all this in the first place while booting. So it's like some sort of "garbage" left on the drive that prevents the installer from working, perhaps from the first failed install in the post above, and gives a lot of errors during Ubuntu Live CD boot up. :confused:

---

### Post by Jugalator on 2007-05-07
Hmm, I've now additionally tried to run GPartEd, but it halts at "Scanning all devices..." after a short while, presumably when it starts trying to work on sdb. I've tried running 'sudo fsck /dev/sdb' but it halts, likewise. No error messages in either case.

Is there any way to somehow restore this drive into an order that is workable in Linux? Again, Windows Vista reads it fine as the NTFS formatted drive it is, but it's all empty (intended as it was just a test format) and I really don't care if the data would be wiped. I just wonder how I can at all restore this drive into an order that doesn't cause Ubuntu to lock up on it, and that I can later use gparted to create new partitions for. All I want is to install Ubuntu on this very ordinary Maxtor 160 GB drive. :-p

I also get lots of kernel messages about I/O errors in the System Log, so because I know for a fact there's no physical problem here, there must be something in here that confuse the heck out of Linux...? I'm not even sure sdb could be mounted -- it's that bad.

---

