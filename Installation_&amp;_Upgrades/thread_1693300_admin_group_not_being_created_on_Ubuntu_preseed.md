---
title: "admin group not being created on Ubuntu preseed"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by bmckim on 2011-02-22
I am preseeding an Ubuntu Server 10.04 installation and after install the default 'admin' group is not present. I am not using this line:

# The user account will be added to some standard initial groups. To
# override that, use this.
#d-i passwd/user-default-groups string audio cdrom video


EDIT:

Looks to be part of this bug: [https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/40684]("https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/40684")
> if you've set a root password, then it won't make the 'admin' group, or allow the admin group to use sudo to become root.

Anyone have a way around this? How would I go about creating this group manually?

---

