---
title: "In Ubuntu 15.04: &quot;There is not enough room on the disk to save ...&quot;"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by tapasray on 2015-05-06
I have installed Ubuntu 15.04 on a Sony Vaio with 1.6 gb memory and 320 gb hard drive alongside Windows 7 Starter, which was the pre-installed when I purchased it. Error messages like the one below keep popping up when I try to download something:

"There is not enough room on the disk to save /tmp/Obnzn5Oj.bin.part.
Remove unnecessary files from the disk and try again, or try saving in a different location."

Restarting the machine temporarily solves the problem, but it returns after some time.

A screenshot of the disk partitions is attached.

Please help!

---

### Post by plucky on 2015-05-06
Your / partition is 17.24G and 16.37G is used, which leaves 899.5M space left.

Try ```
sudo apt-get clean 
sudo apt-get autoremove
``` to clear some space or you will have to increase your partition.

You could move some data off your /home to one of the ntfs partitions.

Good Luck

---

### Post by tapasray on 2015-05-06
Thanks, @plucky! Trying.

@plucky   Thanks again. Done, but it was a "long and winding road."

1. Your codes worked fine.

2. Tried to shrink the NTFS partition right next to ext4 and merge the freed-up space with the latter. Failed.

3. Read that booting G-parted from USB stick was required. Failed to create bootable stick with Startup Disk Creator. All files seemed to be copied but still kept getting an error message.

4. Switched to Windows 7. Did part of the job with MiniTool Partition Wizard Free. Could not take final step, i.e., merge freed-up space with ext4.

5. Came back to Ubuntu and opened G-parted again. Merging worked smoothly.

---

