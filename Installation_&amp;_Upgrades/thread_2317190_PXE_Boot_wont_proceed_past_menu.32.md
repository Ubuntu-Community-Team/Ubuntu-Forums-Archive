---
title: "PXE Boot wont proceed past menu.32"
date: 2016-03-14
forum: Installation &amp; Upgrades
---

### Post by MA94 on 2016-03-14
I am trying to set up a PXElinux server which seems to be close to completion however the problem I am facing is when  it comes to booting up a client machine, I can get to the menu however  if I try pressing enter to proceed with one of the boot options
 “Try Ubuntu 14.04 Desktop” or “Install Ubuntu 14.04 Desktop”

I get no response.

Any idea why this is?


Any idea what is causing this?

below is the content of my "/var/lib/tftpboot/pxelinux.cfg/default" file:




#DEFAULT menu.c32
TIMEOUT 100
PROMPT 0
MENU INCLUDE pxelinux.cfg/PXE.conf
NOESCAPE 1
LABEL Install PXE install Ubuntu
MENU LABEL PXE install Ubuntu
kernel /var/lib/tftpboot/Ubuntu/vmlinuz.efi
append boot=casper automatic-ubiquity netboot=nfs nfsroot=10.0.0.2:/var/lib/tftpboot/Ubuntu/14.04/amd64 initrd=/var/lib/tftpboot/Ubuntu/initrd.$
ENDTEXT

---

