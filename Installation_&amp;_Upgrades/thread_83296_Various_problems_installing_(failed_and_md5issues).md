---
title: "Various problems installing (failed and md5issues)"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by McBrain on 2005-10-28
Hi there,
I wanted to do a fresh installation of Ubuntu 5.10 (currently running 5.04). Various strange things happened resulting in not being able to install. Here the complete history:

1) Downloaded ISO image with bittorrent (failed several time with an weired error message that the disk is currupt), which was successfull after a couple of retries.
2) Bruned, installed, failed: reason, certain package could not be installed
3) Burned again at reduced speed, installed, copying of files worked, first reboot into freshly installed system to configure remaining packages failed and ended in a 'white screen' with a lot of stack information (I assume happened when starting gnome)
4) So I assumes my image might be currupt (because of problems in first step)
5) Downloaded the image again this time using jigdo, could not finish because 1 file was MISSING on all server called 'hw-detect.....', copied from the bittorrent into jigdo folder, ISO image created.
6) This is actually the most suprising thing: This time I checked the md5sum of the image, was not correct, by chance I tried again, and it was different, tried again and again, kept changing (I thought this should be constant on a not changing file)! By the way tried in on both images, bittorrent and jigdo, for a while, the bittorrent was right, but than that also started changing!

Any ideas?

Thanks & regards :confused: 
McBrain

---

### Post by john_c on 2005-10-28
I have had this happen as a result of hardware problems.  An overheating cpu and incompatible memory modules.  The memory checked out in all other respects but caused me a lot of trouble doing md5sums and burning isos.

Good luck

John_c

---

### Post by McBrain on 2005-10-28
Wow!

Obviously the memory that I just added to the box is damaged, the memtest also gives errors for it!

Just with the old one the md5sum is constant!


Thanks! :D 

PS: As I have on image with the right md5sum (the bittorrent), I will not try to understand why the file from the jigdo was missing!

---

### Post by john_c on 2005-10-29
Further to the memory problem - I had a 128 mb module that worked well and then bought another 256 module and plugged both in.  Everything worked and it wasn't until I had inconsistant md5sums on the same file that I finally clued in (after burning a number of coasters).

I returned the new module, got another and the same thing happened.  Either module works well by itself but they do not cooexist happily.   Both check out fine with memtest.  Can't say I understand it but it sure took some time and head scratching to figure it out.

Glad I was able to help.

John_c

---

