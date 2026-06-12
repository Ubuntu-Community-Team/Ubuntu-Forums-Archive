---
title: "Qemu - definitely to slow!"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by Skyo on 2011-05-07
Hey guys,

im runnig Ubuntu 11.04 on my machine. (quite old, pentium 4 3,2 ghz HT)
Im trying now to virtualize a n ubuntu machine with qemu, though it is super slow. 
(boot +-45 minutes, havent succesfully installed yet)


These are my terminal commands:
> 
qemu-img create -f qcow2 ubuntu.img 10G
Formatting 'ubuntu.img', fmt=qcow2 size=10737418240 encryption=off cluster_size=0 

qemu -m 1536 -hda ubuntu.img -cdrom ubuntu-11.04-desktop-i386.iso -boot d
open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support
qemu: pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin"
So, have i completely failed at VM's? How to speed up, why KVM does not exist? :(
If KVm loaded properly, would it influence the network behaviour? :\
(my VM will communicate with the Android Emulator, which is qemu-based.)


Peace! :popcorn:

---

### Post by dino99 on 2011-05-07
it all depend on the available ram on your system and on the graphic card/chipset.

i use virtualbox on my system (4 Gb) and dont know about qemu

---

### Post by Skyo on 2011-05-07
The paramter -m 1536 assures 1536mb of RAM for the VM, sufficient, isnt it?

---

