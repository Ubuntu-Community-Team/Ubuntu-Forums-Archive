---
title: "Ubuntu network installation :: UEFI+PXE+grub"
date: 2020-12-13
forum: Installation &amp; Upgrades
---

### Post by polarbear20 on 2020-12-13
Hello,

I am attempting to install Ubuntu 20.04 LTS over network to Lenovo desktop and looking for an assistance.

Current setup
1. Lenovo desktop UEFI Secure boot option enabled
2. DHCP server set to serve DHCP request to boot shim.efi.singed from 'next server'
3. TFTP server has grub directory with shim.efi.signed, grubnetx64.efi.signed, grub.conf files and directory x86_64-efi
4. Desktop booted with F12 to select network boot over IP4 
5. shim.efi.signed picks up grubnetx64.efi.signed and grub.conf files
6. grub menu presented on the screen
7. selected option to boot Ubuntu 20.04 live
8. on screen appears '[COLOR=#ff0000]error: File not found[/COLOR]'
9. on timeout, it looks like kernel boots and can not find root fs (I assume that initrd file was not found) then kernel panic

```

....
[ 0.554888] VFS: Cannot open root device "(null)" or unknown-block(0,0): error -6
[ 0.555295] Please append a correct "root=" boot option; here are the available partitions:
[ 0.555712] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
.....
[ 0.562027] --- [ end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) ]---
```

The files shim.efi.signed, grubnetx64.efi.signed, grub.conf and x86_64-efi directory are taken from Ubuntu 20.04 ISO image.
The file grub.conf was edited to accommodate location of vmlinuz, initrd files on TFTP server. 

The files shim.efi.signed, grubnetx64.efi.signed was extracted from ISO image for matching packages with following command

```

dpkg -x package.deb
```

I did some reading on the internet and still can not to figure out where is the problem hidden

grub.conf

```

menuentry "Install Ubuntu" {
           set gfxpayload=keep
           linuxefi  /Ubuntu/20.04/amd64/vlinuz .....
           initrdefi /Ubuntu/20.04/amd64/initrd.gz
}

```

Any clues and pointers are greatly appreciated.

NOTE #1: vmlinuz and initrd files are taken from netboot and system able to proceed with installation in 'BIOS/CSM' compatibility mode

NOTE #2: an attempt to boot Fedora and REHEL with similar menu options produces 'error: RHEL/.../vmlinuz has invalid signature' -- it appears that secure boot detects that kernel of these OSes are not signed

Thank you,
Polar Bear

---

