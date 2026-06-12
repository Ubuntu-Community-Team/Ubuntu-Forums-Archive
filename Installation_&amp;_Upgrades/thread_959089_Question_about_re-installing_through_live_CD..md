---
title: "Question about re-installing through live CD."
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by yuuko on 2008-10-26
okay I'm preparing to install 8.10 when it's released, but I have a question.  Last time when I booted from the Live CD I was able to delete my old partition of ubuntu, however there were some locks next to the swap spaces I think.  So I believe I'm actually wasting about 1 GIG of space because I wasn't able to delete the old swap space.  Is there a way around these "locked" partitions.  Could I also delete every partition that has to do with ubuntu from windows XP and still boot using a live CD?  I know if I delete the ubuntu partitions I'll probably mess up the GRUB loader at startup, but will it still let me boot into the Live CD?

---

### Post by scragar on 2008-10-26
I'm going to take a guess and say ubuntu was using the swap partition as swap.

try running```
swapoff -a
```You might need sudo on it or not, I'm not sure. Try it without first in the essense of good security.

---

### Post by bulldog on 2008-10-26
Use the alternate install cd instead of the live cd.
It' s much quicker with the install anyway.
Choose,when you come to the partition part,manual.
Set your / to be formatted ext3,turn on the bootflag,set swap to be formatted as swap,mount your /home DO NOT FORMAT THIS ONE,and you' re ready to go.
That is,if you have a separate /home of course,otherwise skip the /home part.

The live cd does it the same way,but as scragar suggested,turn off the swap file.

---

### Post by yuuko on 2008-10-27
Okay I'll try what you guys suggested, thanks for the suggestions.  I'm still new to ubuntu so hopefully everything will go well.

---

