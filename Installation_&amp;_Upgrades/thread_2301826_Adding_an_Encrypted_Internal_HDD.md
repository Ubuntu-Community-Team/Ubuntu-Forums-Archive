---
title: "Adding an Encrypted Internal HDD"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by clalian on 2015-11-05
Hello everyone,
I have a Xubuntu 15.10 install.
On initial installation, I selected the full-disk encryption.

When I boot up my machine, it asks for the disk's passphrase.
After I enter it, the machine boots up.

I want to add now an additional internal hdd to this workstation.
The main OS is in a SSD, and the new one is a 2TB spinning-disk drive.

I know how I can add this 2TB hdd... and how I can set it up as to "auto-mount" on boot-up using the UUID.

Yet, how can I encrypt this 2TB hdd?
Is it possible to have the same "main OS ssd" passphrase be used on the 2TB hdd?
Or how can I go about this?
I am a little bit lost on this.

Thank you!

---

### Post by TheFu on 2015-11-05
**cryptsetup** is what you seek. There is a how-to.

---

