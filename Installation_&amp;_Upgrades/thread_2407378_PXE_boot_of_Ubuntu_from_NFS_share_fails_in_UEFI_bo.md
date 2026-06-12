---
title: "PXE boot of Ubuntu from NFS share fails in UEFI boot after initrd.gz"
date: 2018-12-03
forum: Installation &amp; Upgrades
---

### Post by qurujames on 2018-12-03
Hi all,

I have been working on booting a diskless image of Ubuntu 18.04 LTS using a combination of PXE booting, and NFS storage.

I built and tested the image using a Legacy BIOS based boot and everything works find. However when I switch to UEFI booting (and the corresponding UEFI network stack in the firmware of my motherboard) I see a strange problem. The network stack gets an IP address from the DHCP server (also Ubuntu 18.04 LTS), and loads the syslinux.efi file from the syslinux-efi package. From there the appropriate c32 modules are loaded, and then the menu. When my default (and only) entry for Ubuntu diskless loads, it successfully downloads the kernel from the TFTP server, and then proceeds to load the initrd image. The process seems to hang for ages on loading the initrd.gz image, and after a lengthy delay, the motherboard reboots. I don't see any output on the screen so I have no error messages to debug - just a reboot.

Both the kernel and initrd.gz files were downloaded from:

[http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/](http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/)

I'm a little stuck on how to debug this issue as I see the UEFI firmware loading the correct files from the server. Here are my (simplistic) menu files from the tftpboot directory on my PXE server:

```
root@mgmt01:/var/lib/tftpboot/EFIx64/pxelinux.cfg# cat default
path isolinux/bios
include pxelinux.cfg/menu.cfg
default isolinux/efi64/vesamenu.c32
prompt 0
timeout 10

root@mgmt01:/var/lib/tftpboot/EFIx64/pxelinux.cfg# cat menu.cfg
menu title Thin client boot menu
label ubuntu-1804-thin-client
  menu label ^Ubuntu 18.04 thin client
  kernel linux
append vga=788 initrd=initrd.gz ip=dhcp nfsroot=xx.xx.xx.xx:/nfsroot rw
menu end

```

Any and all ideas appreciated!

Thanks,

James

Ok a quick update on this - I analyzed a Wireshark trace of the interaction between the client and the PXE server. It appears that the client motherboard is rebooting before initrd.gz finishes downloading.

TFTP reports that initrd.gz is 46921958bytes long, and will be sent in 1408 by chunks. The motherboard reboots itself just after receiving chunk 29548, and the TFTP server retries chunk 29549 several times as it is getting no ACK from the client. It takes just over 228 seconds from the start of the transfer of initrd.gz to the reboot (which seems slow to me but I could live with that if it worked), so I'm now wondering if this is some kind of timeout parameter, but I'm not sure where to start looking - whether this is something that can be adjusted in the syslinux menu, or if it's a firmware issue on the motherboard itself.

Has anyone ever come across anything like this before?

For anyone who comes across this, it turns out there are issues with the TFTP transfer of files in syslinux that cause them to be incredibly slow. With large files the firmware (to be confirmed - I presume it's not syslinux) can choose to reboot the system - presumably as some sort of hang protection? A much more in-depth analysis is given in this thread from 2015:

[https://www.syslinux.org/archives/2015-June/023649.html](https://www.syslinux.org/archives/2015-June/023649.html)

In short the build of Syslinux included with Ubuntu 18.04 LTS is 6.03, which is over 4 years old at this point. There are many bug fixes since that time including this issue, but sadly there has never been a full 6.04 release. There are two possible fixes when using UEFI firmware - one is to use the last "stable" release of syslinux and avoid TFTP transfers of large files as these will fail.

The other is to clone from the syslinux git repository and build that - I did this and my UEFI TFTP file transfers sped up hugely, resulting in a successful boot of my image. Which solution is correct will depend on your own circumstances. Hope this helps someone out who gets stuck like I did! Here are my build steps:

```
git clone [https://repo.or.cz/syslinux.git](https://repo.or.cz/syslinux.git)
cd syslinux
apt install make gcc python nasm uuid-dev gcc-multilib g++-multilib
make spotless
make
cd /var/lib/tftpboot/EFIx64/
cp /root/syslinux/efi64/com32/elflink/ldlinux/ldlinux.e64 .
cp /root/syslinux/efi64/com32/lib/libcom32.c32 .
cp /root/syslinux/efi64/com32/libutil/libutil.c32 .
cp /root/syslinux/efi64/efi/syslinux.efi .
cd isolinux/efi64/
rm -f *
find /root/syslinux/efi64/ -name *.c32 -exec cp '{}' . \; 
```

---

