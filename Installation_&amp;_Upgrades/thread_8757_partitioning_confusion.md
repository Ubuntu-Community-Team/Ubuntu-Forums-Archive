---
title: "partitioning confusion"
date: 2004-12-20
forum: Installation &amp; Upgrades
---

### Post by hannaframmis on 2004-12-20
hey all...i'm completely new to Lnux, but would like to gain some experience in it's use.  i'm having trouble getting to first base, so forgive some incredibly newbie-like questions:

i have Wxp, with a 40g master hd and a 120 gig slave hd, that was formatted into 2 partitions when i installed it (80g/40g), with the intent of installing  Linux on the 40g partition and using a dual boot system..  when i load the Ubuntu cd, and i get to the partitioning part, i get quite lost, and i have been unable to find specific how-to's on this particular step (prolly coz it's so basic).  several questions, not necessarily in order (coz i can't refer back to the areas i'm confused about while i post this):

- i do not see how to subdivide this 40g drive in order to create a small partition for a swap file nor am i clear on what is meant by "mount a partition on /".

- i am not clear on the appropriate usage method or file system, relative to the way i want to set this up.

- i am also not clear on where the RAID step comes into play as well as the file volume step that appears beneath it on the Partition Disk screen.

 can anyone either clarify this are for me or point me to a faq/tutorial/how-to that explains this area a bit more clearly (like, step by step)?

i realize my questions are a little scattered, very basic, and probably dumb and i'm prepared to suffer the slings and arrows of newbie-ness :? 

tia

---

### Post by Rancoras on 2004-12-20
Thwipppp!  (That was an arrow of newbie-ness)  :lol: 

If that 40g partition is clear of data, then delete it once you get to the partitioning stage.  Make sure you are deleting the correct partition.  You have backed up anything you don't want to lose, right?  Once that partition is gone and you have 40g of free space, create a swap partition.  I usually make mine 1.5 times the amount of system memory up to a 1 gig maximum partition size.  Then create the rest of the free space as a single ext3 partition.  This partition is the one you want to mount at /.  What is "/" you ask?  Think of the filesystem as a tree.  / is it's root, as a matter of fact that's what it's called.  / = root  All other folders branch off of the root.

As I said before, make sure you have a good backup of anything you don't want to lose forever.  

This should be enough to make you dangerous.  Make sure to check out [www.ubuntuguide.org](www.ubuntuguide.org) for post-install tweaks and configurations.  It's a great resource.  Do yourself a favor, google around for some very basic linux documentation.  There's a great book, if you're so inclined, called Linux In a Nutshell.  It's an invaluable desk companion.

---

### Post by Buffalo Soldier on 2004-12-20
Don't feel too bad about yourself, everyone was a newbie once.

Here's a few website that I think could be helpful.

On partitioning:
[http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apa.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apa.html)
[http://www.tldp.org/HOWTO/Partition/](http://www.tldp.org/HOWTO/Partition/)

On Ubuntu installation:
[http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/index.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/index.html)

After you've succesfully installed Ubuntu:
[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Rhodan on 2004-12-21
[QUOTE=hannaframmis]hey all...i'm completely new to Lnux, but would like to gain some experience in it's use.  i'm having trouble getting to first base, so forgive some incredibly newbie-like questions:

i have Wxp, with a 40g master hd and a 120 gig slave hd, that was formatted into 2 partitions when i installed it (80g/40g), with the intent of installing  Linux on the 40g partition and using a dual boot system..  when i load the Ubuntu cd, and i get to the partitioning part, i get quite lost, and i have been unable to find specific how-to's on this particular step (prolly coz it's so basic).  several questions, not necessarily in order (coz i can't refer back to the areas i'm confused about while i post this):

- i do not see how to subdivide this 40g drive in order to create a small partition for a swap file nor am i clear on what is meant by "mount a partition on /".

- i am not clear on the appropriate usage method or file system, relative to the way i want to set this up.

- i am also not clear on where the RAID step comes into play as well as the file volume step that appears beneath it on the Partition Disk screen.

 can anyone either clarify this are for me or point me to a faq/tutorial/how-to that explains this area a bit more clearly (like, step by step)?

i realize my questions are a little scattered, very basic, and probably dumb and i'm prepared to suffer the slings and arrows of newbie-ness :? 

tia[/QUOTE]
 Or just use the auto-partition option and let it do it for you, make sure you are selecting the free space though.

---

### Post by hannaframmis on 2004-12-21
[QUOTE=Rhodan]Or just use the auto-partition option and let it do it for you, make sure you are selecting the free space though.[/QUOTE]

so delete the 40g partition, as Rancoras suggests above, then select the auto-partition option for the newly freed space (which i was not aware existed coz i haven't gotten that far), and it will make the appropriate selections and/or present me with the obvious options?

one more dumb question...by turning on the bootable flag for the selected partition, i then make this space, with Linux installed, a boot option alongside XP when i boot up, correct?

---

### Post by Rhodan on 2004-12-21
[QUOTE=hannaframmis]so delete the 40g partition, as Rancoras suggests above, then select the auto-partition option for the newly freed space (which i was not aware existed coz i haven't gotten that far), and it will make the appropriate selections and/or present me with the obvious options?

one more dumb question...by turning on the bootable flag for the selected partition, i then make this space, with Linux installed, a boot option alongside XP when i boot up, correct?[/QUOTE]
 The automatic feature will set it bootable by itself, grub will install and be the boot up menu, giving you an option to boot to XP or into Ubuntu.

---

### Post by hannaframmis on 2004-12-21
ok - got it sorted out...thanks for the help.  my mistake was setting aside a partition, rather than leaving free space for the installer to partition.  thanks again!

---

