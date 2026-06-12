---
title: "Failed upgrade (again)"
date: 2024-11-15
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2024-11-15
sigh. 
by now I should know better than to accept an upgrade offer. 

this latest on seems to have fail and I am (on restart) getting:
error: symbol 'grub_disk_native_sectors' not found
entering rescue mode.... 
grub rescue>

what do I do from here?

---

### Post by Rubi1200 on 2024-11-16
Sounds like something went wrong during the upgrade and somehow the GRUB files are mismatched or corrupted.

Is Ubuntu the only operating system on the machine?

---

### Post by yancek on 2024-11-16
Upgraded from which version to which newer version?  If Ubuntu is not the only OS installed, what others might you have and which handles the booting with Grub?  Did you get any warning or error messages during the upgrade?  What upgrade method did you use?  Did you use apt and a terminal or the Software package manager?

---

### Post by briandu2 on 2024-11-16
@pjstock as @yancek and others have stated. You need to tell the story.
What was my config? (Before it went wrong)     [i.e. Ubuntu 20.04 and also windows (or not)]
Upgrading from Ubuntu 20.04 to 22.04 or whatever?
Do you have a USB bootup stick? (If not I use Ventoy as a bootup usb - I have used it for years and it is great - but there are others)   I means you can get a bootup into the ISO.

No, you should not have lost your data.
IF you can bootup from usb you can reinstall your original OS version (do not format the drives), however it is more complicated if you also have windows.   See why we need the info

Please update

---

