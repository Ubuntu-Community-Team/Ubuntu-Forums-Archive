---
title: "Multiple Hard Disks and Dual Booting woes"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by chisler on 2006-06-03
OK so I really wanted to give linux and more specifially Ubuntu a go this time. I'm a windows user for years and would class myself as reasonably technical.

So I booted Ubuntu 6.06 (tried both AMD64 and i386 versions) from the live CD(s), looks good so I choose install from the desktop. 

I have 4 hard disks in my machine 2 x 74gb raptors and 2 x 400gb Seagates. All are SATA. Under Windows the 2 raptors show up as C: (1st HD), D:, E: (2nd HD). The two 400 GB Seagates show up as F: and G:. All of these partitions are NTFS with the exception of G: which now has ext2/swap partitions.

I cleared everything off the 2nd 400gb drive (G: ) so I could have that for my Ubuntu install. 

The install from the desktop went perfectly, or so I thought. I choose the correct drive and told it to repartion/format it for me. 

I click the message to restart at the end of the install. Unfortunately the machine does not give me a GRUB menu, it simply boots into Windows.

I know it has something to do with where GRUB is installed but the point is I was never given an option to choose where to install it and it obviously didnt do the right thing itself.

I have searched high and low and tried various options to get it to work but cannot for the life of me figure this out. I'm sure the experienced linux people will go "ah you idiot, you should have done X" but my point is an average user has no chance of getting this stuff to work. I realise an average user wont have 4 hard drives but I'm sure the same problem could be there for people with more than 1 drive.

So if someone can point me in the right direction (and btw the GRUB docs are not straightforward) that would be great. I really wanna give this a go but if I cant boot into the OS except from the live CD then its back to windows for me.

Chisler

---

