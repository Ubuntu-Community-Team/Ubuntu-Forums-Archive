---
title: "PXE server 12.04 install will not use NFS export and always asks for cdrom"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by Darrain on 2013-10-23
Hello


We are attempting to install Server 12.04 through pxe using nfs. We are successfully at the pxe portion but every time it goes to install, we are prompted for the cdrom. Further, doing an ip a at this point in a console yields zero network config, as well as loopback completely down. We are putting the preseed file in the initrd.gz file that pxe picks up. If we insert the cdrom source and press continue, the install completes to our satisfaction using the preseed. 


We would really just like to export the install files through nfs and not have to use a cdrom at all. Any help would be greatly appreciated.


Darrain

---

### Post by newbie-user on 2013-10-23
I haven't tried using NFS, but I do network installs using tftpd-hpa. I know it's not the fix you're asking for, but if no one else comes through, then please do give it a try. Instructions can be found here: [http://techblog.glendaleacademy.org/ubuntu-12-04/network-install-server-for-ubuntu-12-04](http://techblog.glendaleacademy.org/ubuntu-12-04/network-install-server-for-ubuntu-12-04)

---

