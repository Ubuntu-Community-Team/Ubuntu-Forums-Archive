---
title: "[SOLVED] Can't install, partition mess"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by Toci on 2008-11-17
Hello, I had Ubuntu installed but the sound became a mess so I decided to reinstall, unfortunately now when it asks me where I want to install it doesn't show my partitions, sometimes it shows just the hard drive (which I actually divided in 4) and others it appears empty.

 I downloaded "TestDisk" and so far it says there's a "Space conflict" but I don't know how to solve that.

 Vista works now but Partition Magic can't seem to fix whatever problem there is.

 Help please.

---

### Post by oilchangeguy on 2008-11-17
> **Toci said:**
> Hello, I had Ubuntu installed but the sound became a mess so I decided to reinstall, unfortunately now when it asks me where I want to install it doesn't show my partitions, sometimes it shows just the hard drive (which I actually divided in 4) and others it appears empty.

 I downloaded "TestDisk" and so far it says there's a "Space conflict" but I don't know how to solve that.

 Vista works now but Partition Magic can't seem to fix whatever problem there is.

 Help please.

use the partition manager on the live cd, and delete any non windows partitions.

---

### Post by Toci on 2008-11-17
Thanks for replying oilchangeguy. 

 GParted isn't showing any partitions, just a single space.

---

### Post by Toci on 2008-11-18
After checking with TestDisk I'm noticing a difference in the size of what my Hard drive should be, is that related to the problem?, can it be fixed with the Ubuntu Live CD?.

---

### Post by Bartender on 2008-11-18
Do you have Vista on the same disk, or is/was Ubuntu on a second disk?
GParted LiveCD is more reliable that using GParted from the Ubuntu LiveCD.
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

I'd use a GParted LiveCD to delete the partitions, then re-format them as ext3.  Ubuntu installer will re-format the swap area even if you tell it not to so don't worry about that.

Several folks have advised avoiding Partition Magic because it causes problems...

---

### Post by Toci on 2008-11-18
Bartender, thank you very much for your reply. Ubuntu and Vista were on the same disk, does that mean that if I use Gparted from a Live CD I could ruin Vista?, I read it might not boot afterwards and I'm not sure I have the right CD's to recover it.

---

### Post by Toci on 2008-11-20
Okay so I'm not sure what I did but it worked and I have Ubuntu installed again.

 I used TestDisk to create a new partition table and I also managed to find a Vista rescue CD which I used to check for errors, both programs reported nothing wrong from the beginning but there was clearly a change somewhere.

 There's still 9GB lost somewhere (as free space) but that's apparently not too important so I'm just going to leave it.

 Thanks again to those who took the time to reply.

---

