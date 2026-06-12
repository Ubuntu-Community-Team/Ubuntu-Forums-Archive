---
title: "dual booting winxp with linux using xp bootloader"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by Tonglebeak on 2005-06-18
I've been reading around about how to dual boot linux with winxp, but I'm worried about the chance of failure regarding this.

I want to dual-boot xp with linux, leaving xp as default since this is a family computer, and they're more inclined to use windows.

[http://www.highlandsun.com/hyc/linuxboot.html](http://www.highlandsun.com/hyc/linuxboot.html) is the tutorial i took the most interest in. In it, it says to edit the boot.ini file by adding "C:\boot.lnx="Linux"" to the boot.ini file. The thing is, my boot.ini doesn't look like it would hold that (winxpsp2). Here's my boot.ini file:

[php]
[boot loader]
timeout = 30
default = multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS = "Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
[/php]

Hopefully you can see where I'm coming from on this one.

Wouldn't it actually makemore since just to add this:

[php]
multi(0)disk(0)rdisk(0)partition(whatever lucky number linux gets)/="Linux"
[/php]

and not screw around with the boot sector?

I've never done this before (Mandrake, which I tried a while ago, automatically set up a dual-boot, but it was default, not windows).

Anyone who has done this before, could I get some advice here? I don't want to end up losing everything to a format because I can't boot anymore (although I'm well aware of fixmbr with winxp, which hopefully could save my ass from any bootloader problems).

---

### Post by diebels on 2005-06-18
No need to worry, but always make backup.

You don't need to use ms bootloader for making msOS default. GRUB(the default bootloader for ubuntu) can have whatever default. Can have pretty colors and nice splash image too.

You can even convert msOS splash image to xpm, and use that for GRUB splash. :eek:

Using ms bootloader is a pain in the a**. You need to do the thing with dd after every little kernel security update.

---

