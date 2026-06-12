---
title: "Odd Grub problems with Dual Boot"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Rand0m_Hero on 2010-06-29
I cant see anything specific to my issue so I figured a new thread might be interesting.

I just started using Ubuntu on my Laptop as my CentOS was having wicked problems with my wifi adapter. I have setup Windows XP first then ran the WebUI exe to install a partition of Ubuntu 10.04 into the system. 1 disk- seperate partitions. What I really want to do is have ubuntu control my MBR with grub2.  I have followed a bunch of walkthroughs but when i run the command:
sudo aptitude install grub-pcit wont actually launch the grub walktrhough for selection. I dont mind formatting and starting again but I was hoping to see if anybody else was having/had the same issue.

When I turn on the computer ill get the windows boot selection list first then grub vs. 1.98-1ubuntu5.

Just want to basic it out. Any help appreciated!

---

### Post by Mark Phelps on 2010-06-29
If I understand what you did, you installed Ubuntu using Wubi.

That does not use GRUB.  It uses a variation of GRUB known as GRUB4DOS -- which installs and runs inside MS Windows.

IF you try to force an install of GRUB or GRUB2, you'll only "break" what you have now -- and probably end up not being able to boot anything.

The only way to have GRUB2 do the boot control is to install Ubuntu outside MS Windows into its own partition.

---

