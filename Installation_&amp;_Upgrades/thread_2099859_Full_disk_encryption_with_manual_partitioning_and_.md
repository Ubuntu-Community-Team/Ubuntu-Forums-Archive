---
title: "Full disk encryption with manual partitioning and no LVM"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by Thoralyon on 2012-12-30
Hello there, it seems I have a problem thats related to the discontinuation of the alternate cds.
A few years back I installed ubuntu from the alternace cd onto a harddrive that looked like this:
sda1 windows boot
sda2 windows
sda3 /boot
rest is all physical volumes for encryption
sda5 /
sda6 swap
sda7 /home
[...]

I reinstalled windows, and now i want to reinstall ubuntu ontop of the old partitions.
However it wont let me.

I get several errors, 
First it complains about the unencrypted swap space
and then it complains about a missing root directory, however I can either select a filesystem and a mountpoint (as in sda3 - ext4 - /boot), OR a physical volume for encryption. However I should be able to select both (as in sda5 - physical volume for encryption - ext4 - /).
How does one go about doing that? There are no options and I cannot advance because it wont let me due to an unassigned root partition
I found a post mentioning something like this:
sudo cryptsetup luksOpen /dev/sda6 crypt1
which seems to work, but I do not know where to go from there, since the installer seems unaffected

If I simplz click on the encrypted drives and enter the password something happens (XGB encrypted drive chances to the name I assigned it the last time I installed) but I dunno how to mount them

Anybody else experiencing something similar or am I the only one using this feature?
Any help appreciated, thanks

---

### Post by Thoralyon on 2012-12-31
I forgot to add that I do not have the option to install ubuntu alongside windows, only the "other"-option, probably due to the fact that all the space is already assigned.
Will changing this help me?
I don't want to repartition if it afterwards turns out to be a useless move

---

