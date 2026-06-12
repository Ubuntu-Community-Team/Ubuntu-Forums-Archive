---
title: "Raid 0 is not mountable after reboot."
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by AugustStorm on 2010-01-07
Hello, I am new to the forum and haven't been around linux for some time. :D I currently am setting up an htpc running Karmic. The problem I am having is getting my Raid 0 to be mountable. My raid is not my boot partition, but is for data storage.
 
My setup is a zotac motherboard with three sata connectors. I have a 300 GB drive, my eSata port, and my DVD attached to these. In the PCIe expansion slot I have installed Syba 2 port Sata PCIe 1a card using the Sil3132 sata II host chipset. Off of this I have 2 1.5Tib Hdds that I am setting up as Raid 0. During the boot I enter the chipset BIOS and establish this as a Raid 0.
 
When I install Karmic it sees the Raid and my 300 GB drive so I install to the 300 GB Drive and everything works fine. I am able to boot to the Hdd and run the OS. I then installed GParted and setup a partition on my RAID as GPT since I want one large partition of 2.78Tib. I then Format it through GParted as ext4 and I am able to mount and access it. I then reboot the system, and can no longer mount the filesystem. What I found interesting is If I reopen GParted I can then mount it. I traced it down to the fact that the until I access GParted the Block Special Device (sil_bgabagabaedd1) does not appear in /dev/mapper. Everytime I reboot I need to go into GParted to restore the Block Special Device then it is mounted. I think I am missing something in the raid setup as to why it is not being retained. What have I missed? What do I need to do to retain the Block Special Device? Is there a boot config setting?

Edit: I did further research and found that if I do kpartx it will appear just as gparted, but on reboot vanishes.  I found something similar at this thread but not comfortable in updating dmraid: [http://ubuntuforums.org/showthread.php?t=1369224&highlight=fakeraid+gpt](http://ubuntuforums.org/showthread.php?t=1369224&highlight=fakeraid+gpt)
I think it is related to gpt and I will try to use a smaller partition to see if the behavior changes.

---

### Post by mfdc1969 on 2010-08-12
AugustStorm,

I am considering purchasing a Syba RAID card using the same chip-set and am curious - did you resolve your problem?

I hope to have a similar set-up with a separate SATA drive, connected to mobo holding the OS and home directory, and then using the RAID card to hold a couple of specific folders which I will mount in my home directory ... or something like that!

Any advice you can offer would be greatly appreciated!

Michael

---

