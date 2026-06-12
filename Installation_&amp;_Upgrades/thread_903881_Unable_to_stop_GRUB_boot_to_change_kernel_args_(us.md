---
title: "Unable to stop GRUB boot to change kernel args (using VMware)"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by skstrobel on 2008-08-28
I am working with Ubuntu 8.04 installed in a VMware virtual machine, running it from a desktop shortcut created with VMware Server (the free version).  I am trying to change the kernel options, but I can't seem to abort the startup process.  In fact, I don't see any messages from GRUB during startup, so I have just been giving control of the keyboard to the VM as early in the startup process as possible by pressing CTRL-G, then pressing "a" or ESC repeatedly to attempt to stop the boot process.  Thanks for any suggestions.

Steve

Full disclosure:  I messed up my username/password and can't log onto Ubuntu, so I trying to recover the password as described at <http://www.petri.co.il/vmware-esx-server-root-password-reset-recovery-lost.htm>.  Any other solution for that problem would be fine too :)  Thanks.

---

### Post by skstrobel on 2008-08-29
I finally figured out how to stop the GRUB boot process so I could switch to single user mode.  From the Ubuntu login screen, select Options (lower-left corner), then Restart.  The GRUB messages are then visible and pressing ESC works fine to access the recovery console.

---

