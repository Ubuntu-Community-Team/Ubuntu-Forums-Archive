---
title: "System Cmdr, 6.10, and XP?"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by dme7 on 2007-01-30
G'day, all ...

I'm building a multi-os system, using the following configuration as the hardware base:
* Dell 1.4GHz P4, 
* 1GB main memory
* 2 18GB SCSI drives
* 2 122GB IDE/EIDE drives

I have XP-Pro already loaded onto the first SCSI drive, and I've installed SysCmdr-8 as the boot-loader.  When I initially installed 6.06 on the first IDE drive, even though the installation claimed to have succeeded, SysCmdr said that the "linux" partition wasn't bootable.  6.06 didn't make any comments about GRUB during the installation.

I'm in the middle of installing 6.10 right now, and it's just said that GRUB would be installed on hd0, which I'm pretty sure is the same drive that XP (and SysCmdr) were installed on.

Anybody out there been down this path before?  Yeah, right -- stupid question.  So ... anyone care to tell me what I've got in store for myself?  Somebody want to warn me about potential potholes and roadblocks?  Pretty-please?

Ta,
doug

---

### Post by dme7 on 2007-01-30
Not sure what the explanation is, so if somebody wants to take a swting at it, please do --

I went into the BIOS setup, and I changed the boot-device order (*not* the "boot sequence", ie., "first try the floppy, then the CD, then the harddrive", not that) -- it initially had SCSI-0 followed by the BIOS followed by SCSI-1, and I moved BIOS to the top; when the system restarted, I saw a boot-menu I'd never ever seen before, with 6.10 at the top, and XP at the bottom ... I selected 6.10, and the sucker booted.  SysCmdr never came up.

"What's it all mean, Mr. Natural?"  [Any Zappers out there?  What's the proper comeback?]

So, except for the requested explanation, consider this case closed.

Ta.

doug

---

