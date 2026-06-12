---
title: "Disklessboot problem"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by ChosSimbaOne on 2012-10-30
Hi Ubuntuforums.org
I'm not sure if this is the correct subforum, so please feel free to move it if so. Couldn't decide between this and the networking.

I'm currently experienceing many difficulties pxebooting the latest LTS 12.04.

I've had followed this guide: [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

I've tried 3 different "images", one copied from a installed client, one newly debootstrap installation, and an upgraded debootstraped installation.

I have a cluster setup, running a deboostrapped ubuntu 10.04 LTS, with no problem. I therefore assumed that it would be no hassle to setup a new installation.

My default file in my tftpboot folder is as follow:
```
DEFAULT precise_pxe/vmlinuz netboot=nfs boot=nfs root=/dev/nfs initrd=precise_pxe/initrd.img ip=192.168.2.102:192.168.2.3:192.168.2.1:255.255.255.0:cub2:eth0:none nfsroot=192.168.2.3:/q/system/precise_pxe,rw,v3 rw pci=noacpi ipv6.disable=1 panic=10
```

I now experience the following problem:
```
Unable to connect to system bus: failed to connect to socket /var/run/dbus/system
_bus_socket: No such file or directory
```

Let me know if you need more information, hope that you can help me with my problem.

Best regards.

---

### Post by ChosSimbaOne on 2012-11-07
I did not find a solution to this problem. What i did was redo the guide all over again, and it seems to be working probaly now.

Best Regards.

---

