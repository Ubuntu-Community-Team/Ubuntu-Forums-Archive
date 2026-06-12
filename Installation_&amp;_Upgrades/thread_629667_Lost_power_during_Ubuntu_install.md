---
title: "Lost power during Ubuntu install"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by soaringthor on 2007-12-02
I have a Dell Inspiron 1520. It has four partitions, a Utility partition, a Recovery Partition, a MediaDirect Partition, and a Vista partition. (wow!) I shrunk down the Vista partition using Vista's Disk Management, which left me with unallocated space. Then I booted from a LiveCD and installed Ubuntu in that unallocated space using the "Guided - Use largest continuous available free space" option. In the middle of the installation (60%? i don't know) the laptop lost power and (obviously) shut off. Now, I can't boot. When I power on the laptop, the Dell splash screen appears, and after that's done, the system beeps twice and an error message, "No bootable devices" pops up with options to enter setup or to run diagnostics. The diagnostics passed. The HDD is recognized in setup. When I boot from a LiveCD, I am able to mount the Utility Partition, the Recovery partition, and the fubbed Ubuntu partition, but not my Vista Partition or my MediaDirect partition. I do not have OS Recovery CDs, they are in the mail and should be arriving next week.
1) What happened??
2) Can I fix it?

Thanks,

Steven
SL,UT

---

### Post by zvacet on 2007-12-02
Reinstall Ubuntu and when you come to patitioning stage select manual.You will see all your partitions.Select the one with Ubunru on and delete it.Thar way you will get free space again.On that free space install ubuntu.

---

### Post by soaringthor on 2007-12-02
In theory, this would install GRUB, and allow me to boot in to Windows? What if I want Vista to manage the boot instead of GRUB?

---

