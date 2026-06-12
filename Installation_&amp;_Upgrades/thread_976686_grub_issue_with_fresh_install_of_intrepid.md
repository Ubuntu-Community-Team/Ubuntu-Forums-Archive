---
title: "grub issue with fresh install of intrepid"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by glennric on 2008-11-09
I had already upgraded via update-manager to intrepid, but I wanted to see what a fresh install of Intrepid looked like.  So I created a new partition on another hard drive and installed Intrepid to that partition, keeping my old root partition intact.  The install went fine and it installed grub and rebooted.  After the bios grub starts to load and gets to "Loading Stage 1.5" or something like that and then hangs.

I booted to the live cd and installed grub from the old root partition and it boots fine.  I tried reinstalling grub from the new partition, and it hangs again.

After looking closer at the files in the boot partition I saw that the *stage1_5 files were are different on the new partition than on the old.  The ones on the new partition were the same as those in /usr/lib/grub/i386-pc, but the ones on the old partition were the ones from Hardy, and hadn't been overwritten in the upgrade.  I tried copying the old files into the boot directory on the new partition and then installed grub from there and then it booted fine.  So it seems that these new stage1_5 files shipped with Intrepid's version of grub are faulty, or at least they don't work with my computer.  I quickly made a backup of the old stage1_5 files just in case these files get overwritten in the future.

Has anyone else experience this?  How could Intrepid get shipped with such a major flaw.  Anyone with a computer like mine that tries a fresh install will not be able to boot at all.

---

