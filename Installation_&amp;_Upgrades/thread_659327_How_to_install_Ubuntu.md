---
title: "How to install Ubuntu?"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by FastMady123 on 2008-01-05
I want to keep Windows XP but don't want to nuke it. I need to partition my hard disk and this may nuke Windows XP. Can I use GParted or Ubuntu will partition my hard disk?

---

### Post by taurus on 2008-01-05
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

p.s.  _Always_ back up your important files first before you try to resize your harddrive.

---

### Post by sub2007 on 2008-01-05
I must say I was very scared of partitioning, it was the only thing that kept me away from Linux for so long. I didn't experience any data loss at all when I shrunk the Windows NTFS partition and installed Ubuntu but it's always a possibility. In order to minimise the possiblilty of data loss I do the following:

1. make a backup of any important files
2. defragment the NTFS volume - I use Diskeeper Lite ([http://www.majorgeeks.com/download.php?det=1207](http://www.majorgeeks.com/download.php?det=1207)) which is better than the Windows XP defragmenter (the XP defragmenter is a stripped down version of Diskeeper Lite). I usually run it a few times - the aim is to try and chunk as much of the blocks into the beginning of the disk and have a large white section and so I run it until I'm convinced that I can get no more white space. If you haven't partitioned in a while then it will take more runs. One run is probably sufficient but I like to know that I have done the best I could have done before risking partitioning - as I mentioned I was scared of losing data when I partitioned my drive.
3. having finished defragmenting, I run a full chkdisk on the NTFS volume and let Windows fix any disk errors.

When you have finished resizing the NTFS partition you will have to run another chkdisk which should be scheduled for you so I would normally boot into Windows after partitioning to let it do that before proceeding with installing Linux (just in case you HAVE to reinstall Windows you would want to do that before installing Linux).

In retrospect partitioning was a pain free procedure but I'm glad I did the preparation.

---

