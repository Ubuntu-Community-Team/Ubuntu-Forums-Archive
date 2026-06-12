---
title: "Booting Ubuntu Desktop via PxE"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by jamesaepp on 2013-05-25
I have a pxe server (TFTP/NFS) set up to boot 12.04.2 desktop installs over the network. When a client finishes booting and has reached the desktop, under the network manager, it says the device is not managed. After completing installation, no network interface is available.. Computer boots, gets DHCP stuff
2. Is presented with menu, ubuntu 12.04 desktop amd64 is chosen
3. Basic stuff (vmlinuz.efi,initrd.lz) is loaded and nfs directory is mounted to /cdrom/ 
4. Normal boot

After getting to the desktop, the machine receives an IP, can access internet services (google homepage, everything), can install the OS, but shows the following: 

[IMG]http://i.imgur.com/TCvIbHe.png[/IMG]

This is a screenshot post-install: 

[IMG]http://i.imgur.com/d9mHxma.png[/IMG]

Thanks!

---

