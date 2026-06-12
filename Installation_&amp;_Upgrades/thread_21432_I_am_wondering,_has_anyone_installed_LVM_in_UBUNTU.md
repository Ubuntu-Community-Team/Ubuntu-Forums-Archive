---
title: "I am wondering, has anyone installed LVM in UBUNTU"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by BORTKOMMEN on 2005-03-22
I have been trying to create a Logical Volume Group during install, but it seems to me the installer does not support that.
My intention is to make a primary /boot partition with ext3 and the rest of my partitions inside the Volume Group so I can resize them if needed.

So is it possible at all?

---

### Post by mukesh agrawal on 2005-04-24
The installer does allow installing onto LVMs. Choose expert mode (type "expert" at the boot prompt), and then load the LVM installer module when the installer gives you the option of loading installer modules.

You can then create LVs, and place filesystems on the LVs. Note that there seems to be a bug with the initrd that the installer creates, and booting from USB. See [ LVM install fails to boot due to misconfigured initird](http://bugzilla.ubuntu.com/show_bug.cgi?id=10110).

---

