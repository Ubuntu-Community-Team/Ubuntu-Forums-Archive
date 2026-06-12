---
title: "GRUB won't install on Thinkpad T43 [resolved itself...]"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by drwoland on 2005-08-14
I'm trying to install Ubuntu on my new IBM ThinkPad T43. Here's what I did:

I used PartitionMagic to partition the drive. I resized the Windows partition to allow space for linux, and kept the IBM Restore partition untouched at the end of the drive. I booted onto the CD, formatted the appropriate partitions to be JFS and SWAP and went on.

GRUB refuses to work. I tried installing it into the MBR, but then discovered that all the guides tell you not to. Then I tried installing it onto /dev/sda5, which is my boot partition (100 mb JFS) and that didn't go either, it just says it couldn't be installed, but won't even tell me why. I tried sda6 as well, which is my / and that didn't do me any good either. What's the deal?

Edit: Strange... just went back and tried it again and when it asked if I wanted to install into the MBR, I just said yes and it worked... vverrry odd... I did change my PreDesktop security level from Secure to Normal, but it was refusing to work at first on Normal too... I don't get it... But just booted Windows and it worked fine, so I guess I'll go play with ubuntu now?

---

