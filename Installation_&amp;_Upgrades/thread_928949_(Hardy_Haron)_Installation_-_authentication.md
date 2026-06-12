---
title: "(Hardy Haron) Installation - authentication?"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by Nlagg64 on 2008-09-24
Hi, beginner here. Trying to install Ubuntu, seems like it'd be a fun OS to learn. But first I need to install before I learn. :P


I have the burned CD, following a guide on the forums for burning it. Everything checked out, followed it perfectly, no error according to the guide.

When I choose "install" on the ubuntu boot screen, it does the progress bar, and then it gets something like this:

Buffer I/O error on device sr0, logical block (numbers here)



Does that a couple more times.... then:

SQUASHFS error: unable to read fragment cache block [352d222]
SQUAHSFS error: unable to read page, block 352d222, size 60b7

Goes in a pattern like that for a while...

It sets up some more stuff.... and then...


This pops up 10 times:

User not known to the underlying authentication module.




Then it locks up.


Help please? Beginner here. Thanks.




HERE ARE THE GUIDES I USED:

[Guide 1]("http://www.psychocats.net/ubuntu/iso") - getting the CD (worked out perfectly as far as I'm concerned).

[Guide 2]("http://www.psychocats.net/ubuntu/installing") - Installing it (Failed, as you know, after the loading/progress screen).

---

### Post by didac on 2008-09-25
> **Nlagg64 said:**
> 
Buffer I/O error on device sr0, logical block (numbers here)


Looks like a bad sector in the installation CD. Or maybe the CD drive itself is getting older?

---

### Post by WWSmith36 on 2008-09-25
What guide are you using?
Are you using the alternateCD rather than the LiveCD?

---

### Post by Nlagg64 on 2008-09-25
Let me send you the links to the guide(s) I followed. I'll edit my post when I find it.

[Guide 1]("http://www.psychocats.net/ubuntu/iso") - getting the CD (worked out perfectly as far as I'm concerned).

[Guide 2]("http://www.psychocats.net/ubuntu/installing") - Installing it (Failed, as you know, after the loading/progress screen).

---

### Post by Rattamus on 2008-10-29
I had the same problem.  I finally found that I was using a CD ROM drive that was not compatible w/ the Ubuntu 8.04 disc.  I tried a DVD drive that was newer and the installation worked fine.  You might have to install a newer firmware.

I hope that helps.

---

