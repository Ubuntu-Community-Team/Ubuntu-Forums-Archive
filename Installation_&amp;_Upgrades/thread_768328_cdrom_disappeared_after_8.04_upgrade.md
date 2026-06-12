---
title: "cdrom disappeared after 8.04 upgrade"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by scananza on 2008-04-26
Hello all,
I encountered a strange problem after upgrading my gusty box to the last 8.04 flavour:

I used to have my primary master ide cdrom drive bound to /dev/hda and everything worked just fine, reading, writing and everything.

Now /dev/hda is not there anymore, I only have a /dev/scd0 (a scsi emulation device, I guess) linked by a /dev/cdrom1. dmesg seems to correctly find the drive, at least I can read out its specs. I have changed fstab and program-defined preferences in order to switch from /dev/hda to /dev/scd0, but if I try to access the drive with /dev/scd0 I obtain nothing. The cdrom isn't even listed in nautilus-burner app or in any other burning software. If I put a cdrom or dvd inside and close the tray nothing happens (it used to auto-start the player in accordance with gnome removable device setup). It seems that my cdrom isn't seen by the high-level operating system layer.

Does anyone have the same problem?
Any clue about how to fix this?
It's kinda a pain not having the cdrom working ;^)

Thanx a lot.

---

### Post by jelofson on 2008-05-22
Hello,
Have you had a chance to look at your /etc/fstab file yet?
You will likely have to change it to read something like this:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

You could also create a symbolic link in the /dev folder from scd0 to cdrom
something like this:
cd /dev
sudo ln -s scd0 cdrom

Some of the applications out there look to /dev/hda for media rather than /dev/scd0. I had to change the defaults in VLC for example.

Hope this helps a bit.

---

