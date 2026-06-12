---
title: "boot-repair stuck on applying changes"
date: 2022-07-23
forum: Installation &amp; Upgrades
---

### Post by god0901 on 2022-07-23
**&#8203;Ubuntu 20.04.3**
After an unexpected automatic update of Windows11, there is no ubuntu option in my boot priority.
Therefore, I turn to a software called boot-repair in order to fix the grub.
This is my URL (paste from boot-repair): [Ubuntu Pastebin]("https://paste.ubuntu.com/p/7R9GncDCTW/")
Everything went on quite well. But right after I clicked the "**Recommended repair**" button,
**the boot-repair stuck on the very first step:**
[B]Now applying changes. This may take a few minutes...
[/B]I had been waiting for about few hours, but nothing changed.
Therefore, there is nothing I can do except posting new thread.
Could anyone help me? 
Great thanks!

---

### Post by tea for one on 2022-07-23
Sometimes, unbeknown to the user, Windows updates reset UEFI settings to default.
Can you double check the UEFI settings such as :-
Secure boot is disabled
Drive is AHCI not RAID

Also see if Fast Start Up has been re-activated within Windows itself.

---

