---
title: "Gutsy Desktop on KVM"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by s_soriga on 2008-01-02
I tried to install ubuntu-7.10-desktop on KVM 58 running on ubuntu 7.10 desktop. It's ok till starting X. It's possible to be something about framebuffer. How can I disable framebuffer at boot time. It looks like debian-installer/framebuffer=false doesn't work anymore. 
Is there a way of installing gutsy desktop on KVM. Gutsy server works.

---

### Post by s_soriga on 2008-01-03
If you installed kvm from source (kvm-58 in this case), start installing with: 
qemu-system-x86_64 -no-acpi -m 386  -hda Gutsy.img -cdrom ubuntu-7.10-desktop-i386.iso  -boot d

Obs. If you have a core 2 duo, as in this case, you can append -smp 2. 

Immediatly after, press SHIFT and answer no. After that, ENTER. [http://kvm.qumranet.com/kvmwiki/Intel_Real_Mode_Emulation_Problems](http://kvm.qumranet.com/kvmwiki/Intel_Real_Mode_Emulation_Problems)

You can press ALT+F1 to bypass the splash. After X server fails to start 6 times in a row, press alt+f1 and type startx. Normal install. 

At the end , before press restart, remove splash from kernel line in /boot/grub/menu.lst and type update-rc.d -f gdm remove (Yes, you'll have to type startx in the command line after restart).

Obs. Afer kernel updates don't forget to remove splash from menu.lst. 

that's it.

---

