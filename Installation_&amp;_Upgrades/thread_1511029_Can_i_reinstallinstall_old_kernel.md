---
title: "Can i reinstall/install old kernel?"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by jafarul on 2010-06-16
i was trying to fix my laptops's FN key. i found one solution on ubuntu forum, it suggest me to install the new linux kernel ad so i dit. 

Kernel Before: 2.6.35-020632rc2-generic (The original - From CD)
Kernel After: 2.6.35-020635rc1-generic (Download)

Problem: 
i) Lagged internet connection :Error: Resolving Host takes to   long(My desktop works fine)
ii)Error during Boot : [2683.238664] bt_intr_complete: hci0 ef1d4a00 failed to submit (1)



i was wondering if there is a was to revert to the old kernell.
any other solution also would be a big help  :p

---

### Post by darkod on 2010-06-16
Installing a new kernel doesn't remove the old ones.

You should see options for different kernels in the boot menu.

If you have only ubuntu and don't get a boot menu, you need to start pressing Shift after the BIOS finishes but before ubuntu starts loading. That will show you the menu.

Select the older kernel to load, and after that remove the newer kernel if you want.

---

### Post by jafarul on 2010-06-16
Thanks. it works. I've been online for one hour now with out interruption. just one last question. how do i remove the newly installed kernel safely?

---

### Post by darkod on 2010-06-16
I prefer Synaptic, it should be listed there. Just open Synaptic in System-Administration, and in the search box type linux-image.

It will show you all kernels installed, among other packages. Click on the one you want to remove and select Mark for Complete Removal.

I think you can do the same with linux-headers, but just removing linux-image will remove the kernel itself.

To update the grub2 menu run

sudo update-grub

---

### Post by jafarul on 2010-06-17
it works :eek: problem solved thanks

---

