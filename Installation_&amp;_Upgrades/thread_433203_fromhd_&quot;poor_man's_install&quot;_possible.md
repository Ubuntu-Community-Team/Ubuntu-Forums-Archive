---
title: "fromhd &quot;poor man's install&quot; possible?"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by clsgis on 2007-05-04
Knoppix lets you run a "live" system from an ISO image on a file system on hard drive, instead of wearing out your CD drive.  The boot command is "[FONT="Courier New"]knoppix fromhd=/dev/sda4[/FONT]" and it looks for a file knoppix.iso in the root of the file system on that partition.  They call this "the poor man's install."

I copied the .iso to [FONT="Courier New"]ubuntu.iso[/FONT] on an ext2 file system on a flash drive. adding fromhd=/dev/sda4 to Feisty's kernel command line but it doesn't do anything different.

I searched for a complete list of ubuntu's boot arguments (like Knoppix' "cheatcodes" file) but couldn't find one.  Is there a reference for that somewhere?

I've got some friends who would probably switch from Windoze to Ubuntu if they could run it from an iso image file on their [FONT="Courier New"]C:\[/FONT] drives for a while.  But they're not going to adjust partition tables, nor run from CD.  It's poor man's install, or they're stuck on MSFT.

---

