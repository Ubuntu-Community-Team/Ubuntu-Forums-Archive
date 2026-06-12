---
title: "Pxe image from persistent USB Livecd 10.10 install"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by drbubbles on 2010-12-19
I've got 10.10 nicely configured on a headless box running from a persistent USB image that has been suitably tweaked for my needs. Now I want to make a pxe boot image of this setup in case the USB fails or I mess up the installation somehow. I can pxe boot it to standard pxe images, so that is fine. However, when I follow the method to make a pxe image of a working system, ([https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)) I get stuck at the first step making an  initrd.img because the USB install (created using pendrivelinux, which works really well!), for some reason doesn't have vmlinuz In the /boot dir. There is a link to it but the actual file isn't at the end of the link. I assume the system knows about one somewhere on the USB stick  as the system is running! (very well in fact! Proxy server, VPN server, jack and my midi kbd with knobs works well with various synth programs). This is why I now want to make an image, as it it really good! And pxe booting is super fast.

Any ideas how to make initrd.img from the pendrivelinux persistent livecd USB install of ubuntu 10.10? Or is there another way? (ok, there is always another way :) but which is it? :)
Thanks!

---

### Post by ndog on 2011-03-06
Can I please bump this? I also am trying to make a persistent ubuntu 10.10 PXE boot environment? can it be done? is it possible? I use NFS

```
LABEL UBUNTU1010
    MENU LABEL ^2. Ubuntu 10.10
    kernel os/ubuntu_maverick/vmlinuz
    append boot=casper netboot=nfs nfsroot=192.168.1.22:/exports/ubuntu_maverick initrd=os/ubuntu_maverick/initrd.lz -- quiet

```

---

