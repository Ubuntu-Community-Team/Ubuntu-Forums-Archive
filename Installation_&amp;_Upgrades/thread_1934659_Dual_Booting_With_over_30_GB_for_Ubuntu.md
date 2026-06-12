---
title: "Dual Booting With over 30 GB for Ubuntu"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by epichacker1 on 2012-03-02
I have recently done a Wubi install of ubuntu, and selected 30 GB. However, 30 GB is the maxiumum amount of space Wubi can supply, so I uninstalled ubuntu and burned the Disc Image File to a disc, hoping to install with over 30 GB. When I did this, I clicked "Use Ubuntu alongside Windows 7," but that did not supply enough hard disc space. (I want to dual boot) Since I was familiar with hard disc partitioning, (I have been with Windows for a long time) I decided to use the "Something Else" option. Here is what I did:

I selected "New Partition Table" (This is not a VM, but a disc install)
I selected OK.
I selected Add, then changed partition size to 35,000 MB
I set the root partition (I selected / )
I selected the new Partition and installed from it.

Thinking that I had just made a 35 GB partition for Ubuntu, and would install it on that, I finished the Installation. I am new to Ubuntu, and when I tried to dual boot by pressing the space bar after my BIOS loads up, nothing happens. Windows 7 was erased from my computer completely, and I am not particularly happy about this. I plan to install Windows again, and install Ubuntu again with more space for it, but why was Windows 7 uninstalled, and is there any way I can use the "Something Else" option without overwriting Windows?

Thank you, 

(P.S. I am extremely new to Ubuntu)

---

### Post by oldfred on 2012-03-02
When you said new partition table it should have said that erases entire drive as it creates a new partition table not just a new partition in the existing table.

I always use gparted from either the liveCD (USB now for me) or a separate download of the gparted liveCD/USB so I have the latest version. Then I know exactly were my partitions are.

Often the installer has issues and only presents a disk erase option when Windows has used all four primary partitions in the MBR partitioning scheme. Windows 7 typically uses two partitions one boot and one system. The vendor then uses 2 partitions, one is the image of the hard drive as purchases since they do not give install disks anymore and another is misc files that seems to be more just to use the last partition and make it difficult to install anything else.

---

### Post by epichacker1 on 2012-03-03
Thanks, I should have noticed that, I guess I wasnt paying attention.

---

