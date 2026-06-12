---
title: "Ubuntu 9.04 Alternate Install LILO error"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Demosthenesaus on 2009-12-07
I need to install an encrypted filesystem on a netbook – I have used the alternate install CD on another laptop and the netbook in question successfully before (MSI Wind U100 Intel Atom).

Now when I get through to the install LILO stage it reports an error has occurred and can not proceed. This is the first time I recall seeing a LILO step, I thought it was all GRUB now, and do not recall any LILO steps when getting an encrypted filesystem running on the netbook, and a laptop before.

The only thing I can think of is that this time I included Swap in the encrypted logical volume but that works fine on the other laptop.

Any thoughts? The system boots ok, can get in to XP and select a Ubuntu 9.04 option, but now it just sits on the splash screen with the scanning graphic moving back and forth, when under ideal circumstances it would prompt me for the passphrase, which it did work previously when I installed without Swap as I forgot that I need to go through the secondary step of a Logical Volume Manager over the Encrypted Partition, and split that in to two encrypted sub partitions of root and swap.

I currently have GRUB and XP booting ok.

---

### Post by Demosthenesaus on 2009-12-07
Could using Ext4 on /boot and the encrypted /root partition have anything to do with this error? After reading of the Ext4 issues, I'm very concerned about data loss and will go back to Ext3 on my next attempt anyway.

---

### Post by Demosthenesaus on 2009-12-07
The only thing I can think of is using ext4 for /boot and throughout, but I thought I used ext4 on the working laptop with no problems.  I will try ext3 this time around.

I wonder if an aborted installation has caused problems, but it *boots* fine, it seems to get as far as the /boot partition and then stalls.

Is there any way to just start completely from scratch - say wipe a partition and restore the default Windows XP bootloader and start from scratch?

I need to use 9.04 as 9.10 is broken on the MSI Wind U100.

---

### Post by Demosthenesaus on 2009-12-08
Fixed!!!! In 9.04 at least, use EXT3 NOT EXT4 for /boot

---

