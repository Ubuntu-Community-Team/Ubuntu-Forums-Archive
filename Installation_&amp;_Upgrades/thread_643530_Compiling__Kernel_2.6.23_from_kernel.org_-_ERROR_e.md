---
title: "Compiling  Kernel 2.6.23 from kernel.org - ERROR every time"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by helix on 2007-12-17
I mistakenly deleted the folder "fglrx" inside my /usr/src directory and now when I'm trying to compile this kernel, I get issues because it is looking for that folder and can't find it. 

I've reinstalled fglrx drivers and the folder has not reappeared. 

I have been loosely following this guide: [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)  as a reference.

If anyone can lead me in the right direction, I'd apreciate it. Thanks!

---

### Post by nowshining on 2007-12-18
do thiis

in terminal type

sudo nautilus

press ctrl + h

navigate to root (a link should be on the left pane)  find .trash and the folder u deleted should be in there.... or have u deleted the file from there? if so just move it back. I don't get why u need it tho, i don't have a fglrx folder  in the /usr/src directory and i compiled and installed kernel 2.6.23.11 fine.

---

### Post by helix on 2007-12-18
I tried what you said but its gone.

This is the exact message.

        done
make[1]: Entering directory `/usr/src/modules/fglrx'
./debian/rules:41: *** the unpacked source (8.42.3-1) doesn't match the fglrx-kernel-source package ()
./debian/rules:42: *** if this is not what you want, erase /usr/src/modules/fglrx and start over
dh_testdir
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules
make[2]: Entering directory `/usr/src/linux-2.6.23'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c:365: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:366: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_check_pci’:
/usr/src/modules/fglrx/firegl_public.c:1990: warning: ‘pci_find_slot’ is deprecated (declared at include/linux/pci.h:481)
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_pci_find_device’:
/usr/src/modules/fglrx/firegl_public.c:2019: warning: ‘pci_find_device’ is deprecated (declared at include/linux/pci.h:480)
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_vm_test_and_clear_dirty’:
/usr/src/modules/fglrx/firegl_public.c:2544: error: implicit declaration of function ‘ptep_test_and_clear_dirty’
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_pci_find_slot’:
/usr/src/modules/fglrx/firegl_public.c:2852: warning: ‘pci_find_slot’ is deprecated (declared at include/linux/pci.h:481)
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_request_irq’:
/usr/src/modules/fglrx/firegl_public.c:2962: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:64)
/usr/src/modules/fglrx/firegl_public.c:2962: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_pte_phys_addr_str’:
/usr/src/modules/fglrx/firegl_public.c:3536: error: implicit declaration of function ‘pte_read’
/usr/src/modules/fglrx/firegl_public.c:3538: error: implicit declaration of function ‘pte_exec’
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:5439: error: expected specifier-qualifier-list before ‘kmem_cache_t’
/usr/src/modules/fglrx/firegl_public.c: In function ‘KAS_SlabCache_Initialize’:
/usr/src/modules/fglrx/firegl_public.c:5478: error: ‘kasSlabCache_t’ has no member named ‘routine_type’
/usr/src/modules/fglrx/firegl_public.c:5479: error: ‘kasSlabCache_t’ has no member named ‘lock’
/usr/src/modules/fglrx/firegl_public.c:5480: error: ‘kasSlabCache_t’ has no member named ‘name’
/usr/src/modules/fglrx/firegl_public.c:5484: error: ‘kasSlabCache_t’ has no member named ‘cache’
/usr/src/modules/fglrx/firegl_public.c:5485: error: ‘kasSlabCache_t’ has no member named ‘name’
/usr/src/modules/fglrx/firegl_public.c:5485: error: too many arguments to function ‘kmem_cache_create’
/usr/src/modules/fglrx/firegl_public.c: In function ‘KAS_SlabCache_Destroy’:
/usr/src/modules/fglrx/firegl_public.c:5508: error: ‘kasSlabCache_t’ has no member named ‘cache’
/usr/src/modules/fglrx/firegl_public.c:5518: error: ‘kasSlabCache_t’ has no member named ‘cache’
/usr/src/modules/fglrx/firegl_public.c:5520: error: ‘kasSlabCache_t’ has no member named ‘cache’
/usr/src/modules/fglrx/firegl_public.c: In function ‘KAS_SlabCache_AllocEntry’:
/usr/src/modules/fglrx/firegl_public.c:5555: error: ‘kasSlabCache_t’ has no member named ‘routine_type’
/usr/src/modules/fglrx/firegl_public.c:5556: error: ‘kasSlabCache_t’ has no member named ‘lock’
/usr/src/modules/fglrx/firegl_public.c:5580: error: ‘kasSlabCache_t’ has no member named ‘cache’
/usr/src/modules/fglrx/firegl_public.c:5583: error: ‘kasSlabCache_t’ has no member named ‘lock’
/usr/src/modules/fglrx/firegl_public.c:5591: error: ‘kasSlabCache_t’ has no member named ‘cache’
/usr/src/modules/fglrx/firegl_public.c: In function ‘KAS_SlabCache_FreeEntry’:
/usr/src/modules/fglrx/firegl_public.c:5619: error: ‘kasSlabCache_t’ has no member named ‘routine_type’
/usr/src/modules/fglrx/firegl_public.c:5620: error: ‘kasSlabCache_t’ has no member named ‘lock’
/usr/src/modules/fglrx/firegl_public.c:5632: error: ‘kasSlabCache_t’ has no member named ‘cache’
/usr/src/modules/fglrx/firegl_public.c:5635: error: ‘kasSlabCache_t’ has no member named ‘lock’
make[3]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1
make[2]: *** [_module_/usr/src/modules/fglrx] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.23'
make[1]: *** [build] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx'
Module /usr/src/modules/fglrx failed.
Hit return to Continue

---

### Post by nowshining on 2007-12-18
oh okay i see try going to my website in my sig on how to compile and what u need to compile and follow the directions. (it's feisty some - xx link)

---

### Post by nowshining on 2007-12-18
oh also 

in the 2.6.23.x source directory

issue

make clean

& try again

---

