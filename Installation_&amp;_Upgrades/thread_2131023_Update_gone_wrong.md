---
title: "Update gone wrong"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by s0563764 on 2013-03-31
Hi,

installed xubuntu 12.04 64-bit on my laptop which dual-boots win 7. Was working fine, bu did some software update for xubunutu.
Restarted computer but the network manager software "did not have permission" to work, nor did the shut down function. After some tweeking I got internet and shutdown back, but I've lost the ability to install/update software.

[ATTACH=CONFIG]240781[/ATTACH]

And I get the issue above if I try.

I tried to reinstall xubunutu, but because of the way grub is working I can't boot the CD. Any ideas?

---

### Post by schragge on 2013-03-31
Open a terminal (press **Win**+**t**), and run:
```

sudo apt-get clean
sudo apt-get update
sudo apt-get --reinstall install indicator-messages

```

---

### Post by s0563764 on 2013-04-01
Thanks that did the trick, any ideas regarding booting from CD in the future?

---

### Post by black veils on 2013-04-01
you choose the boot device from BIOS/UEFI, not sure how it works for the latter though. with BIOS you can either press a key while booting the computer to go into the 'setup', or press a key like F12 to show a menu of bootable devices for one-time selection.

---

