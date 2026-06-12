---
title: "[SOLVED] Detecting SATA hard drive as SCSI?"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by Doc Hoss on 2008-05-13
My install of 8.04 seems to be detecting my SATA hard drive (Western Digital...can't remember the model) as a SCSI drive, listing it as "sda0" instead of "hda0".  Is the drive lettering "sda" an indicator of SCSI, or am I just confused?  It doesn't really seem to be causing any serious problems...yet...but I'd like to figure it out before it becomes an issue.  If it is an issue, anyone know how to fix this...or even if I should?

The SATA controller is built into the motherboard (Abit AW8-MAX), if that matters.

---

### Post by logos34 on 2008-05-13
that's normal.  Scsi, sata and externally hard drives are designated as 'sda', 'sdb', etc.  Even some ide/pata drives show up as sd_, depending on the storage controller

---

### Post by Doc Hoss on 2008-05-18
Sorry I'm a little slow responding.  But thank you for your info.  I was worried about that, but now I'm good with it.  :)

---

