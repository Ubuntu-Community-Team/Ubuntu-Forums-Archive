---
title: "How to add a kernel parameter in Grub2"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by bobnutfield on 2010-04-16
Hello Everyone,

I have not dug into Ubuntu for almost a year now (Since Jaunty, really).  I am trying to come to grips with Grub2, but have just now encountered it in Lucid.  I am having a terrible time with the graphics chipset, and it may well be that Ubuntu cannot be used on this computer (an older laptop with the dreaded Intel 82845G graphics chip).  There are a number of older bug reports that it is unsupported, but some success in more recent versions.

Anyway, one suggestion has been to add i915.nomodset=1 to the kernel boot line.  Now, this was a cinch in Legacy Grub, but I have been reading Grub2 wikis and tutorials for two days now, and I know about the config files, but I cannot find anything which tells me specifically how to add a parameter to the kernel boot line.

I should know this, I know, but I could use a little point if someone wouldn't mind.

Many thanks in advance

---

### Post by bobnutfield on 2010-04-17
OK, didn't realize this one would be so hard to tackle.  I know that it goes in /etc/default/grub, but I just wanted someone to guide me as to which line it goes on and whether to use quotes, single ticks or just the entry.  This does not seem to be shown in any of the guides for Grub2.

Any replies are appreciated.

---

### Post by oldfred on 2010-04-17
[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

Even thought the instructions say to use one I think it may be the other and be sure to run sudo update-grub  after any changes:

[LIST]
[*]***GRUB_CMDLINE_LINUX*** 

[LIST]
[*]If it exists, this line imports any entries to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. This is similar to the "altoptions" line in menu.lst 
[/LIST]
[*]***GRUB_CMDLINE_LINUX_DEFAULT=***"quiet splash" 

[LIST]
[*]This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". The entry "acpi=off", if required, would also be an option entered on this line.
[/LIST]
[/LIST]

---

