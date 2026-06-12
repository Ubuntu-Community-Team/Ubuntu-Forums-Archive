---
title: "GRUB error 17"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by Pai on 2007-03-08
**Background:**
Today I began preparation to dual boot XP and Edgy.

My plan was to partition my drive appropriately, then install XP, and finish off with Edgy.

So I used GParted to reformat my old drive setup, and created the following (in order):

1 ntfs primary
1 extended partition, containing Swap, / (ext3), and /home (ext3)
1 shared fat32
1 DellRestore partition.  This partition contains an image of the OS, because no CD was shipped to me when I purchased the computer. When I have reinstalled XP in the past, this is the tool I have used.

So I checked to make sure, and that layout was successfully achieved. Currently, the only partition that actually has anything on it is the DellRestore, since I haven't yet installed any OS.

**Problem:**
Everything was going as planned. So I rebooted to begin installing XP. To do so, you hold control and press F11 after first powering on the system. This should access the recovery partition. I have done this before successfully, but that was when I actually had a OS on my system to be overwritten. Now when I do it, I get the GRUB error 17 (cannot mount selected partition). Something is preventing me from accessing the recovery partition which contains the image of XP, which means I can't continue with my original plan. What can I do about this problem?

Thanks in advance. Any advice helps, because currently I'm limited to this relatively useless school computer.:-#

---

### Post by rsambuca on 2007-03-08
What you'll want to do is to recover your XP first.  I say recover because you don't have the actual installation disks (same as me).  After you have XP the way you want it, then you can use gParted or the ubuntu live cd to set up your partitions the way you want.  Then install ubuntu and grub will automatically detect XP and give you an option at boot time.

---

### Post by SuSUntu on 2007-03-08
This is a specialized case because of the Dell Recovery partition, obviously. So getting your XP partition working, as rsambuca suggested, takes some specialized information. Luckily (though not guaranteed to work, of course), some nice person has provided everything anyone ever wanted to know about how the Dell system works and how to attempt to fix it after repartitioning your drive:

[http://www.goodells.net/dellrestore/](http://www.goodells.net/dellrestore/)

Though you should probably review all the information (there's lots), this section seems to be particularly germane to the issue at hand:

[http://www.goodells.net/dellrestore/fixes.htm](http://www.goodells.net/dellrestore/fixes.htm)

Good luck and let us know how it goes.

---

