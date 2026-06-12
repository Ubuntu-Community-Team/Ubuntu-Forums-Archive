---
title: "Cannot install Ubuntu server from PXE over NFS"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by jaroon on 2014-03-31
I've had this issue for years and I've finally wasted enough time to need to complain about it. I haven't had this issue with any other distro, I know I am doing something wrong with my kernel appends but I can't figure it out. My goal is to be able to install ubuntu server from my private network without having to go over the internet to pull down resources during the install. I simply want to mount my NFS share as a `cdrom' and perform the standard ubuntu install and I can't figure it out.

My kernel options in the PXE menu:

```
&#9484;&#9472;[arbitrium]&#9472;[/pxe/ubuntu/13.10/x86_64]
&#9492;&#9472;&#9472;&#9596; cat ../../ubuntu.menu
LABEL 1
        MENU LABEL Ubuntu 13.10 (64-bit)
        KERNEL ubuntu/13.10/x86_64/install/vmlinuz
        APPEND root=/dev/nfs netboot=nfs nfsroot=192.168.0.10:/pxe/ubuntu/13.10/x86_64 initrd=ubuntu/13.10/x86_64/install/initrd.gz ramdisk_size=10000 ip=dhcp
```

With this config I can load the vmlinuz and initrd and then go through the keyboard menus then the installer fails to find the cdrom. I narrowed this down some what to the fact that there is no networking for whatever reason with these kernel options. Going into a second term ( alt+F2 ) and running `ip a' shows only loopback is configured and I cannot configure an eth0 interface.

I can get ubuntu server installed using the `./install/netboot/ubuntu-installer/i386/initrd.gz' initrd which appears to not use the NFS server at all and pulls down all the install files from a nearby mirror, in my case the US mirror. I confirmed this by blocking my box's IP from anywhere but my NFS server on my router:

```
root@shields:~# iptables -I INPUT 1 -d 192.168.0.109 ! -s 192.168.0.10 -j DROP
root@shields:~# iptables -I FORWARD 1 -d 192.168.0.109 ! -s 192.168.0.10 -j DROP

```

And also by digging around in the BusyBox shell:

```
ps
...
2187 root 2212 S sh -c wget -q http://us.archive.ubuntu.com/ubuntu/di
...
```

`ps' on the BusyBox shell doesn't support any of the usual flags so I only have the above.

This setup works fine with CentOS which I just installed with the following:

```
LABEL 2
        MENU LABEL CentOS 6.5 minimal (64-bit)
        KERNEL centos/6.5/x86_64/mini/images/pxeboot/vmlinuz
        APPEND method=nfs:192.168.0.10:/pxe/centos/6.5/x86_64/mini lang=us keymap=us ip=dhcp ksdevice=eth0 noipv6 initrd=centos/6.5/x86_64/mini/images/pxeboot/initrd.img ramdisk_size=10000
```

If anyone can shed some light on installing ubuntu server ( not the live cd ) from NFS or confirm that this is not possible it'd be greatly appreciated.

-- Shields

---

