---
title: "Gutsy kernel compilation for DMA"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by skiffler on 2007-12-27
I've recently installed Xubuntu on an old Toshiba Satellite 2800-400 (750MHz PIII, 128MB memory). It took 7 hours! It boots up very slowly. At first I though that it was a problem with the HDD, but after looking around the forums it seems that there is an issue with the HDD driver, as it insists that the IDE drive is sda and not hda. I though that this was a perfect opportunity to compile a custom kernel with the DMA driver in. I though that I'd follow TSELIOT's guide to Kernel Compilation for Newbies. However I can't seem to find the source repository for 2.6.22-14-generic. I've tried 'software sources: ubuntu source code', tried to edit sources.list, but every time I run sudo apt-get install linux-tree I get the same message "couldn't find package linux-tree". What am I doing wrong? BTW I am a complete Linux and programming newbie, but feel that this is within my capability. Of course ideally a kernel with the appropriate HDD driver would be a better solution for me...

---

### Post by Partyboi2 on 2007-12-28
Try doing a search for "linux-source-2.6.22" Linux-tree is no longer used

---

### Post by skiffler on 2007-12-28
Thanks very much. Worked a treat. Now down to the hard work of editing and compiling...

---

