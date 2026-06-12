---
title: "Wanting to install Arch inside of Ubuntu with KVM."
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by Dave_Connor on 2010-07-30
Since I have some free space on my internal drive I would like to try out virtual machine. I want install Arch Linux under 4gb for partition settings, 1 CPU and 1024mb of RAM. It boots fine from X86 iso until it gets to "Processing Udevs" on the screen and X freezes along with KVM. I can kill KVM with "sudo kill -9 $(pidof kvm); sudo /etc/init.d/kvm restart" but still run into the same issue. I am not sure what this issue is. 

Could it be the arch distro itself since it is working fine on older desktop I have on the hard disk. Any help here ?

Edit: Just a KVM issue with restarting KVM and restart virt-manager after that quick fix. Works great :)

---

