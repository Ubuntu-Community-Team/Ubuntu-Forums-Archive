---
title: "Installing on fresh disk - no such cryptodisk found"
date: 2021-02-26
forum: Installation &amp; Upgrades
---

### Post by Gordonbp531 on 2021-02-26
Lubuntu 20.4.
I've tried installing 3 times now, with LVM enabled.
Every time I reboot after the installation has finished, after the "enter passphrase" I get 
"error - access denied
error - no such cryptodisk found
error - disk 'cryptouuid/4f53dd71b1eb499ea96bb20929f4b673' not found
entering rescue mode....
grub rescue>"

I've tried the solution here [https://linuxconfig.org/how-to-fix-grub-error-no-such-partition-grub-rescue](https://linuxconfig.org/how-to-fix-grub-error-no-such-partition-grub-rescue) but ii fails on the mnt sda1 command saying unknown file system.

Can anyone help please?

---

### Post by guiverc on 2021-02-26
The "enter passphrase" implies to me you've used encryption. 

Are you using a non-english language?  Does your machine have a **non-Qwerty** keyboard?

The language selections used when the system is running (ie. you're logged in to LXQt) don't work when the system has just booted, so the keys may have different values IF you're using a non-Qwerty keyboard.

This is a known issue in `calamares` (the installer).  [https://github.com/calamares/calamares/issues/1203](https://github.com/calamares/calamares/issues/1203)

Sorry I only use english, and use Qwerty keyboards so have no experience with it, I also don't know that this is your issue, but I'll suggest [https://discourse.lubuntu.me/t/20-04-encryption-startup-passphrase-entry-issue/1172](https://discourse.lubuntu.me/t/20-04-encryption-startup-passphrase-entry-issue/1172) may have some clues.   Asking a question on the Lubuntu forum (where we have some members who don't speak just english, use only qwerty keyboards may also be worthwhile).

My 2c anyway.

---

