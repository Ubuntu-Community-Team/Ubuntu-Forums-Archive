---
title: "Why are there 3 same Ubuntu options in rEFIt menu?"
date: 2014-09-13
forum: Installation &amp; Upgrades
---

### Post by jason121 on 2014-09-13
[COLOR=#000000][FONT=Arial]I install rEFIt to make dualboot menus on Mac. And, after I installed Ubuntu 14.04 LTS, why are there 3 same Ubuntu options in boot menu? Just like that below...[/FONT][/COLOR]

[LIST]
[*]Boot EFI\ubuntu\MokManager.efi from EFI
[*]Boot EFI\ubuntu\grubx64.efi from EFI
[*]Boot EFI\ubuntu\shimx64.efi from EFI
[*]Mac
[*]...
[LIST=1]
[*]What are the 3 options different?
[*]May I customise to only one option for Ubuntu?
[*]When I select any one of Ubuntu options, I still need to select which action I want
[LIST]
[*]Ubuntu
[*]Check disk
[*]...
[/LIST]
[/LIST]
Why I can't login Ubuntu since I've already selected to launch Ubuntu in boot menu?
[/LIST]

---

### Post by oldfred on 2014-09-13
They are not the same.
MokManager is the secure boot key editor.
grubx64.efi is standard boot
shimx64.efi is for secure boot.

All but grubx64 may not apply to a Mac as that is more for the newer PC systems with the newest UEFI that implements secure boot. Mac has an older UEFI that does not use secure boot.

I would think you could remove shim & mokmanager files from efi partition, but do not know how to update rEFInd or if it will update itself when files are deleted.

---

