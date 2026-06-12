---
title: "New Unformatted USB Harddrive"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by mkaylor on 2007-01-24
I have PC that has one Sata HD that I'm booting 6.10 off of.  I purchased a second sata drive and installed it in a USB caddy because the machine doesn't have a second sata port.  How can I find this hard drive?  It's new and not formatted.  My ultimate goal is to make a mirror image of the main drive on this drive so I can stick in an identically machine.

It's not showing up on /dev/sda like a thumb drive does.  This is where I thought I would find it.


Thanks for the help.

Mike

---

### Post by logos34 on 2007-01-24
You've probably already checked this:
> System>Preferences>Removable Drives&Media Prefs

The 'Mount removable drives when hot-plugged' box should be ticked

[But then it isn't appearing probably because it's unformattted]

Does fdisk detect it?
> sudo fdisk -l

If not, does it show up in your BIOS?

---

