---
title: "GRUB &quot;Reloc Offset is out of segment&quot;/&quot;mismatched names&quot;"
date: 2012-09-24
forum: Installation &amp; Upgrades
---

### Post by cfmackey on 2012-09-24
Working on a Gateway 832GM for my buddy.
Previously he was running Xubuntu, which I had set up for him on his old rig. I thought I'd segue him right into the same routine, and so I ran a Text-install of 12.04. After I completed the install (completely fresh disk by the way, and I wiped the HDD; solo install), GRUB gave me error: "Reloc offset is out of segment"

So I searched the forums and came up zilch. All of the repeats of this problem were on DualBoot setups with Windows, where backup/restore software was messing with the MBR. But my install is solo, and this was occurring on first boot.

So after like three hours of trying every forum solution on the net, I decided to try a few other distros. Here were the distros I tried, and the GRUB errors:

All of these were tried with both ALT installers and LiveCD installs.
Ubuntu 12.04: "Reloc offset is out of segment"
Ubuntu 11.10: "Reloc offset is out of segment"
Xubuntu 11.10: "Reloc offset is out of segment"
Jolicloud 1.2: "Reloc offset is out of segment"
And finally, Sabayon 10 (x): "mismatched names"

The last install (Sabayon) was interesting because I was under the suspicion it was only a Debian problem. Seems Gentoo-based systems give me the same issue.

I'm lost. I have no idea where to go from here, I'm open to any suggestions. PLEASE HELP ME LQ!

---

### Post by cfmackey on 2012-09-24
Forgot to mention that I had the same version of Xubuntu running on this box before this install attempt.

---

### Post by oldfred on 2012-09-26
If you have Ubuntu or any related version installed run the BootInfo report and post link.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by cfmackey on 2012-09-26
Turns out the problem was drive titles. The HDD had been set to cable select, and in the slave position, but the Optical Drive was also configured to slave. I reconfigured the jumpers on the drive and everything's fine now.

Thanks for the help.

---

