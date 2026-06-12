---
title: "Ext3 Filesystem Corrupted After Installing 7.04 Server Beta (Feisty Fawn)"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by glutinous on 2007-03-29
Hi,

I am not sure whether this is a problem with the software or my own hardware.

I did a fresh install of Feisty Server Beta on my computer last night. As usual, I use aptitude after the initial install to only install ubuntu-minimal, and the programs I usually use (including X.org, but none of the desktop environments unless a package depends on them). I also have a Fujitsu 2.5" SATA drive that have all my file backups directly plugged into the computer (so not an external drive), which I copied over (about 40 GB). I then left it running Transmission (a bittorrent client) over night to get a few downloads.

This morning, the root filesystem had been remounted read-only because of an 'invalid entry' Ext3 error or something. Sorry I can't remember the exact wording. I was told to run fsck, so I did a reboot and let fsck do its thing. The run fsck manually error came up, so I did ('fsck /dev/sda1'). And I get question after question about clearing inodes and things (which I just answered yes to). Judging by the endless questions, I am guessing I have lost too much data to bother trying to continue using it. :)

The system still boots okay, but there is no way I can tell what has been lost, so I am going to reinstall.

I ran the memory test for about half an hour this morning and no errors came up. And my hard drive has been working without any problems up until when I wiped and tried installing Feisty yesterday.

Could this be related to the Ext3 corruption bug that was only just patched for in one of the 2.6.20 release candidates?

I will runs more longer memtest86 tests tonight, and try a fresh install again, and see what happens. I might use the desktop CD this time. Not sure, but maybe the server install does something a bit different to the desktop one...

But I am just wondering if anyone else has had this problem, and would have any idea what is wrong?

My computer is a modest one. :) An AMD AthlonXP 2700+, 1 GB DDR400 RAM, 80 GB Seagate SATA 3.5" harddrive (and also another Fujitsu 100GB SATA 2.5" harddrive plugged in at the moment, with my backup files), and an ABit NF7 series motherboard.

-Steven

---

