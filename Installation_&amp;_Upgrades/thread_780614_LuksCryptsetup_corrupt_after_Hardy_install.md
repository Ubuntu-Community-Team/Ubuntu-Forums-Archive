---
title: "Luks/Cryptsetup corrupt after Hardy install"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by watermark on 2008-05-03
I'm pretty sure my data is gone, but I figured I'd alert the masses anyway.

I had a 2nd harddrive that was encrypted with the cryptsetup/luks setup (tons of tutorials out there.)  I do a clean install of Hardy on the 1st harddrive, and now I can't unlock the encrypted 2nd drive.

I installed cryptsetup and modprobed the needed modules (aes errors, but someone else already filed a bug report for that one.)  Hardy named my drives different (it was hdc, but now it's sdc)...So after figuring that out, I tried to luksOpen the drive...it says it's not a luks partition.  I run "cryptsetup isLuks /dev/sdc", and it says it's not a luks partition.

Thinking that the versions of cryptsetup may not have been compatible, I booted to the Feisty live cd...checked the drive with "cryptsetup isLuks"...and it says it's not a luks partition.

So, it's looking like somewhere in the clean install of Hardy...my 2nd harddrive fubared.  It may have been a coincidence, or the Hardy setup may have mucked with it.  Some of the data is irreplaceable, but at the same time, not that important.

So just in case...My advice would be to disconnect encrypted drives before installing Hardy.  If it wasn't Hardy, then it was a crazy coincidence....or I have no clue what I'm talking about.

---

