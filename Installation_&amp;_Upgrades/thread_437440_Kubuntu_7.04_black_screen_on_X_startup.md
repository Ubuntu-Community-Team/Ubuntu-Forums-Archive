---
title: "Kubuntu 7.04 black screen on X startup"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by Tweenk on 2007-05-08
I have some weird graphics issue whie trying to boot Kubuntu 7.04 Feisty from Live CD. Originally the boot failed with the familiar "/bin/sh: cannot access tty" message, but the "modprobe piix" workaround worked for me. I boot without the quiet and splash options. When the X server starts, the screen goes blank (but the monitor still has signal). This also happens in safe gaphics mode. Additionally, when I try to use some other resolution than VGA, even the console messages fails to show up. Switching to another terminal doesn't work, blank screens everywhere.

The graphics card is reported in Windows 2003 Server (currently installed system) as Matrox Millenium G450 Dual Head DVI. The LCD panel is connected via the DVI output. There are 2 SCSI drives 34GB each, one of which is the main boot device, and one 298GB IDE drive (don't know if it's SATA or PATA), all NTFS. There are also 2 DVD-RW drives, but only one of them is bootable, and a floppy.

I can't figure out how to change the xorg.conf, because I have to break=top to use modprobe piix, and this file isn't present then. Passing break=top at the beginning of the command line and break=bottom at the end results in the tty message. Another strangenesses are that I get an NMI after HP Linux Printing Server loads and that there are some horizontal glitches on the screen while the kernel is loading.

I'll check out the LTS version as soon as it downloads to check if this is a Feisty-specific issue.

I can boot from Knoppix 4 Live DVD in default resolution, but I get awful graphic glitches (hard to describe, looks like some horizontal lines from two different v-resolutions are interleaved, happens at the bottom and ca. in the middle of the screen)

---

### Post by Tweenk on 2007-05-09
Checked Ubuntu 6.06 Dapper LTS - works with no problems, so this is definitely a 7.04 issue. However, sometimes the message "mount: function not implemented" pops up during boot or shutdown. No NMIs at boot this time.

Will also check the latest Sabayon and Ubuntu Edgy.

---

### Post by Tweenk on 2007-05-10
Sabayon works, and I even managed to get Beryl working, albeit with some issues (probably that's the junky graphics card's fault).

---

