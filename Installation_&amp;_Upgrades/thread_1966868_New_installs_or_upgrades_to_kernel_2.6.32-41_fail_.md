---
title: "New installs or upgrades to kernel 2.6.32-41 fail to boot"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by tc0nn on 2012-04-27
I don't know if this is specific to VMWare installs or all installs but I'm seeing this on my VMware ESXi 5.0 Lucid 10.4.4 vm's, as well as under fusion. If I do a apt-get dist-upgrade and allow it to install linux-image-2.6.32-41-server or if I create a new VM and do a brand new install with linux-image-server as the kernel choice, neither VM will boot properly. Boot process ends with an error pre-grub menu/prompt: error file not found you need to load the kernel first failed to boot both default and fallback entries vmware ubuntu upgrade

Workaround is to boot to a live CD, mount/chroot, uninstall 2.6.32-41 and then reboot to the older kernel. I haven't been able to isolate whether this is a grub issue or a kernel/initrd specific issue.

---

### Post by bmcgough on 2012-04-27
Having the same problem on real hardware. Also not sure if this is a grub issue or kernel issue. I am seeing this with reiser on /boot and / partitions and can fix it by installing with ext4 on /boot and /.

---

### Post by tc0nn on 2012-04-30
> **bmcgough said:**
> Having the same problem on real hardware. Also not sure if this is a grub issue or kernel issue. I am seeing this with reiser on /boot and / partitions and can fix it by installing with ext4 on /boot and /.

you might try a simple replacement of the kernel and see if that fixes it. Here's our fix:

apt-get install linux-image-2.6.32-40-server
apt-get remove linux-image-2.6.32-41-server

unfortunately we have to boot from a cd and chroot in just to do this. My specs are similar to yours. Boot/root w/reiser
/boot
/

---

### Post by guymauve on 2012-04-30
Hello,

Same thing here... I try by commenting menu.lst entry related to 2.6.32-41 without success. With ubuntu server 10.04.4 LTS I think I can't chroot with "Rescue broken system"??

Thanks for help!

Guy

EDIT : 
Maybe related : [https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/991548](https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/991548)

---

### Post by tc0nn on 2012-05-08
Just clarifying, this has nothing to do with VMWare, this install/upgrade from the archive.canonical repo kills a brand new dell M610/lucid.

---

### Post by tc0nn on 2012-05-11
Also seems to be specific to linux-image-2.6.32-41-server (not generic, generic seems to work fine)

---

### Post by daz101 on 2012-05-15
I don t run the server version and it also fails. The update shows as installed in synaptic but shows no sign in grub. I have manually updated grub to no effect.

---

