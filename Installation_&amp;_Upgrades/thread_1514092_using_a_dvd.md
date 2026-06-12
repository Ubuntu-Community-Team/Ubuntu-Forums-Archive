---
title: "using a dvd"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by sagmate on 2010-06-20
i have a fedora/rhel dvd that i'm tryin to install in my virtual machine but it won't let me do..does anyone have any suggestions on what i could be doing wrong?

---

### Post by lemming465 on 2010-06-21
What's your hypervisor?  The answers are slightly different for vmware, virtualbox, kvm, etc.  The main idea is before starting the guest, go to the configuration page for the virtual DVD device.  If you don't have such a device, edit the VM configuration to add it.  Then, depending on whether your fedora DVD is physical or just an .ISO file, select the appropriate radio button, if necessary supply the path to the physical DVD device or the .ISO file, and click any "connect on powerup" checkbox to on.  For kvm you may also have to change the boot device from disk to DVD.

---

