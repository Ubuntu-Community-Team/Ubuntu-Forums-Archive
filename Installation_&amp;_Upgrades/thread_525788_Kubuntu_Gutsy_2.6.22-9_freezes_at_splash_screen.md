---
title: "Kubuntu Gutsy 2.6.22-9 freezes at splash screen"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by Genesius on 2007-08-14
OK, let's start with the background: I was a happy Kubuntu user, merrily using Feisty, when I thought "Why not upgrade to Gutsy and see what's new?" Backed up my personal files to my Windows disk, just in case (I may be a relative n00b to Linux, but I'm not a *total* n00b!) and ran kdesu "adept_manager --version-upgrade". It downloaded all the files, then crashed halfway through installing them. It was late, so I figured I'd deal with the carnage the next day.

Next day, and one totally borked Linux drive. Downloaded the Gutsy liveCD in WinXP, tried booting with it but it kept giving me errors. Rather than burn a new one, I reloaded Feisty and decided to give the upgrade manager another try. Another crash, but with repeated "sudo aptitude install -f" and "sudo dpkg --configure -a" I managed to get everything installed.

Rebooted, tried to log in with the 2.6.22-9 kernel & it just sat at the splash screen. Rebooted, logged in with the 2.6.20-16 kernel and got in just fine. Went into Adept and tried reinstalling all the 2.6.22-9 packages with the same result. This time when it froze I hit ctrl+alt+F1 to get to the text, and here's whet I get:

```
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/ ep tag 0 cdb 0x0 data 4096 in

```
That repeated three times, then I get this:
```
Check root=bootarg cat /proc/cmdline or missing modules, devices cat /proc/modules ls /dev

ALERT! /dev/disk/by.uuid/<long uuid> does not exist. Dropping to a shell

/bin/sh: can't access tty; job control turned off.
```

The "<long uuid>" part is just because I didn't feel like writing down the uuid. Hopefully it's not vital info.

Any ideas? Or do I just redownload the Gutsy CD and hope the new one works?

---

### Post by Genesius on 2007-08-15
Wow. Got the brain trust stumped.

I've posted this on answers.launchpad.net as well, no reply there either.

Oh well, if all else fails I'll wait until the beta is released & see if running update manager fixes it.

---

### Post by Genesius on 2007-08-22
James from answers.launchpad.net came through! Posting the answer here in case someone else with a similar problem stumbles across this thread.

> try doing this:  edit this file 
/etc/initramfs-tools/modules, and add these lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

after editing:

sudo update-initramfs -u

that should set up your hard drive to 'standard' hda drives, instead of
setting them up as scsi (sd*)


---

