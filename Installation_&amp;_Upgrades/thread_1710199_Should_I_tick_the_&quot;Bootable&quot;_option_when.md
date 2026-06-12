---
title: "Should I tick the &quot;Bootable&quot; option when creating Ubuntu partition?"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by nrundy on 2011-03-19
When I install /root onto /dev/sda1 as a primary partition, do I need to tick off the "Bootable" option?

Currently, I have a dual-boot setup with Windows/Ubuntu and I noticed that the Windows partition has "Bootable" ticked but the Ubuntu install (under the Extended partition) does not. I'm going to be installing just Ubuntu (no Windows). Do I need the Ubuntu-only install (that will be on sda1 primary partition like Windows is now to have Bootable checked off?) What does the Bootable option configure exactly?

---

### Post by srs5694 on 2011-03-19
First, you probably should not create a separate /root partition. You *must* create a "/" partition (pronounced "root"), but /root refers to the /root directory, which is the root user's home directory. That directory is normally part of the root (/) partition, not a separate partition. I realize this terminology is confusing, but making a mistake on this score can be pretty bad, so you should try to be as precise as possible when communicating about these matters, and insist on equal precision from others, in order to avoid potentially disastrous miscommunication.

Second, the "boot" (aka "active") flag in the Master Boot Record (MBR) partitioning system you're using tells certain boot loaders, such as the standard DOS/Windows boot loader, which partition to boot. If you install GRUB to the MBR, this flag becomes irrelevant. Old versions of Windows wouldn't boot with this flag absent, but new versions are fine without it, and Linux is also fine without it. If you install GRUB in the Linux boot partition, then you should probably set the boot flag on that partition and clear it on the Windows partition (unless you want to use a Windows boot loader as your primary boot loader). GRUB 2 (used by recent Ubuntus) often refuses to install in a partition, though; you may have no choice but to install it to the MBR.

Unfortunately, libparted-based tools (including GParted and the Ubuntu installer's partitioner) use the "boot flag" terminology is a completely different and incompatible way on GUID Partition Table (GPT) disks. On these disks, libparted reports the EFI System Partition (ESP), which is a key part of booting an EFI-based computer, as having the "boot flag" set. This has absolutely nothing to do with anything remotely resembling the MBR boot flag, though, which has led many people (myself included, many moons ago) astray. You should *not* set what libparted-based tools identify as the "boot flag" on any GPT disk, except for an ESP.

It appears from your screen shots that you've got an MBR disk, not a GPT disk, so you can probably ignore my last paragraph, at least for now; however, MBR is doomed to go the way of the Dodo before too long, so libparted's unfortunate terminology blunders will become important soon, which is why I mention it.

Overall, the safest approach, for both MBR and GPT, is to leave "boot flags" alone and install GRUB in the MBR. (On EFI-based computers, GRUB won't actually install to the MBR, but at least as of the Ubuntu 11.04 alpha 2 version, the check box to do that is present in the installer.)

---

