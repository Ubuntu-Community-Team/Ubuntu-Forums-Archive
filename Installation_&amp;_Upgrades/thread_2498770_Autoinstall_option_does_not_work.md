---
title: "Autoinstall option does not work"
date: 2024-06-26
forum: Installation &amp; Upgrades
---

### Post by wattersm on 2024-06-26
[FONT=Ubuntu]I am attempting to set up an autoinstall environment however the installer continues to ask for confirmation even after adding the “autoinstall” parameter to the kernel arguments. We are using ipxe to boot with the following configuration.[/FONT]

```
set gfxpayload=keep
imgfree
kernel http://10.70.160.51/ipxe/ubuntu/20.04/hwe-vmlinuz
initrd http://10.70.160.51/ipxe/ubuntu/20.04/hwe-initrd
imgargs hwe-vmlinuz initrd=hwe-initrd netboot=nfs boot=casper ip=dhcp nfsroot=10.70.160.51:/NFS_Mounts/ubuntu-2004 cloud-config-url=http://10.70.160.51/preseed/focal/user-data autoinstall
boot || goto failed

```[FONT=Ubuntu]
This configuration is able to boot the system and load the user-data file however I *still* get prompted to confirm destructive action to continue the install.  Is there a way to avoid this?  Here is a screenshot for reference.

[IMG]https://imgur.com/pBUxDeD.jpg[/IMG]


[/FONT]

---

### Post by ActionParsnip on 2024-06-28
[https://stackoverflow.com/questions/61500905/preseed-file-for-ubuntu-18-04-20-04-hanging-on-formatting-disk-screen](https://stackoverflow.com/questions/61500905/preseed-file-for-ubuntu-18-04-20-04-hanging-on-formatting-disk-screen)
Seems to be a known thing

---

