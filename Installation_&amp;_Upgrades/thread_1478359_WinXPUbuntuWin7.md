---
title: "WinXP/Ubuntu/Win7"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by hauard on 2010-05-09
I installed Winxp and  Ubuntu with no big problems. So I wanted to try Win7.

I partitioned my HD in 4 partitions:
On the first theres XP
On the second theres ubuntu
On the third theres Win7

What I dont get is that in grub/menu.lst XP is hd0,0, ubuntu is hd0,4 ??
And I can't seem to get grub to boot win7, I can't figure out what hd0,X it's on

I have tried everything from hd0,1 to hd0,8 in menu.lst
getting error 22 no such partition on everything, except one NTLDR missing on hd0,2.

After installing win7, when I booted hd0,0, where XP was located, I got the win7 bootloader.
Ran EasyBCD in win 7 and wiped it clean, and bootet XP as usual.

---

### Post by squab on 2010-05-09
windows has its own boot-loader which probably will show both your XP and win7. Your best bet to get all three running at once is to get grub to boot your windows boot-loader and your windows boot-loader to boot your XP/Win7.

Considering your windows 7 booted from where you thought your XP boot-loader was, you probably already have it setup. I would look at how to configure the windows boot-loader because it might be setup to auto boot win7. At the very least it would show you whether its detecting xp.

---

### Post by hauard on 2010-05-09
Yeah, the Win7 bootloader showed Win7 and "other older windows OS"
I removed that bootloader, because I wanted grub to handle it all.
I just cand find out where Win7 is located (hd0,X) ??
The old bootloader just said Win7 on C: and XP on D:

---

### Post by squab on 2010-05-09
The windows drive letters mean absolutely nothing. One thing to try, run > sudo update-grub which will rescan for operating systems and update grub. [For more info.]("https://wiki.ubuntu.com/Grub2#Automatic Entries")

---

### Post by hauard on 2010-05-09
Running update-grub getting this output, still no Win7 in menu.lst
EDIT: I commented out the old Win 7 option in menu.lst before running update.

```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-18-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

I wonder why I get NTLDR missing on hd0,2, cuz before I removed the win7 bootloader, 7 booted just fine. EDIT: Assuming 7 is on hd0,2.

---

### Post by hauard on 2010-05-09
Getting this output from fdisk
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       12453    48829567+   5  Extended
/dev/sda3           12454       18190    46080000    7  HPFS/NTFS
/dev/sda5            6375       12453    48829536   83  Linux

```

That confirms that 7 is on hd0,2 right?
Back to the NTLDR problem?

EDIT: Or maybe I should set sda3 to be bootable too !? wtf

---

### Post by hauard on 2010-05-10
While reading online, trying to figure this out, I seem to understand that Win 7 does not utilize the NTLDR ? This makes my problem even more mysterious..

---

