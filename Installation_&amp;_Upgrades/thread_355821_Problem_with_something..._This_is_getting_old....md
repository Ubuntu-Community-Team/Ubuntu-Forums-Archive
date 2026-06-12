---
title: "Problem with something... This is getting old..."
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by Ish on 2007-02-07
It seems I'm just knocking down error after error. Ubuntu better be worth it! So here's where I'm at, I had a problem because I installed with one of the controllers set to RAID and now have the controllers set to (I reinstalled).
IDE MODE
SATA MODE

The other options for them are both
RAID MODE
and
DISABLED

I'm not sure if one of those should be disabled or not. Just saying that because I thought it might be the problem.

So here's what happens GRUB loads (I think) and I get this
"Error: 15
File not found"
Then it gives me three choices after I press "any key" Which are,
Ubuntu Generic
Ubuntu Recovery mode
And 'memtest86?' 
But after selecting any of those I get an "Error: 15" 
Well I got on the 'terminal?' and typed in 'BOOT' but it gave me this
"Error: 8 The kernel must be loaded" <- Or something like that...
There better be a damn good light at the end of this very long dark error filled tunnel! ;p Thanks for your help, (assuming you do) in advance :)

---

### Post by Ish on 2007-02-07
No one knows how this might be fixed? I tried using find commands but all of them returned "Error: 15's" So GRUB is loading... But once it loads it's not finding the files... Did I partion wrong? I have a root, swap, and boot partion I think (Whatever the default is when it partions for you automagically). So GRUB is broke, or GRUB isn't finding the partions or file, I wish I had a better idea of what to do :confused: ...

---

### Post by meng on 2007-02-07
Do you have more than one hard drive (not partition, but hard drive)? I'm not that familiar with RAID issues, seems to be a common source of trouble.

---

### Post by Ish on 2007-02-07
Yes I have two harddrives the other one has (I think) nothing on it, no partions, on this install it was left as "FREE SPACE." I don't think this is a RAID issue as much as a GRUB issue? It could be related... :/ Yes it does seem to cause quite a bit of problems, I have seen many of those posts around. Something about RAID should be stickied or atleast linked to in a sticky about common problems/fixes (If there is something I missed it, I did lose my glasses and can't read well :P). Might solve a few questions without having other people to help.

---

