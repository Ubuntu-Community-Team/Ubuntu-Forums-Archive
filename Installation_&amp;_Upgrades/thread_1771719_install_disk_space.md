---
title: "install disk space"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by doctortonic on 2011-05-30
I have an (old rusted && with dust) pentium III (Katmai) with 786 SD Ram, and 2 Hardisk as: 

Quantum Fireball        **6.4 Gb** @5400rpm
Seagate U4 St34311A     **4.3 Gb** @5400rpm

I wish to install on it Xubuntu 11.04 and I was thinking to make the partitions as follows in the quantum hdd:

 /boot -> 190 Mega
 /swap -> 768 Mega
 /     -> The rest of space (aprox 5 Gb)

Could I use somehow the free space from Seagate to be added to ''/'' ?

---

### Post by Hedgehog1 on 2011-05-30
Hi There!

You can use both hard disks at a set.

You will need to manually partiton the two drives (Use the 'Something else' option on the 'Allocate Disk Space' screen).

Use the entire Quantum Firebal as your '/' (root) partiton.  This is you best us of space for really small hard disk installs.

**/dev/sda1 EXT4 '/' (root)**

Then you can create 2 partitions on the Seagate drive:

[B]/dev/sdb1 EXT4 '/home' 3.3 gig
/dev/sdb2 Swap 1 gig[/B]

***The Hedge***

:KS

---

### Post by doctortonic on 2011-05-30
Thank you for suggestion. 
Your partition scheme look's good, so it will be as you said.
But I was  thinking to make also a **/boot **if the power failure's will corrupt the filesystem, for fsck to run corectly or, in these times there is no need for a /boot?

P.s
 I was thinking to use ext4, but I see btrfs is here, it's sable enough or is in some alfa/beta/rc/test stage?

---

### Post by baarn on 2011-05-30
i never really tried it out myself, but it should be possible to group both harddrives together in a logical volume group with LVM. afterwards it looks like one harddrive.

i am using xubuntu, and have some packages installed, depending on how many packages you want to install and how much stuff you want to put into your /home i would consider to outsource one of those heavier directories to their own partition.
(on my laptop)
/usr uses 3.7G
/home uses 1.3G
/var uses 1.6G
/ uses just 407M

thats a really small and fresh xubuntu, but i think it is to expect that /home will grow rapidly and /var and /usr will grow slowly most of the programs i think of using should be installed right now.
but i can only speak from my experience here...
uh yeah, another thing: my gentoo server running some proxies, server stuff (apache sambe etc) on gentoo with xfce aswell looks quite the same from distribution of drive usage...
except for /home because thats where i store all my movies, music and backups from my laptop

hope it helps

---

### Post by doctortonic on 2011-05-30
okay, i'll go with ext4, after reading some threads here.
AND I will play with LVM.

---

