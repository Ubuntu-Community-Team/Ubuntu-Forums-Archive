---
title: "LiveCD will not load via PXE"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by mwjones on 2009-11-28
I am trying to boot into the Ubuntu 9.10 Desktop i386 LiveCD over the network.  There is already a PXE server that serves up Ubuntu 9.10 Alternate i386, Damn Small Linux, and DBAN.  

Converted the initrd.lz to initrd.gz:
```
lzma -dc -S .lz initrd.lz | cpio -id
find . -name "init" -type f | cpio &#8211;quiet &#8211;dereference -o -H newc | gzip -9 > initrd.gz
cp initrd.gz /store/tftpboot/ubuntu/9.10/i386_desktop/casper
```

tftpd ubuntu.menu file:
```
LABEL 21
        MENU LABEL Ubuntu 9.10 Desktop i386
        KERNEL ubuntu/9.10/i386_desktop/vmlinuz
#        APPEND boot=casper root=/store/tftpboot/ubuntu/9.10/i386_desktop initrd=ubuntu/9.10/i386_desktop/casper/initrd.gz
        APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.1.103:/store/tftpboot/ubuntu/9.10/i386_desktop initrd=i386_desktop/casper/initrd.gz --
        TEXT HELP
        Boot the Ubuntu 9.10 Live CD
ENDTEXT
```

/etc/exports (also tried with no_root_squash and s/rw/ro/):
```
/store/tftpboot/ubuntu/9.10/i386_desktop	192.168.1.0/24(rw,async,no_subtree_check)
```

As is, I just get returned to the PXE boot menu right away.  If I uncomment the commented line in ubuntu.menu, and comment out the NFS line, the client complains with a kernel panic and can't find init.

Relevant docs I have read without success:

[https://wiki.ubuntu.com/LiveCDNetboot](https://wiki.ubuntu.com/LiveCDNetboot)
[http://ubuntuforums.org/showthread.php?t=1112209](http://ubuntuforums.org/showthread.php?t=1112209)
[http://linuxadministration.us/2009/11/16/ubuntu-9-10-pxe-boot/](http://linuxadministration.us/2009/11/16/ubuntu-9-10-pxe-boot/)
[http://mediakey.dk/~cc/ubuntu-netboot-and-netinstall-with-pxe/](http://mediakey.dk/~cc/ubuntu-netboot-and-netinstall-with-pxe/)

Help me Obi-Wan Kenobi, you're my only hope.

---

### Post by mwjones on 2009-11-29
Stupid slashes.  Here is the proper config:

ubuntu.menu:
```
LABEL 21
        MENU LABEL Ubuntu 9.10 Desktop i386
        KERNEL /ubuntu/9.10/i386_desktop/casper/vmlinuz
        APPEND initrd=/ubuntu/9.10/i386_desktop/casper/initrd.lz boot=casper netboot=nfs nfsroot=192.168.1.103:/store/tftpboot/ubuntu/9.10/i386_desktop --
        TEXT HELP
        Boot the Ubuntu 9.10 Live CD
ENDTEXT
```

/etc/exports:
```
/store/tftpboot/ubuntu/9.10/i386_desktop        192.168.1.0/24(ro,sync,no_subtree_check)
```

Thanks [http://www.panticz.de/Ubuntu-LiveCD-PXE-boot](http://www.panticz.de/Ubuntu-LiveCD-PXE-boot)

---

