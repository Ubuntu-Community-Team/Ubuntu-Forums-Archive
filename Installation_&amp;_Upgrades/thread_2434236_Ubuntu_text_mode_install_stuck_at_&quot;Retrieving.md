---
title: "Ubuntu text mode install stuck at &quot;Retrieving file 1 of 14&quot;"
date: 2020-01-02
forum: Installation &amp; Upgrades
---

### Post by Mikael_Niemel on 2020-01-02
I'm trying to install Ubuntu 18.04 LTS into a virtual machine (Xen as hypervisor) with the netboot images. But the install gets stuck at "Retrieving file 1 of 14", even though it had successfully fetched files earlier.

If you wait long enough, it eventually fails with "failed to install the selected kernel", and it goes into the setup menu.

Any ideas what could be causing this?

---

### Post by sudodus on 2020-01-02
Are you using the newest possible version of the 18.04 mini.iso? For example via this link for amd64:

[iso.qa.ubuntu.com/qatracker/milestones/384/builds/204695/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/384/builds/204695/downloads)

---

### Post by Mikael_Niemel on 2020-01-02
Actually I was using these images instead of an iso.

[http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-amd64/current/images/netboot/xen/](http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-amd64/current/images/netboot/xen/)

I guess I could try booting the VM from a iso as well.

---

### Post by sudodus on 2020-01-02
I have  no experience of those images. Maybe soneone else can chip in and help you use them.

Otherwise, yes, you can try booting the VM from an iso. At least, they work in a VirtualBox virtual machine and similar tools.

---

### Post by Mikael_Niemel on 2020-01-02
Looks like booting VM from an iso without HVM is a bit complicated in Xen... :(

---

### Post by Mikael_Niemel on 2020-01-02
Also, looks like it's trying to install generic kernel, rather than the xen version, based on this:

"Kernel package: 'linux-generic'"

---

### Post by Mikael_Niemel on 2020-01-02
I managed to do an installation with a Debian ISO, but not with Ubuntu. It looks like Ubuntu ISOs are not bootable for paravirtualized VMs.

The Debian ISO failed to install GRUB to the VM, so I have to figure out how to fix that.

EDIT: I finally managed to get a Debian VM running. I had to manually copy the boot kernel and ramdisk out of the Debian iso file, and use those to boot the setup.

---

