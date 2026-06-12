---
title: "Installing on USB flash disk"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by g0ng on 2007-07-23
Hi there.

I want to install feisty on my 2GB flash disk. I read some tutorials where you have 2 partition on FAT with the live CD contents, and one ext2 for data.

I did it but when I install a programm (such as apache) and I restart the changes aren't there.

What I want is -if possible- to have a full linux (meaning I can install programs, store my files, etc) on my flash disk. So whenever I plug it I can boot and have a ready workstation for my work (web development, so I want to have apache, php, mysql etc).

Can I do this?

Thanks

---

### Post by pxwpxw on 2007-07-23
It should be possible to simply install feisty on a usb 2gb flash drive (using an installer rather than a copy of desktop live cd), assuming you have an intel pc or mac that can boot usb., but 2GB might be a bit small.
The U3 ReadyBoot (Vista) usb jetflash drives have a small dos boot partition builtin, so linux and grub can be installed on the remaing partition on the drive in the normal way, and booted via the dos boot. Seems to work for a MacBook (intel mac) as far as booting, but I have not yet tried a complete install. On the other hand these usb ready boot drives have been around for a while, so maybe this is not news, but it was to me when I tried it yesterday.
Edit:
Tried it today on a MacBook (intel). The readyBoot Vista stuff is not useful, just a separate bit of ROM with vista stuff, just use it as a standard USB stick, as **Michel Roelofs** says below.  For a compact system, I use a server install (no graphics, ) about 350 MB.
Handy for rescues etc.

---

### Post by Michel Roelofs on 2007-07-24
Hi,

Some time ago I've installed Debian on a usb flash disk. I've simply treated it as a normal disk: removed the fat partition, created a single ext3 partition, installed Grub and finally installed the distribution itself. It just works fine. I assume this would work equally well with Ubuntu. Just be careful to not put the drive in a windows computer, because it then may ask you to format it.

As a side note: I've kept the distribution small, < 400MB. During startup, I create a ramdisk (tmpfs), copy the complete filesystem into this ramdisk, and then run everything from ram. Then I can safely remove the usb drive.

---

