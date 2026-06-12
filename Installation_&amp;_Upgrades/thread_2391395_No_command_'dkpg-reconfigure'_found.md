---
title: "No command 'dkpg-reconfigure' found"
date: 2018-05-09
forum: Installation &amp; Upgrades
---

### Post by bcqqp on 2018-05-09
Because of *blk_update_request: I/O error, dev fd0, sector 0 *errors, I'm attempting to run a fix:
```
sudo rmmod floppy
echo "blacklist floppy" | sudo tee /etc/modprobe.d/blacklist-floppy.conf
sudo dpkg-reconfigure initramfs-tools
```
Which I found here: [https://askubuntu.com/questions/719058/blk-update-request-i-o-error-dev-fd0-sector-0](https://askubuntu.com/questions/719058/blk-update-request-i-o-error-dev-fd0-sector-0)

The last step of this fix (*sudo dpkg-reconfigure initramfs-tools*) cannot be executed because *No command 'dkpg-reconfigure' found. *Do I need this last line? If so, how can I execute it? I asume normally it would involve installing dkpg and this might be a silly question, but is that still used in Ubuntu 16.04?

Thanks in advance.

---

### Post by PaulW2U on 2018-05-09
> **bcqqp said:**
> The last step of this fix (*sudo dpkg-reconfigure initramfs-tools*) cannot be executed because *No command 'dkpg-reconfigure' found. *
I'm not commenting on the validity of the fix but what did you actually type into the command line - **dpkg**-reconfigure or **dkpg**-reconfigure?  :)

"dpkg-reconfigure" is part of a default Ubuntu installation.

---

### Post by bcqqp on 2018-05-09
Oh how stupid of me. Sorry, it works now :)

---

### Post by Irihapeti on 2018-05-09
Don't worry, you aren't the only person who's made that mistake. :oops:

---

