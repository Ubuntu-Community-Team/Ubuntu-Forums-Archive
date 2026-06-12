---
title: "Ubuntu installation made another Windows partition not bootable"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by nair on 2012-02-11
A few hours ago, I had a dual boot configuration sporting both (1) Windows 7 and (2) Windows Server 2008 R2.  I had some free space available on the hard drive--about 40 GB--so I performed an install of Ubuntu 11.04 x64 off of a CD I had.  I did the partitioning manually, and before I did the install, I saw a few partitions already in place:

[LIST=1]
[*]Partition 1: Windows System reserved partition (about 100MB)
[*]Partition 2: Windows Server 2008 R2
[*]Partition 3: Windows 7
[*]Partition 4: Linux swap partition (about 2 GB from a previous installation of Linux on this machine which presumably was not being used for anything recently, as there was no active, usable Linux partition on this machine within the last month)
[*](nothing/no partition - 40 GB of free space)
[/LIST]
I have gone through the installation of this exact distro of Linux on this exact laptop, so performing the actual install was nothing special or difficult for me.

Before I did this Linux install, I was previously switching between the two Windows partitions using the Windows bootloader (not GRUB).  After the Linux install was performed, as was expected, I was presented with the GRUB bootloader.  And then I discovered the problem--my Windows Server 2008 R2 partition was not available to boot from in the GRUB bootloader menu!

Where did it go, and how do I get it back?  Does the issue have something to do with my physical hard drive reaching its limit of active partitions (which I believe is 4)?  Should I have installed Ubuntu as a logical partition and not an active partition to avoid this problem (I never saw the option to do so in the manual partitioning screens during the install)?  If I have to erase or sacrifice the Linux partition to get back my Windows Server 2008 R2 partition back to being bootable, I can do that.

Additional information which may be useful:

[LIST]
[*]I can still see both the Windows Server 2008 R2 and Windows 7 partitions while booted into Linux.  I can navigate through them both and retrieve all data.
[*]Windows 7 is still bootable, as it is listed in the GRUB bootloader menu.  I don't know why Windows Server 2008 R2 got did not get preserved but Windows 7 did.
[*]This may not be a problem with the partitioning; this may be a problem with GRUB itself, and the way it is configured.
[/LIST]

---

### Post by darkod on 2012-02-11
If you select win7 from the grub menu, does another windows bootloader show offering options for 7 and 2008?

Grub will only jump to the windows bootloader files you had, and depends how it detects them, it might call it win7 in the menu. After you select it, it passes the boot process to the windows boot files which should offer you the choice of 2008 as before.

---

### Post by oldfred on 2012-02-11
It is not a grub issue but a Windows issue. Window only boots from the active partition or partition with the boot flag. Second installs of Windows litteral move all the boot files into the active partition, so the second install has no boot files for grub2's os-prober to find.

You may be able to copy/move Windows boot files, move boot flag and run repairs. Boot repairs by Windows is only to the active partition, but by moving boot flag you change active partition. Both Windows partitions do have to be primary for that to work.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by nair on 2012-02-11
> **darkod said:**
> If you select win7 from the grub menu, does another windows bootloader show offering options for 7 and 2008?

Grub will only jump to the windows bootloader files you had, and depends how it detects them, it might call it win7 in the menu. After you select it, it passes the boot process to the windows boot files which should offer you the choice of 2008 as before.

Ah, you are correct.  I should have tried to boot into the Windows 7 loader first before posting.  I assumed that was representing the OS, not the loader.  As you described, once I select the Windows 7 loader, then I am presented with the Windows loader which lets me choose between Windows 7 and Windows Server 2008 R2.

---

### Post by darkod on 2012-02-11
> **nair said:**
> Ah, you are correct.  I should have tried to boot into the Windows 7 loader first before posting.  I assumed that was representing the OS, not the loader.  As you described, once I select the Windows 7 loader, then I am presented with the Windows loader which lets me choose between Windows 7 and Windows Server 2008 R2.

This happens because as oldfred said above, windows combines the boot files if you have more than one install. So even if it wanted to, grub can't boot both of them directly.

---

