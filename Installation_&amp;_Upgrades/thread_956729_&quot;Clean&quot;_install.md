---
title: "&quot;Clean&quot; install"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by Jim Lewis on 2008-10-23
Right now I have an XP/Ubuntu dual boot system.

Windows is beginning to work even more oddly than normal and I find myself not needing (or wanting) it.

My question:

If I put the install disk in the drive and opted for the full, Ubuntu-only installation that scrubs the hard drive, will that get rid of the dual-boot GRUB program and leave me with a log-in straight to Ubuntu?

I vaguely recall reading here (or somewhere) that getting rid of GRUB was next to impossible -- but I think that was from someone wanted to ditch Ubuntu.

If I'm stuck with the existing GRUB, how do I get rid of the 14 (or so) Ubuntu options, that pop up now?

Hopfeully, the answer to my first question is YES and the rest won't need to be answered.  :)

---

### Post by Pumalite on 2008-10-23
Just install and choose 'Guided>Use Entire Disk'. You'll end up with a brand new Grub and no problems.

---

### Post by jnorthr on 2008-10-23
no your system will always need some version of grub (grand unified boot loader) even with a single version of the kernel. On my fresh insall of 8.10 yesterday, did a full install on a brand-new drive. My version of grub runs directly into the only version of the kernel without asking 'which version'- so i suspect yours would too.

We only see a choice when more than one choice exists, and if there is only one, then there is no choice.

---

### Post by Pumalite on 2008-10-23
Do not choose 'Automatic Login'

---

### Post by Jim Lewis on 2008-10-23
> **Pumalite said:**
> Do not choose 'Automatic Login'

OK, I won't, but Why?  :)

---

### Post by Pumalite on 2008-10-23
Later, you'll have a choice in case a kernel doesn't boot.

---

