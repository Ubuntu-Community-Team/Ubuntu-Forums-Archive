---
title: "cloud-init ubuntu22 server bare metal"
date: 2023-06-09
forum: Installation &amp; Upgrades
---

### Post by kleijheeg on 2023-06-09
Since the last couple of days I am working on a autoinstaller for ubuntu 22 desktop/server.

On a virtual machine everything is working fine, boots nicely in ipxe and the installer is working fine with the user-data file.
Now I am facing a problem on the bare metal machine, the user-data will not be loaded into the installer.

In the beginning I had a problem with starting the bare metal  machine. It was stuck during the boot at "Reached target Host and Network  Lookups"
After reading this post: [https://askubuntu.com/questions/1238070/deploy-ubuntu-20-04-on-bare-metal-or-virtualbox-vm-by-pxelinux-cloud-init-doesn](https://askubuntu.com/questions/1238070/deploy-ubuntu-20-04-on-bare-metal-or-virtualbox-vm-by-pxelinux-cloud-init-doesn)
I have changed the ```
ds=nocloud-net;s=${base-url}/
``` to ```
ds=nocloud-net\;s=${base-url}/
``` and that works for me.
That problem has been solved but since that change the user-data will also not loading on my virtual machine.

Does someone know a solution for loading the user-data on a bare metal machine.
Only need help with the bare metal problem because the virtual machine is only for testing.


1. Configuration for the ipxe.

```
:jammy-desktop
set base-url http://server.example.com/iso/ubuntu/22.04
kernel ${base-url}/vmlinuz
initrd ${base-url}/initrd
imgargs vmlinuz initrd=initrd cloud-config-url=/dev/null ip=dhcp url=${base-url}/ubuntu-22.04-live-server-amd64.iso autoinstall ds=nocloud-net\;s=${base-url}/
```

2. user-data

```
autoinstall:
  version: 1
  identity:
    hostname: ubuntu-server
    password: "$6$exDY1mhS4KUYCE/2$zmn9ToZwTKLhCw.b4/b.ZRTIZM30JZ4QrOQ2aOXJ8yk96xpcCof0kxKwuX1kqLG/ygbJ1f8wxED22bTL4F46P0"
    username: ubuntu
```

---

### Post by MAFoElffen on 2023-06-10
I think it is your user-data file...

I don't do PXE this way anymore, so not sure on where to point it via that. If I do PXE deployments, I now use FOG Server...

But for Cloud Images, I do use user-data cloud-init files in various ways. I used these as reference:
[https://dev.to/otomato_io/automating-custom-iso-with-cloud-init-2lc2](https://dev.to/otomato_io/automating-custom-iso-with-cloud-init-2lc2)
[https://www.pugetsystems.com/labs/hpc/ubuntu-22-04-server-autoinstall-iso/](https://www.pugetsystems.com/labs/hpc/ubuntu-22-04-server-autoinstall-iso/)
[https://www.golinuxcloud.com/pxe-boot-server-cloud-init-ubuntu-20-04/](https://www.golinuxcloud.com/pxe-boot-server-cloud-init-ubuntu-20-04/)
[https://github.com/frederickding/Cloud-Init-ISO](https://github.com/frederickding/Cloud-Init-ISO)
[https://www.digitalocean.com/community/tutorials/how-to-use-cloud-config-for-your-initial-server-setup](https://www.digitalocean.com/community/tutorials/how-to-use-cloud-config-for-your-initial-server-setup)

And came up with this to setup my user using a cloud init file, which I named as 'cloud-init.cfg' and compressed as an ISO (for my application of)
```

#cloud-config, cloud-init.cfg
system_info:
  default_user:
    name: ubuntu
    home: /home/ubuntu

password: ubuntu
chpasswd: { expire: False }
hostname: ubuntu-cloud-00

```
Where yours fails right off, as a cloud config file, is that the first line must start out with the string '#cloud-config'...

---

### Post by kleijheeg on 2023-06-16
I did include the #cloud-config i the cloud-init but forgot to copy paste it in the forum post.
Going to experiment a bit otherwise going to search for a other solution.

---

### Post by MAFoElffen on 2023-06-16
Just an idea--- The biggest issues I see with people having errors in cloud-init files is format errors = spacing and indentation...

It uses yaml, which is like Python in the formatting of. One extra space somewhere, or a tab instead of spaces... and it breaks. I usually run my file through a yaml format verifier to check them.

---

### Post by kleijheeg on 2023-06-16
The yaml syntax is working fine, otherwise I also should have problems on my virtual machine.
I am going to look for possible network driver issues.

I noticed that before booting in the installer the network is working fine but during the start of the installer I noticed some network issues.

---

