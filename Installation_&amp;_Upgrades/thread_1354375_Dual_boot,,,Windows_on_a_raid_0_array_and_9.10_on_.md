---
title: "Dual boot,,,Windows on a raid 0 array and 9.10 on a separate hdd"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by Turbocharged on 2009-12-13
So I have run into a problem that simply google searching (like I have done on my past linux installs) hasn't helped me with...figured it was finally time to join up.

I currently have Windows 7 64-bit running on two hard drives in a 160GB RAID 0 array and recently purchased an extra 500GB internal drive for storage. Since I have more space than I really need now, I wanted to throw Ubuntu 9.10 64-bit on a 50GB partition on this third drive.

Problem that I ran into...well maybe not a problem, but it worried me...is that when I put the image disc in and go to install linux, the installer doesn't see my windows raid array and thinks that my computer currently has no operating system. I'm sure I could install just fine from there onto the new hard drive, but I don't know what that would do to my windows setup.

Any ideas?

---

### Post by nelfin on 2009-12-13
Is there anything wrong with just removing your two drives in raid from your computer and then installing onto the third drive from the LiveCD? If anything goes wrong, you won't have borked anything because the drive was unformatted anyway (and the LiveCD can't use it's evil Jedi mind-powers to wipe your windows install).

After that, make sure that ubtuntu and grub can find your array and then you *should* just run update-grub from the ubuntu install (provided that grub2 is your main flagged bootloader) to get it to chain into win7's loader (via os-prober magic).

---

