---
title: "feisty upgrade menu.list"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by merlin666 on 2007-09-03
I have been using edgy on a dual boot system for a while now, and have tried to upgrade to feisty several times. Finally, after many hours of downloading it looked like all files had arrived and an other hour of installs started. When I checked back there was a light blue screen with login prompts where I entered my old user name and password and ... nothing happened. All I got was a blank light blue screen. I rebooted and was greeted with my old edgy menu.list with 2.6.17 kernel as choice. I tried that but the boot failed because of a missing RAID 456 module. In recovery mode there were additional messages that are no devices in a conf file, and it failed to assemble all arrays.

I was able to use the live CD to inspect the boot folder and menu.lst and I found 2 problems:

1) part of the feisty kernel seems to be missing as there is no initrd.img-2.6.20-16-generic file that corresponds to the vmlinuz-2.6.20-16-generic which is present in the boot folder. where can I find a missing initrd.img?

2) the menu.lst entries refer to a root=UUID=.... that worked in edgy; but with feisty I get a message that /dev/disk/by-uuid .... does not exist. how can I find the correct UUID code?

---

### Post by merlinus on 2007-09-03
You might try **sudo fdisk -l** to see your partitions, and then **blkid** to get the UUIDs for them.

-merlin

---

### Post by merlin666 on 2007-09-03
Thank you, it seems that the UUID as used in menu.lst points to the correct hda3. Somehow through the upgrade process it did not get configured though.

 I am reading up on these issues in the context of mdadm but I'm not sure if this will lead to a solution, I am very confused about the RAID, as I am using a laptop with a simple hard drive.

---

### Post by merlinus on 2007-09-03
FWIW, many folks have problems when upgrading as opposed to a fresh install.

So you might consider installing 7.04 from scratch....

-merlin

---

### Post by merlin666 on 2007-09-05
Actually, I managed to get it to work and it was not that hard, though I have no idea why it worked. But this is what I did:

1) As I was unsuccessful booting to 2.6.20 or even 2.6.17 kernels I tried one of the older ones that were still hanging around the system: 2.6.15. This at least got me to gnome.

2) Then I ran

sudo dpkg --configure -a
sudo apt-get update

and 2 reboots later I had 7.04, which so far seems to run fine.

---

