---
title: "Error: /dev/md1: unrecognised disk label.. First time software raid setup."
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by Coatezy on 2011-07-01
Hi,

I'm currently trying to setup a server using a HP Proliant Microserver with 4 WD20EARS. I am setting up in raid 5. Now I had used Ubuntu for a good 2-3 years but this is the first time tackling something like this.. I normally find the answers I need within the forum or elsewhere but this has stumped me. I will try and explain what I have done the best I can.

My partitions consist of

1mb biosgrub

1gb /          <raid1

8gb for raid   <raid5   (lvm used for /usr /var /tmp /home all formatted as ext4)

xxtb (remaining space) <raid5 formatted as ext4


Install completes fine but once booted and run sudo parted -l I receive this message near the end

Error: /dev/md1: unrecognised disk label 

md1 is my last partition in the list above where I plan to store everything. It is formatted as ext4 and mounts as /zdrive.

It mounts fine and I can use it but the error above worries me that I'm missing something during the setup process. Most other posts with this error messages result in grub or boot issues but mine seems to start up and run fine. From the info I have found on the net the label should possibly be gpt!? But how do I label it?  :(

Would really appreciate any help! Please let me know if you need any more info. :)

---

### Post by psusi on 2011-07-01
The error is because /dev/md1 is not a disk and does not have a partition table.  You just shouldn't be running parted on it.

By the way, you don't need to have a separate raid1 /; it can be in the LVM on the RAID5 too.

---

### Post by Coatezy on 2011-07-01
Aaaaaah brilliant so I dont actually have any issues?! :) Ooooops,  my first time and never had to look at stuff like this before.. Also thanks for the tip with / on LVM.. Thanks for your help! Going to reinstall now and add / to LVM.. :p You made me happy! :)

---

### Post by Coatezy on 2011-07-01
Hi, Just wanted to say thanks again! Reinstall with a 1mb bios grub, a RAID5 containing /, /usr, /var, /tmp, /home and another RAID5 for my storage.. Works perfectly and looks even cleaner. :P

---

