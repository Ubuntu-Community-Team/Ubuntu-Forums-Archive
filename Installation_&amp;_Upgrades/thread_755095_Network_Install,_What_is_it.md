---
title: "Network Install, What is it?"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by GCoffee on 2008-04-14
Hi,

I'm not planning on a network install (I'm perfectly happy with a live cd or wubi.) I'm just curious to know what they are. Iv'e heard of them but never researched them.

Thanks.

---

### Post by pseudo-random on 2008-04-14
Some Companies network boot their clients off of a server.
This way they only have to update/patch the one image and its done for the rest.
Home folders etc are held on a server also.
Its becoming less common these days with virtualization taking over.

---

### Post by chucky chuckaluck on 2008-04-14
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

it appears to be a minimal installer, particularly nice if you don't have a cdrom, or it's surfed up.

---

### Post by ibutho on 2008-04-14
Network installs are just methods of installing an OS when the actual installer files or discs are located on a remote machine either on the same network or via the internet. Usuaully HTTP, NFS, and FTP are used for network installs and the system on which the OS is to be installed is booted using a floppy, usb disk, cd etc and then you enter details of where it should get the files to be used for the installation. If the system has a network card that supports PXE, then you can boot without a physical boot disk and do the network installation.

---

### Post by koenn on 2008-04-14
what happens is that, in stead of loading boot code from a floppy disk, a hard disk, a usb stick, ... your network card 'boots', and then connects to a server to download  further boot instructions, an operating system kernel, etc, and runs that. 
it's used for "diskless' clients,  

A net install is similar, but instead of an operating system, it runs an OS installer so you can setup an OS whithout using CD's, floppies, etc. 

The term "Net install" is also sometimes used for an install that starts from a minimal installation CD , that only contains the installer and a few files. The installer boots from the CD, goes through some of the steps of setting up the OS (like configuring network)  and downloads whatever additional required files from the repositories on the internet (Debian : netinst.iso, business card image ; Ubuntu: mini.iso )
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

---

