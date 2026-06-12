---
title: "update-grub not working?"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by Collywobbles on 2010-07-22
Hi,

I have upgraded from 9.10 to 10.04 but I'm still using Grub1 as I came from 9.04.

Anyway, during the upgrade I kept my original menu.lst file when prompted as I have a Windows XP boot option that I wanted to keep. I have read that this means your kernel won't be updated - and indeed mine wasn't.

The new kernel files (vmlinuz-2.6.32-23-generic) are on my machine in the /boot directory. uname -r currently shows 2.6.31-20-generic.

From what I've read you should just need to run update-grub manually and it will install. However, I have done this but it isn't upgraded. It doesn't modify my menu.lst or anything.

Output for update-grub:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-23-generic
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

So it says its updating menu.lst but there is still no entry for 2.6.32-23? Am I missing something?

Thanks for any help.

---

### Post by kansasnoob on 2010-07-22
There's a known upgrade issue:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version)

I personally find their explanation there a bit difficult to understand :)

I prefer just renaming the old menu.lst to something like "boot/grub/menu.lst_OLD" and then running "sudo update-grub" again.

That should create a new menu.lst, and then I can just copy-n-paste the Windows entry from the old one to the new one, being absolutely certain to place it below the line:

### END DEBIAN AUTOMAGIC KERNELS LIST

Then I make all of the other needed tweaks like timeout, show menu, etc with "startupmanager". Are you acquainted with Startup Manager?

---

### Post by Collywobbles on 2010-07-22
Thanks kansasnoob!

Deleting the menu.lst worked for me.

---

