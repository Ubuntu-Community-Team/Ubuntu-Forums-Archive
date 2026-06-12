---
title: "Clean up  \boot or move it to main partition"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by midden on 2011-02-16
I recently installed 10.10 on my desktop (on which I occasionally dual boot Win7). I thought that I might install \ as a LVM so I partitioned \boot out onto its own 92 Mb partition. In the end I did not install \ as LVM and my \boot is full (which causes problems when trying to install new packages or upgrade the kernel). Since I don't really need \boot on its own partition now, I have two questions:

1) How can I safely move \boot to the 46 Gb \ partition?
2) If #1 is not possible, how can I routinely clean up my boot directory?

Thanks for your help.

---

### Post by quixote on 2011-02-17
Not sure about most of your questions, but one solution might be to enlarge the /boot partition.  Or is there some reason why you can't?  Boot off a liveCD or liveUSB, and use gparted under the System>Admin menu to resize that partition.

---

### Post by oldfred on 2011-02-17
A few versions ago, I thought I wanted a separate /boot and just moved the files to a new partition and reinstalled grub. But I then decided I wanted a grub partition so I moved them back and reinstalled grub. That was just before grub2 and now I do not use grub partition.

You should just have to move all the files to the /boot partiton in / (root). Besure to preserve permissions & ownership (root). And you will then have to reinstall grub or grub2. 

I think I used rsync with these parameters:
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress

Like this from a backup script:
rsync -auvP /home /media/backup

House cleaning:
Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by midden on 2011-02-26
Thanks for the suggestions! Oldfred has the most thorough example, but I took a short cut (for better or worse). Here is what I did:

1) sudo cp -r /boot /tmp/.  [[I suppose I should have used rsync here]]
2) sudo umount /boot
3) sudo mv /tmp/boot /.
4) sudo vi /etc/fstab    [[here I used a "#" to comment out the line for /boot]]

I am still left with a small partition that won't really get used, but the convenience of having boot on / outweighs that small cost.

Thanks again.

---

### Post by Hedgehog1 on 2011-02-26
ARRGG!!  A whole 92 meg partition unused! That is almost 1/10 of a gig?!?!?! :p

You know what - I am such a Nerd I would move partitions around to get it back.

I envy your self control to leave well enough alone.

*I wish I could...*

:KS

---

