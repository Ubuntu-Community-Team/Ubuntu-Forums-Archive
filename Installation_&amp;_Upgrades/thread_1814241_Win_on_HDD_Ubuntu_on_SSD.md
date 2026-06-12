---
title: "Win on HDD Ubuntu on SSD?"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by pbeesley on 2011-07-29
Just ordered a bucket load of PC parts for a new build YAY :P

However, was just wondering the best way to have it set up? 

I've only ordered a 30gb SSD and was planning on installing windows 7 on my 2tb HDD and just ubuntu on the SSD (with /home on the HDD) is there any tricky way of doing this?

I was planning on;

Plug everything in
Install win 7 on HDD partition
Install ubuntu on SSD (with Grub)
Bask in the glory of my new PC

---

### Post by YesWeCan on 2011-07-29
"Bask in the glory of my new PC" :D

I set up something similar recently. You probably want your SWAP partition on the HDD too. So your HDD will have Windows partition(s), a linux /home partition and a linux SWAP partition. For best flexibility, put the linux partitions inside an extended partition.

I'd be inclined to install Ubuntu first. Run the live CD and use Gparted to configure the HHD:
1. Empty space at beginning of disk for Windows
2. Extended partition containing a logical partition ext4 for home and another for swap.
Then install Ubuntu and tell it to use the HDD partitions for /home and swap.

Then set your bios to boot HDD first. Install Windows to the HDD empty space.
Then set bios to boot SSD first. Boot Ubuntu and run [COLOR="Navy"]sudo update-grub[/COLOR] to add Windows to the Grub boot menu.

Then bask away.

---

### Post by pbeesley on 2011-07-29
ah ok, 

I was planning on running GPARTED from a live CD and setting up all my partitions before doing anything so

HDD
[LIST]
[*]WINDOWS INSTALL
[*]/HOME
[*]/SWAP
[*]SHARED STORAGE DRIVE
[/LIST]

SSD
[LIST]
[*]UBUNTU INSTALL
[/LIST]

Any other reason for the install ubuntu first suggestion?

---

### Post by YesWeCan on 2011-07-29
Sounds like you know what you are doing already. Sometimes Windows 7 uses 2 partitions, one for boot. I'm not sure under what circumstances it decides to do this. That's the only vague reason I have for installing Windows to an empty space rather than a pre-made NTFS partition. And making all your linux-only partitions logical keeps primary ones free for possible future Windows purposes. The order you install things in doesn't matter much.

---

