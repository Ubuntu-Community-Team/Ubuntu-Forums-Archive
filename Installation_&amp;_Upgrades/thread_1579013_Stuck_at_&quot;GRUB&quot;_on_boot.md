---
title: "Stuck at &quot;GRUB&quot; on boot?"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by luciusthecanine on 2010-09-21
Hi all, I'm new to the forums and Linux. I've been a Windows kiddie since Win3.1 and have decided to make the change to Open Source after experiencing Ubuntu on the computers at my local library two year ago.


I've tried to install both 9.10 and 10.04 (one at a time, not dual-boot) via Live CD.

Booting after install gives me the standard Manufacturer logo (HP), then I get "GRUB" text with a flashing Cursor.

I figured this was a prompt, but I can't enter any text.

I figured something got missed during install, so I re-installed and manually set up partitions for each directory, making sure they all have enough space allocated to them.

Same result.

I'm confused as to why the system stalls at this point. 
My research here has found some similar issues remedied by reinstalling Grub to the MBR or running "fsck" command on the Root partition from a terminal on the live CD. 
I will be trying this tonight and I'll post the results.

Does anyone else have suggestions as to a possible fix?

---

### Post by luciusthecanine on 2010-09-27
I decided to start from scratch.

Installed XP on the 6Gig drive and Xubuntu on the 40gig.

Swapped cables so 40Gig drive was on Master end.

Booted up straight to XP - no GRUb screen.

First thing that came to mind: BIOS is booting from 6Gig as Primary Boot Drive regardless of cable selection.

Rebooted, hit the BIOS setup and sure enough - 6Gig was primary HDD.

Changed to 40Gig as Primary Boot Drive.

Rebooted

BEAUTIFUL GRUB SELECTION SCREEN!

Loaded Xubuntu 10.04 - took awhile due to lack of Memory. I'll fix that in time. :grin:

Ran some 218 updates. :grin: :grin:

Haven't touched it since... lol I'm a busy guy apparently.

I guess all this took was a little common sense and general knowledge of how the Boot Process works.

---

