---
title: "Virtualization Technology (VT) broken after upgrade of 11.10 to kernel 3.0.0.17"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by rockney on 2012-03-27
The Update Manager popped-up today with an upgrade to the 3.0.0.17 kernel. After upgrading Virtualization Technology (VT) is somehow no longer compatible with VMware. I use several virtual machines and now VMware will not run any of the 64-bit VMs.

The 'host' operating system is Ubuntu 11.10 64-bit.

How can I fix things so VMware will run the 64-bit VMs again?

---

### Post by rockney on 2012-03-27
Something was changed during the upgrade from 3.0.0.16 to 3.0.0.17 because VMware will not run any of the existing 64-bit VMs --- even when I reboot into the older kernel.

The VMware Player 4.0.2 message is:

"Software virtualization is incompatible with long mode on this platform. Disabling long mode. Without long mode support, the virtual machine will not be able to run 64 bit code. For more details see http://vmware.com/info?id=152."

But it all worked before the upgrade today. Argh!!  This is putting my work behind.

---

### Post by rockney on 2012-03-30
After much digging and working different approaches I discovered an HD was going bad. Worked that issue where it went from behaving badly to dead in about 4 hours. Luckily it was just a back-up drive. After disconnecting that HD the system ran well and VT worked again.

Have no idea how a failing hard drive could have any impact on Virtualization Technology if any. In any case it seems it was not the upgrade of the kernel that was causing the problem with VMware.

To Moderator - these 3 posting can probably be deleted if you wish.

---

### Post by Elfy on 2012-03-30
Closed.

---

