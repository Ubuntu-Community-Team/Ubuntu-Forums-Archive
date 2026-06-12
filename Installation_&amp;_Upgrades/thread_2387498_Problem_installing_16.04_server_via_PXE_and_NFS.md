---
title: "Problem installing 16.04 server via PXE and NFS"
date: 2018-03-19
forum: Installation &amp; Upgrades
---

### Post by henrylaw on 2018-03-19
I'm trying to install Ubuntu 16.04.3 server across my network. The BOOTP/TFTP part works fine, and I can start the installation, but before it has gone very far it asks me to choose a mirror, whereas I'm expecting the installer to mount the distribution files via NFS.

In my PXE boot (.../pxelinux.cfg/default) I have the following definition:
```
LABEL Ubuntu 16.04.3 server 64-bit
append root=/dev/nfs netboot=nfs nfsroot=10.18.78.254:/home/iso/ubuntu-16.04.3-server-amd64 vga=788 -- quiet
initrd ubuntu-16.04.3-server-amd64/initrd.gz
kernel ubuntu-16.04.3-server-amd64/linux
```
10.18.78.254 is the PXE server, which contains the complete tree from the installation disk in the directory /home/iso/ubuntu-16.04.3-server-amd64.  

The paths for initrd and kernel are relative to the TFTP directory and are in fact symbolic links to ...install/netboot/ubuntu-installer/amd64/initrd.gz and ...install/netboot/ubuntu-installer/amd64/linux in that /home/iso tree (which is supposed to be mounted by NFS).

This is very similar to my Ubuntu desktop definitions, which work fine across the network.  Plainly my "append" incantation isn't providing the correct information for the installer to find the code and mount it.

Can someone point out what I've done wrong, or suggest lines of investigation so I can find out for myself?

---

### Post by markzl1 on 2018-04-11
Were you able to resolve this?  I am having the same problem.  Ubuntu 16.04.3 Desktop installation works fine using nfs.  16.04.4 server tries to use a mirror.


> **henrylaw said:**
> I'm trying to install Ubuntu 16.04.3 server across my network. The BOOTP/TFTP part works fine, and I can start the installation, but before it has gone very far it asks me to choose a mirror, whereas I'm expecting the installer to mount the distribution files via NFS.

In my PXE boot (.../pxelinux.cfg/default) I have the following definition:
```
LABEL Ubuntu 16.04.3 server 64-bit
append root=/dev/nfs netboot=nfs nfsroot=10.18.78.254:/home/iso/ubuntu-16.04.3-server-amd64 vga=788 -- quiet
initrd ubuntu-16.04.3-server-amd64/initrd.gz
kernel ubuntu-16.04.3-server-amd64/linux
```
10.18.78.254 is the PXE server, which contains the complete tree from the installation disk in the directory /home/iso/ubuntu-16.04.3-server-amd64.  

The paths for initrd and kernel are relative to the TFTP directory and are in fact symbolic links to ...install/netboot/ubuntu-installer/amd64/initrd.gz and ...install/netboot/ubuntu-installer/amd64/linux in that /home/iso tree (which is supposed to be mounted by NFS).

This is very similar to my Ubuntu desktop definitions, which work fine across the network.  Plainly my "append" incantation isn't providing the correct information for the installer to find the code and mount it.

Can someone point out what I've done wrong, or suggest lines of investigation so I can find out for myself?

---

