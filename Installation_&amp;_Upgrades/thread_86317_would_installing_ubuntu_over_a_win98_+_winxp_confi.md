---
title: "would installing ubuntu over a win98 + winxp configuration be a bad idea?"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by red.wooden.dog on 2005-11-04
hello

I've found lots of useful material on the subject of installing a linux distro to a computer with win98 or xp already installed, but how about both? Will I be able to use my win98, installed to c: (primary partition, naturally) and winXP, at e: (logical partition of the same disk) after installing ubuntu? The xp installation modified the master boot record, so that a menu shows up that lets me select the OS to boot. What I found out earlier was, that if I re-installed win98 on top of my current configuration, the boot menu would disappear, hence, rendering the xp installation unusable (though there may well be a fix for this that I'm unaware of .. but fixing this, of course, is not what I'm after).

so, fundamentally, I'm asking if (after the ubuntu installation) grub will give me a menu that allows me to boot any one of these 3 systems, without a glitch, without having to reinstall anything, which I'd really hate to do?

this is my first linux installation, so please bear with me ..!

thanks in advance

---

### Post by earobinson on 2005-11-04
if you follow the how to's it should be the same as installing with just the one os, (many people triple boot, so grub can handle it)

---

### Post by aysiu on 2005-11-04
Provided you have three separate partitions:

Windows 98
Windows XP
Ubuntu Linux

and you install Grub to the MBR (you'll be asked about this during the Ubuntu installation process)

Windows 98 and XP should both show up in the boot menu. If they don't, we can help you get them in there.

---

### Post by SickTwist on 2005-11-04
[QUOTE=red.wooden.dog]hello

I've found lots of useful material on the subject of installing a linux distro to a computer with win98 or xp already installed, but how about both? Will I be able to use my win98, installed to c: (primary partition, naturally) and winXP, at e: (logical partition of the same disk) after installing ubuntu? The xp installation modified the master boot record, so that a menu shows up that lets me select the OS to boot. What I found out earlier was, that if I re-installed win98 on top of my current configuration, the boot menu would disappear, hence, rendering the xp installation unusable (though there may well be a fix for this that I'm unaware of .. but fixing this, of course, is not what I'm after).

so, fundamentally, I'm asking if (after the ubuntu installation) grub will give me a menu that allows me to boot any one of these 3 systems, without a glitch, without having to reinstall anything, which I'd really hate to do?

this is my first linux installation, so please bear with me ..!

thanks in advance[/QUOTE]

If you do not currently have free (unpartitioned) space on your drive, Ubuntu can try to resize your partitions for you during the installation. Let me give you a couple tips if this is what you plan on doing:

1. **Defragment all of your Windows partitions before starting the Ubuntu install.** This will sort the data to the beginning of each partition and will result in your having a better chance of not corrupting anything. Which brings me to point two...

2. **Back up your data before installing Ubuntu.** Resizing/moving partitions is serious stuff. Ubuntu will try its best to protect your data but there is always a chance that something could go wrong. Don't put yourself in a position where you risk losing your stuff.

---

### Post by MacStew123 on 2005-11-08
> What I found out earlier was, that if I re-installed win98 on top of my current configuration, the boot menu would disappear, hence, rendering the xp installation unusable (though there may well be a fix for this that I'm unaware of .. but fixing this, of course, is not what I'm after).

[I][COLOR="Blue"][COLOR="DarkSlateBlue"][FONT="Verdana"]Umn...I actually have this problem and keen to find out how to fix it...I installed linux (impi) over xp and now can't get into XP...ideally, i'd like to remove linux from the drive completely and do a clean install for XP. Each time I try booting off the XP cd though (after formatting and partitioning drives), the boot screen automatically starts loading lilo...

it's driving me insane so any help would be appreciated.

thx[/FONT][/COLOR][/COLOR][/I]

---

