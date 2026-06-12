---
title: "Dual boot instructions for Ubuntu/Windows 7"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by qiet72 on 2011-08-24
Hi,

Some people seem to have problems getting dual boot to work with Ubuntu and Windows 7.  Some articles suggest installing grub to the ubuntu partition and copying the first sector of the partition to a file and then using together with bcdedit.

Well, thats history now as grub2 seems to support Windows 7 directly.
So:
- install windows 7 and leave partition space for an ubuntu installation
- when windows 7 installation is complete, install ubuntu on the empty partition

If after the ubuntu installation, Windows 7 is not recognized by grub, then do the following steps at the command line:

sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-pc # mark /dev/sda as the boot area for grub

That's it.

qiet72

---

### Post by sikander3786 on 2011-08-24
Most of the times, Grub does detect Windows 7 and automatically configures itself to boot Windows successfully.

If it doesn't, there are probably more than one reasons why it didn't and thus, more than a single workaround that would work in different situations.

Purging grub packages like that isn't recommended for new users. If they manage to remove the packages by running the first command and at the second one they realize they don't have Internet connectivity, they are in big trouble.

Also while re-install Grub, they can accidentally install it to a partition instead of the MBR of the drive, or if they have got more than one HDDs in their PC, they can install it to the MBR of another drive which would obviously lead to other troubles.

So if anyone suffers situations like this, they must start their own thread and post the output of [bootinfoscript]("http://bootinfoscript.sourceforge.net"). If they know what they are doing, they probably won't read this thread ;)

---

