---
title: "booting to an nbd root"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by neil.the.blue on 2016-06-20
Hello,

I have been playing with dnsmasq and pxe recently and looking at options for diskless systems. 

I would now like to install a small desktop system that can boot via PXE and get the root fs from nbd. 

Now I can get PXE running fine and booting with kernels and initrd images from pxe/http. So I would like to know if there is a standard way to get ubuntu to run the root fs over nbd. I assume the process would be something like load the nbd module in initrd, and use an nbd client to change to an nbd root device, but I am not sure of the details. I would appreciate any advice on this, as most of the google searches seem to be for LTSP or just booting a live cd.

Thanks
Neil

---

### Post by u1106 on 2017-01-13
Somewhat late reply, just found this when searching myself...

I agree, there doesn't seem to be much on the net about running the rootfs from nbd. 

There is a commercial cloud provider scaleway, which offers bare metal ARM servers and virtual Intel servers. All their disks are accessed via nbd. They have Ubuntu images for both types of servers. At least on ARM they don't use an Ubuntu kernel, but a mainlaine kernel (if I understood it correctly).

Not sure whether the images can be downloaded directly, but the source code to create them is on [https://github.com/scaleway](https://github.com/scaleway)

I have used xenial and yakkety on ARM. Both boot fine. (Yakkety images had a bug related to /etc/machine_id. I don't know whether the image has updated, but at least the image generation code has changed and I just fixed the file manually on my machine)

However, shutting down does not work well. With their older kernel the shutdown seems to work, but I have the strong feeling it just aborts before the rootfs is mounted read-only. So not a clean shutdown.

With the newer kernel shutdown is even worse. It either hangs or hits a kernel bug. 

I think the common problem for all problems is that the network interface is turned of while the shutdown is still progressing. I tried to fix than in the related systemd unit, but now I hit a kernel bug.

I have not studied in detail how their images differ from default Ubuntu installations. They certainly don't use NetworkManager and networking.service is masked.

Disclaimer: I guess the Forum rules (which I have not read) do not allow advertising. I mention a commercial provider only for the technical merit of their Open Source work. This is not a advertisement to buy anything from them. I could share experiences in a more suitable forum.

---

