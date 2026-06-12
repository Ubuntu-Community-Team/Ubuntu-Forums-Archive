---
title: "VMware Tools install on 11.04 guest OS."
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by PirateFanAZ on 2011-07-16
I've installed 11.04 as a guest on a VMware Player 3.1.4 build-385536.  Host OS is Windows 7 Home Premium 64 bit.  I can't get VMware tools to configure.

Creating a new initrd boot image for the kernel.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
initctl: Job failed to start
Unable to start services for VMware Tools

Execution aborted.

I've installed the build essentials and headers for my kernel (2.6.38-10-generic) but I still get this error.  My mouse cursor in the guest OS (Ubuntu) seems to work perfectly but I can't get access setup to a shared folder.

Has anyone else run into this and solved it?

Thanks in advance

---

### Post by johnkw on 2011-08-12
Where you able to fix this?  I am having the same issue and would love to know if you were able to find a solution.

Thanks

---

### Post by steve11911 on 2011-08-15
I've always been a virtual box fan but  found a few pages that might help:

[http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html](http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html)

[http://www.sysprobs.com/install-natty-narwhal-ubuntu-1104-vmware-easy-install-vmware-tools](http://www.sysprobs.com/install-natty-narwhal-ubuntu-1104-vmware-easy-install-vmware-tools)

(Brief pause to admire the way how-to's ALWAYS make whatever your trying to do look easy as pie...)

[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

The shared folder thing...

[http://www.sysprobs.com/install-vmware-tools-manually-ubuntu-11-04-vmware-shared-folders](http://www.sysprobs.com/install-vmware-tools-manually-ubuntu-11-04-vmware-shared-folders)

---

### Post by prog101 on 2011-09-18
I have the same problem; has anyone got it running well?

---

### Post by garvinrick4 on 2011-09-18
I run one 11.04 VMware player as guest, I run it 32 bit,[COLOR=Red] it only see's one processor[/COLOR]
and I run classic gnome and VMware tools seemed to just install it was a dropdown 
menu on top panel and said install tools.
 Good luck prog101, remember run a 32 bit.

---

