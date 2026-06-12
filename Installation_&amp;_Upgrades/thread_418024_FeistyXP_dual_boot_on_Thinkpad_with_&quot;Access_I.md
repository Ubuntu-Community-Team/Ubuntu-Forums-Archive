---
title: "Feisty/XP dual boot on Thinkpad with &quot;Access IBM&quot; support"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by OriginalGabriel on 2007-04-22
Ok, this is eating me alive!

I installed Ubuntu on a 20G partition only to find that, since Thinkpads have their own bootloader in order to deal with their hidden system restore partition, GRUB trashed the MBR (I kept getting an "Error 18").  I tried multiple ways to recover my system and finally ended up having to use an old DoD hard drive scrubber (a lovely 6 hours ordeal).

I dug around and found some means to deal with the situation and opted for loading GRUB onto the linux partion (via the "alternate" install CD) and then using 'dd' to make a boot image and having the Windows NTLDR list that via the boot.ini however, for whatever reason, I could not install GRUB to any partition via the "alternate" install CD; I continually received "Install Failed" errors.

Has anyone succesfully pulled off a dual boot of XP and Ubuntu on a Thinkpad while still leaving the "Access IBM" "Rescue and Recovery" option intact?

---

