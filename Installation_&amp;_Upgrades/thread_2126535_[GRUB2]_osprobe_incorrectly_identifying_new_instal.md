---
title: "[GRUB2] osprobe incorrectly identifying new install"
date: 2013-03-17
forum: Installation &amp; Upgrades
---

### Post by MrAureliusR on 2013-03-17
So I have Ubuntu and Windows dual-booting on one hard disk, my primary /sda. This has worked fine and except for the odd little problem here and there (GRUB2 finding Vista as 'Recovery Environment' once and then never changing back, everything worked perfectly.

That is, until I added a new 160GB hard drive and installed Fedora. For some strange reason that I can't figure out, after successfully installing Fedora and rebooting, booting into Ubuntu and running grub-update, it added TWO new entries, BOTH Mac OS X, one 32-bit and one 64-bit. It is correctly identifying that hard drive as /sdc, and it has the correct partition, but that's where the correctness ends. Of course, it has set the boot options completely wrong (HFS+ as filesystem, for example, among many others) so now I can't get into Fedora.

So -- I know you're not supposed to, but I could manually edit /boot/default/grub and change the entries if I knew the proper flags, etc. However if there's a better solution I'm all ears. I've googled this a lot and never have I found a single other example of Fedora being identified as Mac OS X by GRUB2... :confused:

Thanks everyone!

---

### Post by darkod on 2013-03-17
Are you sure you don't have any OSX leftovers at all? Some small and possibly hidden boot partition?

The fedore boot commands should be easy to find on google. When you do, don't edit grub.cfg manually (by the way the menu entries are in grub.cfg not in /etc/default/grub). Instead edit /etc/grub.d/40_custom. In there you can make all custom menu entries that you want. Running update-grub will include these entries in grub.cfg.

EDIT PS. One reason for wrongly finding Mac partitions is if you had that disk in a Mac and then used it on windows. Mac uses gpt table and windows when writing a new msdos table doesn't delete the backup gpt table. For windows it doesn't matter since it ignores it (or can't see it, not sure what is true). But linux tools do see this backup gpt table leftover and are confused whether the msdos table or the gpt table is the correct one.

Make sure the partition table is good. If in doubt write a new msdos (or gpt as you wish) table with parted in terminal, it does it properly unlike windows. But that would mean reinstalling fedora after that.

---

### Post by MrAureliusR on 2013-03-17
Man, this is the weird part -- I have never owned a Mac, nor used that HDD in one. I literally just created fresh partitioning while installing fedora using gparted so I don't see how any artifacts could be left over...

I'll see if I can find the boot commands and go the 40_custom route. But how will I remove the incorrect menu options?

PS I actually did edit /boot/default/grub a few days ago and it DOES include the menu options, I fixed an incorrect menu option title in there and it worked after grub-update

---

### Post by darkod on 2013-03-17
You can't remove the incorrect entries unless you disable 30_os-prober (make it non-executable). But that will delete the windows entries too. So, first open grub.cfg and copy the windows entries into 40_custom, then disable 30_os-prober.

It's weird, usually grub2 os-prober is very good, it shouldn't detect these weird partitions.

As for /etc/default/grub it does include grub2 options but more like the default OS, the timeout, etc. I haven't edited it for the menu entries, but I haven't even tried to on the other hand. I always thought the scripts in /etc/grub.d/ are for that purpose.

---

