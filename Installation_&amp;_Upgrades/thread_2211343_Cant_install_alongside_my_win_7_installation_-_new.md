---
title: "Cant install alongside my win 7 installation - new type of MBR wont allow"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by josh44 on 2014-03-15
this isnt like, a generalized problem Ive ever had in the past, done tons of installations from slackware to almost everything else... Its just this PC has some sort of different MBR pre-installed than anything used on XP, vista, or prior. touching it in any way disallows windows to load from grub or via any other method, giving some error about the MBR, even if the windows partition is not touched. im not sure that I can repartition windows to take space away either, but I have a second HD Ive been using anyway, now it just has games on it.

I almost lost everything when I first got the thing trying to install linux to dual boot, but was able to remove grub and reset the MBR by wiping everything and reformatting. But even getting into the recovery partition was a bitch because the windows bootloader wouldnt accept any modification to the mbr.

is there a workaround for this? I cant imagine Im the only one having the issue, and someone must have figured out something by now, been like a year.

---

### Post by sammiev on 2014-03-15
How many partitions does your HD have? Do you have Secure Boot or Bios? May want to google those items for more info.

---

### Post by oldfred on 2014-03-17
A few Windows 7 systems did use UEFI that Windows 8 now uses, but do not have all the issues of secure boot.

Post this:
sudo parted -l

Some BIOS may have settings for security and lock MBR?

---

### Post by josh44 on 2014-03-17
IM not sure what happened, it is UEFI, im pretty sure it thought something was corrupt after I installed grub.

is it possible to install ubuntu anyway and not have windows freak out? Im looking at the link in your signature there too..

---

