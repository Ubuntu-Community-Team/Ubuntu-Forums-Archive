---
title: "virt-manager won't start after upgrade 10.04 to 10.10"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Bow rat on 2010-10-11
I just upgraded from 10.04 to 10.10 and now virt-manager won't start. If I try from the menu, nothing happens. If I try and start it from the command line (as root) it give the error:

**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted

I've tried searching and can't seem to find anything related, but was hoping this might make some sense to someone.

Many thanks in advance for any help!

---

### Post by Bow rat on 2010-10-12
OK - PEBCAK

I still don't know why I get that error when trying to start virt-manager, but I seem to have got things running again.

What I did:

I double checked that my user account was a member of both libvirtd and kvm. I had dropped out of kvm group for some reason, so I added myself back in.

I double checked permissions on the image files in /var/lib/libvirt. They had got changed as well, so I chgrp'd them to kvm again and chmod of 660.

I tried starting / stopping VMs through virsh (as both myself and as root) and that seemed to work now.

virt-manager also started to work (must have been some permissions thing) and I could now change the (default) usermode connection to the proper QEMU/KVM connection on my machine and hey presto - it all started playing nicely again.

Hope this might help someone else seeing a similar issue.

---

