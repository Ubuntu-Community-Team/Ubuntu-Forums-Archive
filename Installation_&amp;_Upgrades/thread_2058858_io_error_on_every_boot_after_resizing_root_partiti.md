---
title: "i/o error on every boot after resizing root partition"
date: 2012-09-16
forum: Installation &amp; Upgrades
---

### Post by Paleskin on 2012-09-16
Recently I resized my root partition on my ubuntu usb flash drive installation (full install, not live usb with persistence)

I deleted the swap partition and enlarged my root partition size to the max, using ubuntu on another machine

Now on every boot, there are some messages which says something like "i/o error, fd0, sector0....and so on

The messages keep showing with new sectors, I must wait a long time to come into the desktop environment

The desktop works fine, but the long boot process with i/o msg errors really become a pain in the.....

Can anyone help me ?



Thanks

---

### Post by oldfred on 2012-09-16
When you deleted swap did you delete the entry in fstab?

Do you have a floppy disk? You might turn off floppy in BIOS.

---

### Post by Paleskin on 2012-09-17
> **oldfred said:**
> When you deleted swap did you delete the entry in fstab?

Do you have a floppy disk? You might turn off floppy in BIOS.

No, I don't have floppy and I turned off the floppy in the bios

Which entries related swap should I delete in fstab ?

---

### Post by oldfred on 2012-09-17
The entry for swap. You can just put # as the first character and then it is a comment.

sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

should be an entry like this:

```
# swap was on /dev/sda6 during installation
UUID={longUUIDchars}  none            swap    sw              0       0

```

---

