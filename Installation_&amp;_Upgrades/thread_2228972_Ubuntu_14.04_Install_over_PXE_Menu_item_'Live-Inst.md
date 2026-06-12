---
title: "Ubuntu 14.04 Install over PXE: Menu item 'Live-Installer' failed"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by John_Kelly on 2014-06-10
Hello all,

I recently tried to put Ubuntu Server 14.04 (latest) on our company PXE server, but when I get to the actual installation portion of the install wizard it fails. 

Upon exporting the syslog, I can see the following entries:

INFO: Menu item 'live-installer' selected
base-installer: error: Could not find any live images
WARNING **: Configuring 'live-installer' failed with error code 1
WARNING **: Menu item 'live-installer' failed.

This is strange because I extracted the .iso file to my pxe server and just copied all the files over to my tftp directory (which is also sym linked to my web server for faster transfers via http)
I don't think I can be missing any files since I literally just extracted the .iso

This is what my ubuntu 14.04 directory contains:
root@jumpstart:~ # cd /usr/tftpboot/images/ubuntu/14.04/x86_64/
EFI/                           boot/                          doc/                           isolinux/                      pics/                          preseed/                       ubuntu@
README.diskdefines             dists/                         install/                       md5sum.txt                     pool/                          ubuntu-14.04-server-amd64.iso  

Also, this is what my menu entry within pxelinux.cfg looks like:
Label ubuntu 14.04 64
 Menu Label Ubuntu Server 14.04 (64 bit) Interactive Install
 KERNEL [http://10.0.0.250/tftpboot/images/ubuntu/14.04/x86_64/install/netboot/ubuntu-installer/amd64/linux](http://10.0.0.250/tftpboot/images/ubuntu/14.04/x86_64/install/netboot/ubuntu-installer/amd64/linux)
 APPEND ks=http://10.0.0.250/tftpboot/images/ubuntu/14.04/x86_64/install/netboot/ubuntu-installer/amd64/ks.cfg initrd=http://10.0.0.250/tftpboot/images/ubuntu/14.04/x86_64/install/netboot/ubuntu-installer/amd64/initrd.gz


Any help is greatly appreciated, thanks!

---

### Post by John_Kelly on 2014-06-25
Still having this problem.. anybody know what's happening?

---

### Post by ppatrick on 2014-09-08
if you want to PXE install i.e.

>     ubuntu-14.04.1-server-amd64.iso
    ubuntu-14.04.1-server-i386.iso

without internet support please read how Serva does it here :
[http://vercot.com/~serva/an/NonWindowsPXE3.html](http://vercot.com/~serva/an/NonWindowsPXE3.html)

```
;-Serva v2.1 Non-Windows Asset Information File 
;-Boot/Install:
;  Ubuntu LTS 14.04 Server / 12.04 Alternate
;-Tested on:
;  ubuntu-14.04.1-server-amd64.iso
;  ubuntu-14.04.1-server-i386.iso
;
;  ubuntu-12.04.4-alternate-amd64.iso
;  ubuntu-12.04.4-alternate-i386.iso
;-Require:
;  \NWA_PXE\ offered as as HTTP root
;-Notes:
; -
[PXESERVA_MENU_ENTRY]
asset    = Ubuntu LTS 14.04.1 Server
platform = amd64
kernel   = NWA_PXE/$HEAD_DIR$/install/netboot/ubuntu-installer/amd64/linux
;kernel   = NWA_PXE/$HEAD_DIR$/install/netboot/ubuntu-installer/i386/linux
append   = initrd=NWA_PXE/$HEAD_DIR$/install/netboot/ubuntu-installer/amd64/initrd.gz vga=788 mirror/country=manual mirror/http/hostname=$IP_BSRV$ mirror/http/directory=/$HEAD_DIR$ mirror/http/proxy="" live-installer/net-image=http://$IP_BSRV$/$HEAD_DIR$/install/filesystem.squashfs
;append   = initrd=NWA_PXE/$HEAD_DIR$/install/netboot/ubuntu-installer/i386/initrd.gz vga=788 mirror/country=manual mirror/http/hostname=$IP_BSRV$ mirror/http/directory=/$HEAD_DIR$ mirror/http/proxy="" live-installer/net-image=http://$IP_BSRV$/$HEAD_DIR$/install/filesystem.squashfs
```

If you want to do this using some other PXE server different than Serva you might require some editing of the former parameters.

---

