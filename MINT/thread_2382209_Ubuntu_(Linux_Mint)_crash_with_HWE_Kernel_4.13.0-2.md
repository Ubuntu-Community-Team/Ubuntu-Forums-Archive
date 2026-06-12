---
title: "Ubuntu (Linux Mint) crash with HWE Kernel 4.13.0-26"
date: 2018-01-10
forum: MINT
---

### Post by anselch1011 on 2018-01-10
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1742470](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1742470)

```
Distributor ID: LinuxMint
Description: Linux Mint 18.3 Sylvia
Release: 18.3
Codename: sylvia
Linux Asus-1000HE 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 i686 i686 i686 GNU/Linux
Linux Mint 18.3 with HWE Kernel (sudo apt install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04)
```

I've upgraded linux kernel from 4.10.0-4.10.0-42.46~16.04.1 to 4.13.0-26.29~16.04.2.
I've got errors while upgrade kernel.
And, After rebooting, my linux login screen has been broken.
I cannot log in and my linux screen has gone black.
Restroing kernel 4.10, then works well.
```
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
Error! Bad return status for module build on kernel: 4.13.0-26-generic (i686)
Consult /var/lib/dkms/ndiswrapper/1.60/build/make.log for more information.
```
Belows are /var/lib/dkms/ndiswrapper/1.60/build/make.log.
```
DKMS make.log for ndiswrapper-1.60 for kernel 4.13.0-26-generic (i686)
2018. 01. 11. (&#47785;) 00:16:20 KST
make: &#46356;&#47113;&#53552;&#47532; '/usr/src/linux-headers-4.13.0-26-generic' &#46308;&#50612;&#44048;
  AR /var/lib/dkms/ndiswrapper/1.60/build/built-in.o
  MKEXPORT /var/lib/dkms/ndiswrapper/1.60/build/crt_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.60/build/hal_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.60/build/ndis_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.60/build/ntoskernel_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.60/build/ntoskernel_io_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.60/build/rtl_exports.h
  MKEXPORT /var/lib/dkms/ndiswrapper/1.60/build/usb_exports.h
  CC [M] /var/lib/dkms/ndiswrapper/1.60/build/crt.o
  CC [M] /var/lib/dkms/ndiswrapper/1.60/build/hal.o
  CC [M] /var/lib/dkms/ndiswrapper/1.60/build/iw_ndis.o
  CC [M] /var/lib/dkms/ndiswrapper/1.60/build/loader.o
  CC [M] /var/lib/dkms/ndiswrapper/1.60/build/ndis.o
In file included from /var/lib/dkms/ndiswrapper/1.60/build/ndis.h:19:0,
                 from /var/lib/dkms/ndiswrapper/1.60/build/ndis.c:16:
/var/lib/dkms/ndiswrapper/1.60/build/ndis.c: In function ‘NdisMAllocateSharedMemory’:
/var/lib/dkms/ndiswrapper/1.60/build/ntoskernel.h:122:20: error: ‘__GFP_REPEAT’ undeclared (first use in this function)
       GFP_KERNEL | __GFP_REPEAT)
                    ^
/var/lib/dkms/ndiswrapper/1.60/build/ndis.c:1095:10: note: in expansion of macro ‘PCI_DMA_ALLOC_COHERENT’
  *virt = PCI_DMA_ALLOC_COHERENT(wd->pci.pdev, size, &dma_addr);
          ^
/var/lib/dkms/ndiswrapper/1.60/build/ntoskernel.h:122:20: note: each undeclared identifier is reported only once for each function it appears in
       GFP_KERNEL | __GFP_REPEAT)
                    ^
/var/lib/dkms/ndiswrapper/1.60/build/ndis.c:1095:10: note: in expansion of macro ‘PCI_DMA_ALLOC_COHERENT’
  *virt = PCI_DMA_ALLOC_COHERENT(wd->pci.pdev, size, &dma_addr);
          ^
/var/lib/dkms/ndiswrapper/1.60/build/ndis.c: In function ‘NdisMIndicateReceivePacket’:
/var/lib/dkms/ndiswrapper/1.60/build/ndis.c:2261:15: error: ‘struct net_device’ has no member named ‘last_rx’
   wnd->net_dev->last_rx = jiffies;
               ^
/var/lib/dkms/ndiswrapper/1.60/build/ndis.c: In function ‘EthRxIndicateHandler’:
/var/lib/dkms/ndiswrapper/1.60/build/ndis.c:2349:14: error: ‘struct net_device’ has no member named ‘last_rx’
  wnd->net_dev->last_rx = jiffies;
              ^
/var/lib/dkms/ndiswrapper/1.60/build/ndis.c: In function ‘NdisMTransferDataComplete’:
/var/lib/dkms/ndiswrapper/1.60/build/ndis.c:2464:14: error: ‘struct net_device’ has no member named ‘last_rx’
  wnd->net_dev->last_rx = jiffies;
              ^
scripts/Makefile.build:308: '/var/lib/dkms/ndiswrapper/1.60/build/ndis.o' &#53440;&#44191;&#50640; &#45824;&#54620; &#47749;&#47161;&#51060; &#49892;&#54056;&#54664;&#49845;&#45768;&#45796;
make[1]: *** [/var/lib/dkms/ndiswrapper/1.60/build/ndis.o] &#50724;&#47448; 1
Makefile:1550: '_module_/var/lib/dkms/ndiswrapper/1.60/build' &#53440;&#44191;&#50640; &#45824;&#54620; &#47749;&#47161;&#51060; &#49892;&#54056;&#54664;&#49845;&#45768;&#45796;
make: *** [_module_/var/lib/dkms/ndiswrapper/1.60/build] &#50724;&#47448; 2
make: &#46356;&#47113;&#53552;&#47532; '/usr/src/linux-headers-4.13.0-26-generic' &#45208;&#44048;
```

---

### Post by slickymaster on 2018-01-10
*Thread moved to **MINT**.*

---

### Post by mc4man on 2018-01-10
Ubuntu 16.04 doesn't install ndiswrapper by default, maybe ask on mint forums?

---

### Post by anselch1011 on 2018-01-10
OK! Thanks. I will ask on Mint forums :D

---

### Post by mc4man on 2018-01-10
I happened to have a mint 18.3 (cinnamon) install on another laptop that is on the hwe path so updated.
Saw same error about ndiswrapper - 
> ...
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
ERROR (dkms apport): [COLOR="#FF0000"]kernel package linux-headers-4.13.0-26-generic is not supported[/COLOR]
Error! Bad return status for module build on kernel: 4.13.0-26-generic (x86_64)
Consult /var/lib/dkms/ndiswrapper/1.60/build/make.log for more information.
...
But upon reboot it booted up ok
```
$ inxi -Fx
System:    Host: doug-Lenovo-IdeaPad-Y580 Kernel: 4.13.0-26-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.6.6 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Linux Mint 18.3 Sylvia
Machine:   System: LENOVO product: 2099 v: Lenovo IdeaPad Y580
...
Graphics:  Card-1: Intel 3rd Gen Core processor Graphics Controller
           bus-ID: 00:02.0
           Card-2: NVIDIA GK107M [GeForce GTX 660M] bus-ID: 01:00.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa) FAILED: nouveau
           Resolution: 1920x1080@59.93hz
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile
           GLX Version: 3.0 Mesa 17.2.4 Direct Rendering: Yes
....
```

---

### Post by anselch1011 on 2018-01-10
I cannot boot with 4.13.0-26.
I reported this problem at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742474](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742474) .

---

