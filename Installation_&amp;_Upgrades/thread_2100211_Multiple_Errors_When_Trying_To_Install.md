---
title: "Multiple Errors When Trying To Install"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by 122jdh on 2013-01-01
I have an IBook G3 (everymac.com/systems/apple/ibook/specs/ibook_600_2.html)
and I want to install Ubuntu (10.04 desktop PowerPC). The medium I use never shows up when I start up holding option so I try to load it from Open Firmware, but every time I try and install it I get all of these errors: "block0 is bad can't open", "load size is too small", "can't OPEN enet:bootp" "no specified file-name"....etc,etc. Ive been using a microsd 2GB with adapter in place of an actual USB drive, and a CD-RW instead of a CD-R so i can rewrite to it. I've even tried installing MintPPC 11 and Fedora with the same errors. Can someone help me out?

---

### Post by 2F4U on 2013-01-01
How did you burn the iso to CD? You probably know that it is not sufficient to write the iso as data disk.
Another possibility: bad download or bad burn. Did you verify the checksum of the downloaded iso file? Did you burn at the lowest possible speed?

---

### Post by 122jdh on 2013-01-01
I opened the ISO with Cyberlink Power2Go 8. The program gives 2 ways to burn an ISO: clicking on the ISO opens it in ISO Viewer then gives the option to burn it (option I used), or open the program and select Copy Disc and then select Burn Disc Image. Did not verify the checksum of the file. The way I chose to burn only gave me the option of 4x speed, the maximum. There is no lower speed the way I burned the disc.
I have UltraISO also, so I'll burn the disc the other way and with UltraISO and burn it at a lower speed, and see how it works out.

---

### Post by gordintoronto on 2013-01-01
As a comment, Ubuntu 10.04 has less than four months before it will no longer get security updates. You might be better off with Xubuntu or Lubuntu 12.04.

Oh, this might be significant: if the RAM has not been upgraded, the computer can't run Ubuntu or any of its derivatives. The original spec was 128 MB, which is not enough.

---

### Post by 122jdh on 2013-01-01
The amount of RAM in my system is 256 MB.
And i found the ubuntu-12.04-desktop-powerpc.iso file so im going to use this.

---

