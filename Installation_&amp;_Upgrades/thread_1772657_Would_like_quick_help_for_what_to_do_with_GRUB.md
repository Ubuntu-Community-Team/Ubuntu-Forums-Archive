---
title: "Would like quick help for what to do with GRUB"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by BKbroila on 2011-05-31
I have Win7 and Ubuntu currently dual-booting and with the upgrade to 11.04, I'm confused as to what I should do.
There's a list of options, but what am I supposed to select under my circumstances?
[LIST]Install the package maintainer's version
Keep the local version currently installed
Do a 3-way difference between the available versions
Start a new shell to examine the situation
[/LIST]

Thanks

---

### Post by Quackers on 2011-05-31
If you have made changes to your old grub menu it may be best to keep the local version currently installed (otherwise you may lose your changes).

---

### Post by oldfred on 2011-05-31
I have found for all system files, that it is best to do your own backup and save those files you manually edit. I try to copy each file I manually edit into a folder in /home so my backup of /home includes those files.  Often if you do not accept the system maintainers version something does not work. It is easier to accept the system maintainers version, then go back and edit that file using your backup as a reference.

If you do not accept grub changes it will not offer to boot the new kernel, but will keep your changes. You then have to manually add more changes to get it to boot the new kernel. And if you cannot get a first boot then you do not have a chance to do a sudo update grub to automatically add the changes.

---

