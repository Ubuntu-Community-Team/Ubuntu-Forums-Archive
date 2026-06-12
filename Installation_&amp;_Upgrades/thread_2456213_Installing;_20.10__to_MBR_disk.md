---
title: "Installing; 20.10  to MBR disk"
date: 2021-01-07
forum: Installation &amp; Upgrades
---

### Post by holiday2 on 2021-01-07
I have an old laptop [COLOR=#242729][FONT=Arial]Asus G74Sx originally Windows 7 upgraded to Windows 10

[/FONT][/COLOR]```
[COLOR=var(--black-800)][FONT=Consolas] Disk /dev/sda: 256.17 GiB, 275064201216 bytes, 537234768 sectors[/FONT][/COLOR]
 Disk model: Crucial_CT275MX3
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos [COLOR=var(--black-800)][FONT=Consolas] Disk identifier: 0x1db352ee[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

The Ubuntu installer does not recognize the Windows installation.

In Linux I have tried a straight dd transfer of the iso  to the USB drive.

I tried in Windows using Rufus to write a MBR USB bootable disk but this fails with a kernel panic about `init` not found.

I want to keep the Windows partition because this is the only Windows machine I have. 2 desktops and 2 laptops all Linux. Then this one 

Is there anyway to make this happen. 

Eventually I want to move it all to SSD. Is it possible to clone the Windows drive to a SSD and create a gpt partition for the Ubuntu installer. 

What options do I have?

[/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-01-07
You can install Ubuntu in a MBR drive like you always did, and dual-boot it with Windows in BIOS mode like you always did.
I does NOT depend on the USB drive. DD or any tool that uses it (almost all except Rufus with default option) always produce a USB installer that can be booted either in BIOS or UEFI. Rufus by default doesn't use DD and the required options BIOS/MBR or UEFI/GPT must be selected before "burning" the ISO.

If you can boot to a live session the USB was made correctly. That it later doesn't identify NYFS Windows partitions is a totally different and unrelated issue.
Any Windows 8 or newer has the Fast Startup "feature" enabled by default and that must be disabled for dual-booting. And, of course, before attempting to install the second OS (Ubuntu) you should shrink the main Windows partition to make room, preferably from Windows itself using Windows native tools. Reboot and check Windows boots correctly before proceeding.

A few details you need to learn first.
One is that the partitioning types are about drives, not partitions. A single drive can't be MBR ("msdos") and GPT at the same time.
GPT is always preferable but you can't use it in your case because you intend to dual-boot with Windows and Windows strictly requires MBR for BIOS and GPT for UEFI. So, because you have an old BIOS machine - apparently - you must install all in a MBR drive, exactly as it is now.

However, if your laptop is new enough to have UEFI instead of BIOS in spite of having originally Windows 7 installed in Legacy mode, a mode that emulates the behavior of old BIOS and that was typically used for the late Windows 7 offerings, then you can and should take advantage of UEFI and install both OSes in the proper mode. So...

If you intend to replace that drive for a SSD later then much better to reinstall both OSes. Although cloning and entire drive including the MBR where the bootloader resides is possible that is strongly NOT recommended, particularly for someone who doesn't yet understand the basics as shown above. And assuming it's really UEFI then you should install in that mode in the new SSD with GTP.

---

