---
title: "kickstart: cannot suppress logical volume question"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by bchill on 2010-06-08
Hello,

In kickstarting 10.04, I cannot get past the message that asks you to confirm deletion of the exiting logical volumes. I've tried these preseed directives in my kickstart file, but they don't seem to be having any effect.

What am I doing wrong?

Brian

------------------------------------------------------------

%pre
preseed d-i             partman-lvm/device_remove_lvm boolean true
preseed d-i             partman-lvm/confirm_nooverwrite boolean false
preseed partman-lvm     partman-lvm/device_remove_lvm   boolean true
preseed partman-lvm     partman-lvm/confirm_nochanges   boolean true
preseed partman-lvm     partman-lvm/confirm     boolean true
preseed unknown         partman-lvm/confirm     boolean true
preseed partman-lvm     partman-lvm/vgdelete_confirm    boolean true

---

### Post by bchill on 2010-06-10
I figured this out.


The preseed directives go in the main kickstart area - not in %pre.

---

