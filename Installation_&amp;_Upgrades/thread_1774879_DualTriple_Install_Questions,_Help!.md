---
title: "Dual/Triple Install Questions, Help!"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by JohnBonne on 2011-06-03
I have purchased a hard drive. I would like to install Windows and Ubuntu on it. Windows plays games and though I don't use it much, I  would still like to have a copy for hard stuff like games. The Ubuntu  may as well be 64 Bit. I have a Laptop with a 2.3 MHz dual Intel  processor and three Gigs of memory. The hard drive is
a 320 Gig Scorpio Blue.

Now for the initial set up questions.

First  I want to do a dual install on the new hard drive. Windows first; for  some proprietary reason, Vista wants to be the first installed. That's  right isn't it?   And Ubuntu I want installed on the same drive, that  ok? I install Vista first , set up a second partition, and then Ubuntu  goes in there. Am I right so far or have I missed something?

I  believe a boot partition has to be set up just  right to avoid problems. How do I go about that?
 
After I partition, is Wubi a good installer? Should I use a different installer??

Can anyone run me through the install install process. I once had the  best instructions I could find and they are lost. I had them and lost  them. Drat!

Can I keep the Ubuntu I have on the external drive in  the process? I don't want to eliminate the external drives O/S for  technical reasons. I would like to still have it around, maybe change  it  later for a lighter flavor of Ubuntu.

Problems with this plan of mine?

Suggestions for going back to an earlier release of Ubuntu on the main hard drive? 

Please feel free to make suggestions or brag about your install.

Regards,

Whew!

---

### Post by akand074 on 2011-06-03
Yes you can use the same drive, don't use wubi and yes Vista first would save you trouble. Just install vista (preferably in it's own partition you set up) but otherwise you can use the whole disk shouldn't be a big deal. Then just download and burn the Ubuntu ISO and boot into it, it has an auto installer feature which will automatically install it side by side with Windows. If you'd prefer a manual install this is what you should do:

1. Make a partition for Ubuntu (20GB is all you need, but if you have the space you can use more) set it to EXT4 choose to format it and set it's mount point to "/" without the quotations.
2. Make another partition about the same size of your RAM (3GB was it?) and set it to type "swap" and that's it
3. *Optional* if you want all your config files and data from ubuntu on it's own partition, you can make a separate /home partition. Basically just make a partition as big as you want, format it as EXT4 with mount point "/home" without quotations.

---

### Post by oldfred on 2011-06-04
+1 on akand074 suggestions.

You should not need a /boot partition for a standard desktop.

A link to installing a a second drive. I strongly suggest using manual install and then you can install grub2's boot loader to the MBR of the second drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external Maverick screens shown
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by JohnBonne on 2011-06-05
Thanks so much for your instructions in advance! Last night I installed  windows for gaming purposes. There are not any games I really want for Linux yet. Finally this afternoon I got Ubuntu installed in a partition along side Windows. Windows updated and Natty  upgraded, right on the first try. I am so proud of you aknd074, and thanks again, fred.






 Go.

---

