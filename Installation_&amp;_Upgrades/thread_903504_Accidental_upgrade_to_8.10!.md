---
title: "Accidental upgrade to 8.10?!?"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by daltonlaffs on 2008-08-28
Hello forum peoples,

I had to enable an intrepid (development) package source to get my hands on a few development-level packages. However, I forgot to remove it when I ran an unattended update and came back to find that my computer had been 'upgraded' to a prerelease of 8.10, a dev release.

Bootup and shutdown are terribly slow now, and a few programs have lost stability. Is there any way for me to safely downgrade to the most recent version of 8.04 without losing anything else?

Please help, I hate this :(

---

### Post by Sef on 2008-08-28
The only way to downgrade would be to reinstall 8.04.

---

### Post by daltonlaffs on 2008-08-28
Sef: So, my only option is to lose all my files and configurations?

I had to pull a LOT of strings to get my system up and running. My wireless required a newly-compiled driver and my speakers required a few difficult changes to configuration. That and I'm terrible at restoring these .tgz updates :P

---

### Post by forger on 2008-08-28
> **daltonlaffs said:**
> I had to pull a LOT of strings to get my system up and running.

Should've thought about that before touching the apt sources and upgrading? :)
I could help you if it was a couple of packages, but since you went on and upgraded *everything*, I wouldn't want you to go on a wild goose chase, hence the only real (and definitely working) solution is to reinstall ubuntu. Sorry :?

edit: How about doing a backup everytime you do something extreme that you don't know how it's going to end? [Clonezilla]("http://www.clonezilla.org/") has saved me several times

---

### Post by daltonlaffs on 2008-08-29
Okay,

Sorry it took so long to reply... but Forger, about downgrading just a few packages...?

The major feature that broke with the update is CD/DVD burning. None of the burner programs work now. Is there a library or two I should downgrade?

---

