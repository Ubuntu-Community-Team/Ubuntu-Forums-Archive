---
title: "upgrade from 1204 to 1404 with raid. system can't boot"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by walter_j on 2014-11-23
My home server had 12.04 on it. I was having trouble connecting to it from a win 7 pc, so I tried upgrading the server. A error occurred during the install of grub, resulting in File Not Found error when booting. I downloaded boot repair cd, which didn't resolve the issue. The boot repair utility stepped through apt-get scripts which i ran, but still generated a File Not Found message with a Grub Repair prompt. I think it's a LVM issue which I can't resolve. The server was set up as a RAID. The utility generated a message to past.ubuntu.com/9177537/

Thanks

---

### Post by oldfred on 2014-11-23
Is this yours? Your link does not work.
[http://paste.ubuntu.com/9177537/](http://paste.ubuntu.com/9177537/)


That shows kernel 2.6.31 or Ubuntu 9.10??
And LVM but not RAID?

---

### Post by walter_j on 2014-11-23
that appears to be mine. It's not a UEFI issue, as it's an old Pentium 4 pc. It was probably 9.10 originally, and upgraded continually to 14.04. Maybe it's not RAID, but thats what I was trying to instal from 12.04. It ran great for a year or so, until the upgrade. The boot repair utility may have selected an older kernal to boot, but I could fix that if it booted. This PC can't boot from USB, so it's a old bios. perhaps the old bios is a issue?

---

### Post by oldfred on 2014-11-23
Some really old BIOS need / (root) or the /boot partition fully inside the first 100GB of a drive. The BIOS cannot read boot files beyond that point. But if yours worked before, I would not think that is an issue, but normal installs have /boot partition first on hard drive then rest of drive is LVM.

You only show one drive, so that would not be RAID.

The only kernels shown are the 2.6 versions.

Best not to attempt an upgrade when having issues. That then usually just compounds the errors and makes it very difficult to fix.

Do you have good backups of all your data? If not use live installer to copy data now.

---

### Post by walter_j on 2014-11-23
I used the pc as a test for my work pc, where i wanted to set up RAID. The raid test worked with 1 disk: i assumed it would start mirroring data to a second disk when i installed it. As for kernals, the latest one showing from a live cd is initrd.img-3.2.0-70-generic-pae. I don't know why it wasn't set up by boot repair: could this be the issue? I can back up the pc easily enough: so is a reinstall necessary?

---

### Post by oldfred on 2014-11-23
Never used RAID, so do not know details.

Running Boot-Repair does not update kernels. It just runs scripts to run Ubuntu's own updates. But if install is obsolete there are no repositories to update from.

I think you are to a new install.
Is hardware so old the PAE is an issue?
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

