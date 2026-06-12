---
title: "Help restoring the partition table"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2012-08-19
Hi,

I have a Dell Inspiron 17R laptop and I had some hardware issues (the SD-card reader didn't work and the keyboard kept losing keys).

I sent it to Dell for repair, and they replaced the keyboard and the motherboard really fast. But, for no reason, they did a "system reinstall".  I wonder if they do it to discourage my sending them the PC again.

Anyway, this means I lost the whole Windows setup (no big deal, I hardly ever use it), and all the Ubuntu partitions, which is where I have most of my work. I have backups, but I'd like to recover the whole setup without reformatting.

So I fired up System Rescue CD, and used testdisk to find the old Linux partitions. They were there indeed, but when I recovered the old partition table, I screwed up the (new) Windows installation.

With testdisk, I can find the Windows installation, but if I recover it, it takes up the whole disk, and it will screw up Linux again.

What I would like to do is to recover and resize the Windows partition, keeping Linux. Then I can run grub and get the installation back to normal.

Is there any way to do that?

The situation now is not too bad. I can boot into Linux with a tool that searches active partitions, but I would like to do it more user-friendly, and also keep Windows. Not that I use it much, but sometimes I need to do some testing with it.

---

### Post by darkod on 2012-08-19
Wasn't testdisk able to also recover the old windows partition(s)?

Otherwise I am not aware how to bring it back. You said it yourself, if you bring back the new windows partition you will mess up ubuntu which is more important to you. I wouldn't play too much with it because you can lose ubuntu.

If testdisk doesn't see the old windows partition, forget about it. That's safest. Recovering the ubuntu partitions left some unallocated space I guess (where the old windows was), so you can consider installing windows into that space if you still need it occasionally.

---

### Post by skamarla on 2012-08-19
The original Windows install is gone for good.

Testdisk sees the installation that the repair guy, in his infinite wisdom, did. That's the only Windows I have (I can also try to restore the installation disk that I created when I bought the PC, but this will even be more intrusive).

Since it is an OEM install, you have the privilege of paying for Windows but don't get any media to reinstall it legally.

I suppose I can backup the Linux partition with partimage or something like that, restore Windows, and then do a normal Linux install. But I hoped there would be a faster way.

---

### Post by Topsiho on 2012-08-19
You want to keep the newly installed Windows, though you did not mind loosing the old Windows. That's why I dare to give you this answer.

You can manage your partitions using a liveCD, or even during the install itself, both ways gparted is used.

That way you can identify the partition that Windows sits in (it is an NTFS partition, green), and shrink it so as to make room for Ubuntu, if necessary. If you are lucky, that succeeds. If not, it doesn't.

Then you can create the necessary partitions for Ubuntu, I always create one for /, and one for /home, and another one for swap (twice the size of the RAM (working memory)). But that's up to you. Or you let Ubuntu decide this during install (use all unallocated memory). You take care that all memory not used by Windows is unallocated.

I would rather have shrunk the Windows partition in Windows itself, as Windows has problems if it finds a disk, when booted, that contains another situation than it knew previously. From posts I have read, you should let Windows sort it out itself, which can take a long time, when it complains.

If you loose Windows, you can install Ubuntu using all the disk :)

Good luck,

Topsiho

---

### Post by skamarla on 2012-08-21
In the end, I tried to restore the Windows partition, but it didn't work out. Windows was complaining of some file it couldn't find. So I bit the bullet, restored Windows from scratch, then performed a normal kubuntu installation (shrinking the Windows disk space a little more), and finally restored the Linux backups.

---

### Post by Topsiho on 2012-08-21
Great.

Topsiho

---

