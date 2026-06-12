---
title: "Duel boot 9.04 &amp; 9.10"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2009-12-09
Can I duel boot 9.04 & 9.10?

I have a machine that I did a clean install of 9.04 when it was released and it uses the entire partition.

I would like to go back in forth until I can make sure there are no issues with my machine and the new 9.10. I have read of some wireless and other driver problems and my 9.04 is working great!

I have found many references about duel booting windows and ubuntu but I can't find anything about duel booting two different releases of ubuntu.

Is it possible and if so can someone point me to a help page or give me instructions?

Thanks, Bob.

---

### Post by audiomick on 2009-12-09
Hi Bob.
Yes, it is possible. You will need to shrink the existing partition to make room for the new system. Since the new one is just for testing, you wont need to give it all that much room. 20 gig or so should do it. If you already have a seperate home partition, you should be able to mount that for the test installation, although there is a small chance that this might mess something up in the existing installation. 
As far as I know, grub will sort it self out, but I am not a great expert.

---

### Post by oldfred on 2009-12-09
I have winXP, Ubuntu9.04 32bit (upgraded every 6 months for 3 years), 9.10 64bitand another 9.10 from alpha.

I originally was chainbooting from a dedicated grub partition. The new grub2 took over the mbr and found all the installs without any real issues other than the menu is very long. I am converting from everything in root to separate /data and a separate /home. I already had a shared NTFS partition to share some winXP stuff, but now am 90% in Ubuntu. I had so much cruft and many applications and just now am booting primarily in 9.10 but going back to find what setting or applicaton I am missing. I had experimented with moving all apps to a test 9.04 64bit install but that installed many old apps that I really did not want. I am not sure I even want a separate /home as I am finding many old settings and history that I do not want to convert, so I did not copy oldhome to new home. My data is now in a separate partition and linked into home so that does most of what a separate home is for. I can easily back up home since it is small.

---

### Post by bob brazie on 2009-12-10
Thanks, but if it's possible i am looking for a how-to I guess.

Any ideas?

---

### Post by oldfred on 2009-12-10
The quick how to is just make a new partition with gparted from a liveCD and use the manual install so you choose the new partition you made and also reuse the existing swap partition. Any other way (auto) will create duplicate swap partitions but will also work.

You also have to decide which boot loader you want. The new install should find the other install and let you choose which to boot. The new install will automatically become the install to the MBR unless you use the advanced button near the middle/end of the install.  If you still want the old boot you will also have to update it to see the new install.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by bob brazie on 2009-12-10
"If you still want the old boot you will also have to update it to see the new install."

How do I up-date it? I assume during boot I will be able to choose between 9.04 and 9.10?

Thanks for the help.

---

### Post by oldfred on 2009-12-10
The new grub2 is very good at finding other installs. If you want your old grub to be in charge you would have to add an entry at the end of menu.lst. (Old grub may find the new install on an sudo update-grub command also).

---

### Post by bob brazie on 2009-12-11
I will give this a try next week and mark this as solved if I don't have any other questions.

Thanks to all, Bob.

---

