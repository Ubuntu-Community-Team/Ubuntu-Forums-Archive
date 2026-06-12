---
title: "Buffer I/O error = sign I should try alternate CD?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by raydar on 2007-04-21
I'm trying to install xubuntu 7.04 from the CD image I just downloaded, on an old Dell Latitude laptop, Pentium II 300MHz, 192MB RAM, which currently has a full WinXP Pro installation on it (plus the command-line-only barebones Win95 intallation it came with, in a dual-boot setup).  

This laptop has two "bays," one for a battery and one for a floppy drive or CD-ROM drive--but it it's not possible to have *both* a CD-ROM and a floppy drive simultaneously; only one or the other may be inserted because the second bay is battery-only.  I suspect that may have something to do with the nature of the errors (quoted below) I get when I try to boot from the xubuntu installation CD.

When I boot from the xubuntu CD (or an ubuntu CD--I've tried both, with same result), (1) I get the splash/menu screen, and (2) when I choose the first option, the kernel seems to load successfully and (3) I get the progress-bar screen for 30 seconds or a minute; then (4) the screen goes black and I get the following over the next several minutes, after which I can type at the prompt but the system goes unresponsive after I press enter:

--- snip ---

[  208.468000] Buffer I/O error on device fd0, logical block 0
[  246.572000] Buffer I/O error on device fd0, logical block 0
[  312.604000] hdc: drive not ready for command
[  437.656000] Buffer I/O error on device hdc, logical block 0
[  437.656000] hdc: drive not ready for command
[  442.084000] BUG: soft lockup detected on CPU#0!
[  442.660000] hdc: drive not ready for command
[  502.660000] Buffer I/O error on device hdc, logical block 1
[  etc.      ] Buffer I/O error on device hdc, logical block 2
[   	       Buffer I/O error on device hdc, logical block 3
[              Buffer I/O error on device hdc, logical block 4
[              Buffer I/O error on device hdc, logical block 5
[              Buffer I/O error on device hdc, logical block 6
[              Buffer I/O error on device hdc, logical block 7
[              Buffer I/O error on device hdc, logical block 0
[              Buffer I/O error on device hdc, logical block 1
. . . 
[              Buffer I/O error on device fdc, logical block 0
[              Buffer I/O error on device fdc, logical block 0
[              Buffer I/O error on device fdc, logical block 0

BusyBox v1.1.3 (Debian 1:1.1.303ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

--- snip ---

The laptop's floppy drive is "NOT INSTALLED" according to the BIOS settings, so I'm not sure why there's an "fdc" issue; and I can boot Windows just fine from the laptop's hard drive, so I don't understand why there should be an "hdc" issue.  The laptop does have an ethernet connection, but I don't know of any way to do a first install without booting from CD.  Do the above error messages look like the sort of thing one would get when the "alternate installation CD" should be used, even though this laptop does meet the 192MB requirement for a standard xubuntu installation?  Anyone have any other ideas?

Thanks for any help!

---

### Post by jsnelli2 on 2007-04-21
For Ubuntu it says that the alternate cd is for under 256 MB of RAM.  I ran the alternate cd on my laptop---has 1GB of ram.  Updated the system fine.

---

