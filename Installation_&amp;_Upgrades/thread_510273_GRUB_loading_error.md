---
title: "GRUB loading error"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by adam820 on 2007-07-26
Hello all,

I've run into a rather strange error with Ubuntu 6.06 LTS. I've installed it numerous time, and actually installed it once in a working fashion on this machine once, but now I am getting the error. The error is after POST and disk check, when it's supposed to say "Loading Grub.." or whatever the text may be, it fills the screen with the word GRUB, in a fashion such as below:

GRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUB
GRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUB
GRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUB
GRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUB
GRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUB
GRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUB
GRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUB
GRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUBGRUB


It looks like it's continually writing the word "Grub" to the screen, as the last line is flickering at a rapid rate.


On to the machin:
It's an IBM IntelliStation M Pro, used to be a Win2K Server, and we're looking to turn it into a Moodle Server at where I work. It had a Hitachi Deskstar 41GB/Maxtor 38GB combo IDE, but the Maxtor died yesterday, and was replaced with a similar Hitachi, so it is now a 41GB/41GB non-RAID setup. I had installed Ubuntu 6.06 LTS successfully to the Hitachi/Maxtor combo, but after it died, I wanted to do a fresh and clean install, and it's now the third installation and each time it does this after a successful install.

I have done manual partition edits, as well as cleaning the disk and letting Ubuntu set my partitioning scheme. Booting in from the LiveCD I have tried to reinstall GRUB, but it tells me it cannot find the drive...

Any help is vastly appreciated.

Thanks,
AdamD.

---

