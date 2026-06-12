---
title: "Reinstall Grub?"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by fineghal on 2007-02-16
So I was installing another operating system, and long story short it fubar'd my MBR. Grub error 17, nothing will load...

Thinking I can recover with a live cd of some kind, I realize all of my cds have an older kernel. (I have a 965 board, needs those Jmicron drivers) So, I grab the old Windows cd and drop to the recovery console, and fixmbr.

So now I can boot to my windows partition. Yay!

But I want the linux install back, it's got a lot of stuff on there. 

I've got a grub installer that I haven't tried yet, and I can download another 'buntu cd with a newer kernel and reinstall grub from that, but here are the questions:

Which disk do I put it on? I'm thinking the MBR for my windows disk.

Disks go like this:
hda - Windows
hdb 
Win partition
OS X partition
Extended partition containing another win partition and Swap
and finally the actual / partition.

I'm thinking reinstall grub on hda, set it up to boot windows, and also point it at the linux partition which should be something like hdb4.

Will this work?
And if the grub super disk doesn't work, can I reinstall grub from the recovery console of a live cd? If I have to, will re-installing ubuntu wipe all my data, or well it be like a windows in place reinstall?

---

### Post by mikewhatever on 2007-02-16
The setup you want with GRUB should work. GRUB can be reinstalled from both the Super Grub and Live CD. I am not sure whether or not you can reinstall Ubuntu and keep the data on that same partition.

---

