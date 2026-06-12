---
title: "How to prevent kubuntu from uninstalling current kernel header?"
date: 2022-07-13
forum: Installation &amp; Upgrades
---

### Post by halogenlamp on 2022-07-13
On kubuntu 21.01, if i try to uninstall anything or update software it tells me it will also uninstall linux-headers-5.16.#######-generic. Virtualbox requires this generic header to run, so i dont know why everything is demanding it removed or how to stop it.

edit: i dont know if it matters or if anyone is wondering why, but 5.16 is the last kernel with a generic header that includes dkms which is required for virtualbox.

---

### Post by TheFu on 2022-07-13
Assuming you mean 21.10, not 21.01, support for that release ends - this week.  It will be difficult to move to 22.04 soon after, so best to move now, ASAP.

To "hold" packages in APT, use the **apt-mark** command.

---

### Post by Impavidus on 2022-07-14
21.10 came with the 5.13 kernel, 22.04 comes with the 5.15 kernel. So what's this about the 5.16 kernel?

Is the package you want to keep autoremovable? Then mark it as manually installed. But for these kernel packages there's some magic going on, so that might not work. And why worry about removing 5.16.x when you still have 5.16.y?

---

### Post by &amp;KyT$0P# on 2022-07-14
Is this a System76 machine?
Is this the host OS or is it a VirtualBox guest?

Could you please post the outputs from running these commands in Terminal -
```
uname -a
apt-get -s autopurge
dpkg-query -W | grep -P -i '^linux'
```

> **halogenlamp said:**
> 5.16 is the last kernel with a generic header that includes dkms which is required for virtualbox.

VirtualBox has not used DKMS since a long time ago, and the latest version 6.1.34 should work with kernel 5.17 according to the [changelog]("https://www.virtualbox.org/wiki/Changelog").

---

### Post by SeijiSensei on 2022-07-14
Besides you can install dkms and its dependencies with
```
sudo apt install dkms build-essential
```
Even if it mattered for VirtualBox, it's not a limitation.

That said, I switched from VirtualBox to KVM virtual machines a year or more ago now. Functionality is built right into the kernel. You just need some additional software to create and manage virtual machines. [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

You can also convert VirtualBox disk images to ones in the qcow2 format that KVM uses: [https://www.tecmint.com/migrate-virtualbox-vms-into-kvm-vms/](https://www.tecmint.com/migrate-virtualbox-vms-into-kvm-vms/)

---

### Post by TheFu on 2022-07-14
I stopped using virtualbox around 2014, but moved to KVM as my primary VM hypervisor in 2010.  I started using VM tools in the 1990s and tried nearly all the different hypervisors before ending up on KVM + libvirt + virt-manager.  No regrets. It is a fantastic system, probably the fastest hypervisor in the world today regardless of the marketing by others and their license agreements which prohibit sharing any performance information (looking at you VMware).  

I used Xen for a few years. It was fine, but there were some issues after new kernels were installed which prevented some VMs from booting.
  
Virtualbox was the best choice for desktop-on-desktop VMs, before KVM got spice around 2016. Since then, there's really no comparison.

---

