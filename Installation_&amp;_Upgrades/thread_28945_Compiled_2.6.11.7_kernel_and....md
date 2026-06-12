---
title: "Compiled 2.6.11.7 kernel and..."
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by zolookas on 2005-04-22
I ave successfuly compilded and installed 2.6.11.7 kernel, but when i try to boot linux it give me error:
```
Could not load /lib/modules/2.6.11.7/modules.dep: No such file or directory
``` 
My grub configuration:
```

title		Ubuntu, kernel 2.6.11.7 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.11.7 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

``` 

P.S. My english is not very good  :neutral:

---

### Post by heimo on 2005-04-22
To me it looks like *depmod -a *wasn't run and the file with information about kernel modules is missing. I can't verify the details at this moment, you may need to give a parameter for depmod if you're running it while using another kernel (not the one that you're creating the modules.dep file for).
 
Check parameters: depmod -h
 
 
EDIT: It could be like this: (I am not sure)
```
   
cd /lib/modules/2.6.11.7/
depmod -a

```

---

### Post by zolookas on 2005-04-22
[QUOTE=heimo]To me it looks like *depmod -a *wasn't run and the file with information about kernel modules is missing. I can't verify the details at this moment, you may need to give a parameter for depmod if you're running it while using another kernel (not the one that you're creating the modules.dep file for).
 
Check parameters: depmod -h
 
 
EDIT: It could be like this: (I am not sure)
```
   
cd /lib/modules/2.6.11.7/
depmod -a

```[/QUOTE]
I did that:
```
cd /lib/modules/
depmod -v 2.6.11.7 -a
``` 
I and get many errors
```
...
/lib/modules/2.6.11.7/kernel/fs/fat/fat.ko needs "load_nls": /lib/modules/2.6.11.7/kernel/fs/nls/nls_base.ko
/lib/modules/2.6.11.7/kernel/fs/fat/fat.ko needs "unload_nls": /lib/modules/2.6.11.7/kernel/fs/nls/nls_base.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_call_read_data": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_create_transport": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_put_call": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_add_service": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_put_connection": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_call_write_data": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_put_transport": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_call_abort": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_del_service": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_create_connection": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.11.7/kernel/fs/afs/kafs.ko needs "rxrpc_create_call": /lib/modules/2.6.11.7/kernel/net/rxrpc/rxrpc.ko
...
```

---

### Post by alastair on 2005-04-22
Tell us all the steps you did to compile/install the new kernel e.g.

download source
copy tar.gz to ...
unpack using : tar xvfj ...
cd ...
...
make xconfig
...
etc.

---

### Post by zolookas on 2005-04-22
```
cd /usr/src
rm -f linux
ln -s linux-2.6.7.11 linux
cd linux
make menuconfig
make bzImage
make
make install
make modules
make modules_install
```

---

### Post by alastair on 2005-04-22
I thought "make install" wanted to do a "depmod" to sort out modules? In other words, I think the order is best as :

make
make modules
make modules_install
make install

and check you have /boot sorted i.e. vmlinuz, initrd, System.map etc.

I haven't done this on Ubuntu/Debian - so am not sure if this "auto-edits" the GRUB config.

---

### Post by myer0052 on 2005-04-23
> My grub configuration:

title Ubuntu, kernel 2.6.11.7
 root (hd0,4) 
kernel /boot/vmlinuz-2.6.11.7 root=/dev/hda5 ro quiet splash 
initrd /boot/initrd.img-2.6.10-5-386 
savedefault 
boot


I believe you want to get rid of the initrd line. Or you'll need to do:

"mkinitrd"

I'm not sure how to properly use it. The easiest way is to skip the initrd and recompile your kernel with your system bus and filesystem type and other hardware that you need to boot loaded into the kernel and not as modules. That way you do not need to load a initrd image before you load your kernel. Or you might want to check up on the "Debian" way to build kernels, do a search on make-kpkg.

---

### Post by Camo R on 2005-04-26
My first ever post on this board....

Running kernel 2.6.11.7 on an omnibook 6100 installed from vanilla source of kernel.org (2.6.11.* in repos always locked up my system). 
Notes: 
1. Kernel doesn't show up as installed in synaptics.
2. Boot up doesn't display the usual jibba jabba, (but it boots up obviously)
3. *make sure your menuconfig double checked twice" (busted usb drives, have to recompile)

this is how i got mine to work, not a defacto way of doing things i guess but heck it worked.

pre-compile work: apt-get install build-essential bin86 libncurses-dev
1.  Get kernel source from kernel.org, in this case 2.6.11.7
2.  untar and cd into directory
3.  make mrproper
4.  make menuconfig
5.  make
6.  make modules_install
7.  cp arch/i386/boot/bzImage /boot/kernel-2.6.11.7 *personalize and put your   name i.e /boot/camokernel-2.6.11.7 hehe* (this installs the kernel)
8.  cp System.map /boot/System.map-2.6.11.7 (install map file)
9.  cp .config /boot/config-2.6.11.7 (to save your confile from from menuconfig)
10. edit /boot/grub/menu.lst to reflect the new kernel: 

      title 		Ubuntu, Kernel 2.6.11.7
      root	       (hd0,1)
      kernel	      /boot/kernel-2.6.11.7   root=/dev/hda2 ro quiet splash
      boot

11. mkdir /etc/grub && (run this command)
      >ln -s /boot/grub/menu.lst /etc/grub        
12. Reboot and don't be scared when nothing appears on the screen for a while.
      
Got this install sequence from a couple of sites, please feel free to show the error of my ways or alternate ways of doing it. Will try and build a deb package and see how that works out.

---

