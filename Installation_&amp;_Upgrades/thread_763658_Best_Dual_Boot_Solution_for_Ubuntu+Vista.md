---
title: "Best Dual Boot Solution for Ubuntu+Vista?"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by diplomat.x on 2008-04-23
So tomorrow hardy is being released. I am very excited.

I wish i could only use ubuntu but some other things force me to have a windows OS in my computer.

I have a new 250 GB hard-drive on which i want to install Vista and hardy heron. 

How do i go about doing this in the best possible way? I need suggestions on partitioning.

I also need a partition of about 20 GB where i could try other linux distros and delete them as i like. Where should this partition be placed in the hard-drive? Like in the end or middle or where?

And since these days ubuntu reads NTFS just fine, i dont see any reason why i should format most of the space in ext3 since that would also mean that most of my hard-disk stays hidden when connected to a windows computer.

Please guide.

---

### Post by Pumalite on 2008-04-23
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by diplomat.x on 2008-04-23
Thanks for the links pumalite. I am aware of the "how to" install.

Anyways, i have thought to do like this(check attachment).

Let me know what you think or any other suggestion.

---

### Post by Pumalite on 2008-04-23
It's hard for me to understand your picture. I think /swap of 1 GB it's fine. It would be better if you boot a Live CD and post:
sudo fdisk -l

---

### Post by Lantesh on 2008-04-23
It looks like you've got it planned out pretty good.  Maybe you might want to make the swap 2 gigs.  The only downside I see is that you will have to defrag the NTFS partitions from time to time, but that's the price you have to pay if you want Windows to have access to your data partitions instead of using ext3.

---

### Post by diplomat.x on 2008-04-23
Yes Lantesh, even i see that downside of using NTFS partition but most of my friends have windows so i need a good amount of space that is readily recognised in their computer when i attach my hard-drive.

And about swap, i have 2 GB RAM, do i still need 2 GB swap? I have never seen swap being used in gutsy...and it was set to just 512 MB.

---

### Post by Pumalite on 2008-04-23
1 GB is more than enough. Only in laptops /swap=RAM for hibernation.

---

### Post by punkybouy on 2008-04-23
How about installing Virtualbox and then running Windows in a virtual session.  I am running XP on Edgy that way and it works great.  I no longer need a stand alone Windows machine.

---

