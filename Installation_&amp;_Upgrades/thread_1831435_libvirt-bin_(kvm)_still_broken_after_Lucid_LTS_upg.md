---
title: "libvirt-bin (kvm) still broken after Lucid LTS upgrade"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by bl8n8r on 2011-08-23
After upgrading a 12 core Opteron hypervisor to the latest Lucid LTS patches, virtualization is broken.  guests will not start using virt-manager.

The error message I get is: failed to retrieve chardev info with 'info chardev'

Anyone know what's up?

---

### Post by bl8n8r on 2011-08-23
Solved by doing: touch /etc/apparmor.d/disable/usr.sbin.libvirtd  and then reboot.  Not a great fix from security standpoint. Just one step above useless.

---

