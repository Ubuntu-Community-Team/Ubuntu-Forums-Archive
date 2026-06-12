---
title: "Hangs, then crashes after &quot;update-initramfs: deferring update (trigger activated)&quot;"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by ManuelOKelly on 2007-11-14
I recently upgraded to Gutsy, I don't know if that had something to do with this. I also installed Cryptsetup while using feisty and now while many packages seem to have upgraded,  my other upgrades are being blocked.

When I run the command:

When new updates are available I open the update program and it sometimes installs them. Then it defers the update to setup cryptsetup. For some reason at this point it hangs, then my screen freezes and I am forced to reboot.

I have done two things so far. I tried to reinstall initramfs-tools, but I can't change anything until dpkg is satisfied. How do I get around this?

```

manuel@edniacthethird:~$ sudo apt-get --reinstall install initramfs-tools
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
manuel@edniacthethird:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up cryptsetup (2:1.0.5-2ubuntu2) ...
update-initramfs: deferring update (trigger activated)
dpkg: error processing cryptsetup (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Errors were encountered while processing:
 cryptsetup

```

I don't know what else to attach, I will try to check frequently.

---

### Post by ManuelOKelly on 2007-11-14
No ideas?

---

