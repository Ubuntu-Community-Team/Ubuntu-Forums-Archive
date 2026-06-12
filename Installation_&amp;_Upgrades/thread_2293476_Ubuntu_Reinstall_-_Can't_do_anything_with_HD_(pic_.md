---
title: "Ubuntu Reinstall - Can't do anything with HD (pic attached)"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by mr_si on 2015-09-05
My install died earlier in the week (Kernal upgrade, failed to boot. Some sort of known bug with ACPI PCC lookup). I don't know if it was powered off at a bad moment, ... live key failed to read the disk , so I've deleted all the partitions and reformatted it in NTFS on my Win7 box. Checked the disk there, no errors.


The live key still can't read the disk (same errors as before the format I believe). Any idea what I can do with it?

[IMG]https://dl.dropboxusercontent.com/u/28380264/badhd.png[/IMG]

---

### Post by ajgreeny on 2015-09-05
Try using a live system from USB or DVD to delete the partitions you made, leaving the disk with unallocated space, then you should be able to use gparted on the live OS to make new partitions if you want to, or leave it as unallocated space and make partitions on the fly as you install Ubuntu.

Windows can and often does make dynamic partitions which are unreadable and unusable in Linux, so it is usually best to make partitions for Linux with Linux.

---

### Post by mr_si on 2015-09-05
> **ajgreeny said:**
> Try using a live system from USB or DVD to delete the partitions you made, leaving the disk with unallocated space,

That's what I'm trying to do, I've booted off a live 15.04 key, it wont let me read the disk, delete partitions, do anything at all. The error message has been the same all along.

I'd have happily fixed it in Linux if I'd found a tool that was capable of doing it... and I'm still looking.

---

### Post by oldfred on 2015-09-05
Can you create partitions with gparted from live installer? Or does it also give errors?

Then what does Disks from live installer show. And in upper right corner icon of Disks for more info, what is Smart Status of drive? If passed ok, if not you have drive issues.

---

### Post by mr_si on 2015-09-08
So the SMART check failed. Guess I'll give this one up as a bad disk. Thanks for the help though.

---

### Post by Bucky Ball on 2015-09-08
Bad luck about that. :(

Please mark the thread as solved. This won't close it but will help others. Thanks.

---

