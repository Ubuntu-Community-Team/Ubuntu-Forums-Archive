---
title: "Dual Boot XP GParted Confusion.."
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by cad2blender on 2007-09-29
Ok I want to install Ubuntu on a existing 250GB drive that has about 60 GB of USED (XP) space. Now I was installing Ubuntu and the slider did not show up you know where it asks me to set the size of the partition. There were only 3 options 
1. Format entire HD
2. Used largest unallocated space
3. Manual
After doing some research I found out that the best way was to use gparted and create a partition for ubuntu. This is the part I am confused. In gparted It shows that there are 3 partitions one that is 3 GB another that is about 240 GB and another that is 8 MB, yes MB. Now I think I can just shrink this 240 GB partition the one with XP I suppose and use the unallocated space to installed Ubuntu right? The reason that I am confused is that when I did this in another buddies IBM and he had one partition for XP (60 GB) another that was about 10 MB and about 100 GB of unallocated space, this was simple, just install ubuntu in that unallocated space. duh. So it this the correct way or am I going to screw up my system? Do I lose data if I resize an existing partition, in this case XP? Thanks for the help guys...

---

### Post by Pumalite on 2007-09-29
Do you have a laptop?

---

### Post by cad2blender on 2007-09-29
yes but why would that matter?

---

### Post by Pumalite on 2007-09-29
The root (pardon the pun)of the problem is that you probably have a small 'recovery partition'. Did they give you any CD's when they sold you the laptop?

---

### Post by cad2blender on 2007-09-29
nope I have no cd's but If I press f11 while booting it goes to Compaq's "recovery suite" That is the small partition.

---

### Post by cad2blender on 2007-09-29
Ok I defraged my HD so all my files are not scattered, then I'll resize my main partition to accomodate my ubuntu partition using gparted, finally install ubuntu in THAT created partition. I think that is how it is done.

---

### Post by Pumalite on 2007-09-29
Yup! Don't mess up your 'recovery partition'

---

### Post by cad2blender on 2007-09-29
ok I did all that now I keep getting and error saying that it does not detect a root system file please correct this in the partitioning menu.

This iswhat i did:
1. defrag
2. run gparted to shrink xp's partition
3. I have about 70 GB of unallocated space
4. run the installer and on step 4 I select manual
5. now in step 4 I select to install in partition "free space" and click foward but then I get the error message

Now What?

Thanks forhelping soo much

---

### Post by Pumalite on 2007-09-29
You have to give at least 10 GB to '/'

---

### Post by logos34 on 2007-09-29
I see a problem here: if you already have 3 partitions, and you're installing on a fourth (created from the main 240 MB which you shrank), then you won't be able to make a swap (limit 4 primary parititons).  So make an extended partition out of that space, then create two logical partitions inside: a ~1 GB swap (/swap) and the rest to an ext3 root partition, mounting like pumalite said at '/'.

Here's some screenshots that might help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html)

---

### Post by cad2blender on 2007-09-29
Drumroll please... I am posting this from my Ubuntu installation! Thanks for all your guys help. Especially your patience, well I got to tinker with my new Ubuntu!

---

### Post by Pumalite on 2007-09-29
Glad you got it working.

---

### Post by cad2blender on 2007-09-29
Ok maybe one more question :) Is there a way that I can boot XP first without any intervention. For example just turn on the computer and it boots directly to XP? Then whenever I want ubuntu press a key or something? If this is not possible no worries. By the way the desktops effects are AWESOME who needs Flip 3D?!

---

### Post by Pumalite on 2007-09-29
You would have to edit your menu.lst, go to the line that says 'default=0? change it for where Windows is, knowing that Grub starts counting from 0

---

