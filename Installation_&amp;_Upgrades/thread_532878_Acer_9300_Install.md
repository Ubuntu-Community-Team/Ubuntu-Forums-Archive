---
title: "Acer 9300 Install"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by mohnkern on 2007-08-23
I hit my first machine where an Ubuntu install didn't goet 99% flawlessly, and this one is a weird one.

I recently purchased an Acer Aspire 9300, upgraded it to 2 GB of ram, and change the partitions so there was 30 GB free for an Ubuntu install.

(There were originally 3 partiions, a rescue partition, a root partition, and a data partition.)

This machine has Vista on it (yeah, if I'd had any choice at all.....)

I put in the Ubuntu install disk (I tried the 32 bit, and the 64 Bit, since it has a dual core AMD in it), and started the machine up.

Opening menu came up fine, however, if I run the memory test, or the Install, the screen flashes:

"Failed to allocate Memory resource" and some number.  It goes by so fast  I can't see it.

Then the screen goes black, the CD drive flashes for awhile, and then it locks up.

Anyone got any ideas as to what would be causing this?  I'm surprised I'm seeing this even in the memory test.


Vista is running fine, and I've "pushed" it pretty hard resource wise, so I doubt it's a bad memory issue.

---

### Post by Pumalite on 2007-08-23
Try Alternate CD. Do md5sum on your iso, Burn at 4x.

---

### Post by mohnkern on 2007-08-23
Will try a different CD,  Here's the md5 sum

e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso


(But I couldn't find an md5 to compare it against.)

---

### Post by Pumalite on 2007-08-23
The whole purpose of an md5sum is to compare it to the original. Otherwise you could be working with a corrupted file, not know it and break your head against a brick wall.

---

### Post by mohnkern on 2007-08-23
Checked with md5's at [http://us.releases.ubuntu.com/feisty/MD5SUMS](http://us.releases.ubuntu.com/feisty/MD5SUMS) and my iso has a match, I'll try burning another CD, see what we get.

---

### Post by mohnkern on 2007-08-30
Actually, it just required LOTS of patience.  It ultimately came up (after 10 minutes).  I haven't gotten wireless to work yet.  But that's next on my list.

---

### Post by Pumalite on 2007-08-30
Good!. Glad for you.

---

### Post by mohnkern on 2007-08-30
NOw I just need to figure out why I can't browse my windows network on any of my machines.  I can map to stuff, I just can't browse.  Damn strange.... Thx microsoft.

---

### Post by Pumalite on 2007-08-30
Do you have Samba installed?

---

