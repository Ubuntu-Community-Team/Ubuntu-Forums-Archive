---
title: "Can't install breezy on iMac G3/233"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by ebeyer on 2006-06-07
OK.

So now I'm trying to install breezy on my iMac G3/233. I think I asked it to erase the whole hard drive, an 80 Gb I installed several months ago. The installer created two partitions and installed the operating system without any errors. It popped out the installation CD and reset the iMac.

On reset, I get the yaboot greeting (Welcome, version 1.3.13 ...) and press ENTER. It says:

Please wait, loading kernel.... (long wait)
/pci@800000000/mac-io@10/ide@200000/disk@0:3,/boot/vmlinux: Input/output error
boot:

Anything I put at this point comes back with "loading kernel" and then nothing.

Where did I mess up?

More to the point, what can I do about it?

I went back and I tried installing and completely erasing the hard drive. The stage 1 installation seemed successful, as before, with no errors. The system resets itself, placing me ultimately in front of the 'boot:' prompt. If I hit enter, 'Linux' or 'old' I get "input/output error". If I try again, the system stops responding.

Am I doing something wrong? Is this install salvageable?

I can boot up into breezy live, but the OS there cannot access any of the new partitions I have created. The disk utility seems unable to enable the partitions either. So it seems as though I won't be able to change any of my configuration files or do anything useful with the system I just installed.

Any guidance at all will truly be appreciated.

EB

---

