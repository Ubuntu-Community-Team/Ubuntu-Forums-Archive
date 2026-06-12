---
title: "Repartion /?"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by Kimm on 2005-10-24
Is this possible?
I started qtparted and it refused to do anything to the root filesystem.

I need to partion my Drive and free... maby 20 GB or something like that. I need to install Windows 2000 temporarily for a LAN-Party. Both Cedega and Wine refuse to run games after I upgraded to Breezy, so this is realy the only way out that I can see.

Do I need to use a LiveCD or something like that? If so... which one should I use?

And another question... after I install Win2k GRUB will be gone, right? How do I restore GRUB and make Windows available in the boot list?

---

### Post by aysiu on 2005-10-25
[QUOTE=Kimm]Is this possible?
I started qtparted and it refused to do anything to the root filesystem.[/quote] QTParted and other partitioning programs cannot partitions that are mounted, and if you're running QTParted from your root filesystem, the root filesystem is definitely mounted.

> 
Do I need to use a LiveCD or something like that? If so... which one should I use? Yes. I'd advise Knoppix or Mepis.

> 
And another question... after I install Win2k GRUB will be gone, right? How do I restore GRUB and make Windows available in the boot list? Follow [these directions](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Kimm on 2005-10-25
Ah thanks. I downloaded Knoppix and tried QtParted, but it could not resize my ext3 Ubuntu partion, only delete it.

I tried Ubuntu Breezy Live CD instead. GParted managed to find all the disks and I could set it up for resizing, but when I turn the process on, it works for a long time, then tells me something like this: "Atleast one procedure was made on a busy device", then it reloads the Partitioner and its back as it was before. Ofcourse, I am running it as root.

I realy dont get it. The HD is not mounted so it cant be busy... right? Anyway I can tell somehow?

If I need to run any aditional commands, tell me since I never repartioned a Linux system anymore.

---

### Post by Björn on 2005-10-25
Not even your SWAP is mounted? No partition on the same harddrive should be mounted i think, check and see if any extanded or linux swap is mounted.
I am trying to figure out how to boot breezy live without SWAP

/Björn

---

### Post by Björn on 2005-10-25
ah, another thread, you didn't even have to boot with no swap, you could unmount it =D
[URL="http://ubuntuforums.org/showthread.php?t=81171"]
http://ubuntuforums.org/showthread.php?t=81171[/URL]

/Björn

---

