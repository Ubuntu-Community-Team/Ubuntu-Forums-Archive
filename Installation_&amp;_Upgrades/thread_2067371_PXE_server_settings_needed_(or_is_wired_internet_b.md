---
title: "PXE server settings needed (or is wired internet broken?)"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by likyl on 2012-10-06
Hi, a while back I wrote a tutorial on PXE booting, and just casually described how to get Ubuntu to boot over PXE.  Not only was it tricky finding a way to get Ubutuntu 12 to boot, but the method which I manged seems to have broken connecting to the internet over the wired ethernet port which was used to connect to the PXE server and boot up.  

So my question is, does this sound like a known bug in the Ubuntu 12.04 release, or maybe is there someone out there who can explain what I'm missing?

Here's the code I'm using in my PXE menu which I assume must be the only thing I can change to make the system work??

```

LABEL Ubuntu LiveCD 12 32bit   
  MENU DEFAULT   
  KERNEL boot/ubuntu/ubuntu32/casper/vmlinuz   
  APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.0.11:/tftpboot/boot/ubuntu/ubuntu32 initrd=boot/ubuntu/ubuntu32/casper/initrd.lz quiet splash --  

IPAPPEND 3
```Commands to perform while booted up to fix the wired connection are also welcome.  Also, if it turns out this is a bug, where do I go to speak with Ubuntu devs about this?

---

### Post by pixeldotz on 2012-10-10
i think you might be on to something with this.
the reason i say is because i am booting various distros from http and nfs using a hybrid WDSsyslinux system.

i'm trying to get UBERMIX to boot from nfs (which they say is supported). however the newest version of UBERMIX is based on 12.04 precise. 

it will boot the kernel, and it will load the initrd, but once it does that it fails to move forward. dropping to a shell after this and trying a PING or IFCONFIG command results in nothing, as if the nic card was disabled or broken after it loaded from pxe.

i'm going to try an older kernel/initrd and see if that works.

---

