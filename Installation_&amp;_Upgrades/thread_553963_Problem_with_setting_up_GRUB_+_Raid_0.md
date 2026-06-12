---
title: "Problem with setting up GRUB + Raid 0"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by tsukasa1105 on 2007-09-18
Hey all, 

I set up my ubuntu installation using the fakeraid howto article on the ubuntu wiki ([https://help.ubuntu.com/community/FakeRaidHowto#head-a019bddf36ad61bc29d9b787c95d8921ea762ba9](https://help.ubuntu.com/community/FakeRaidHowto#head-a019bddf36ad61bc29d9b787c95d8921ea762ba9))
and everything up until setting up grub has been a breeze. The problem is with root (hd0,5). That is indeed the partition number i want to work with (partition 6 in actuality), but I get errors that the partition doesnt exist. I tried root (hd0,1) all the way through 6 and nothing is recognized. 

Now here is why I think this is: 

Going into /dev/mapper and doing an ls produces something of the sort:


* A device called jmicron_GRAID
* Not sure what this is actually, but its 'jmicron_GRAID          <lots of spaces>               '
* My numbered partitions, which are 'jmicron_GRAID                          <insert partition number here after many spaces>

I have to setup the device pointing to 'jmicron_GRAID' but the partitions themselves are 'jmicron_GRAID   <lots of spaces>    <number>. I think the spaces are the culprit. So what can I do to fix this? I already edited my menu.lst to point to the correct partiton (im assuming using '\' for escape characters is okay for this?), but I don't know how to get grub to install itself on my MBR properly.

---

