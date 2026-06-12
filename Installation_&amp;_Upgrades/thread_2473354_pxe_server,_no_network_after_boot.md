---
title: "pxe server, no network after boot"
date: 2022-04-01
forum: Installation &amp; Upgrades
---

### Post by karolkopytko on 2022-04-01
Hi.

TLDR: after booting by PXE clients get IP by DHCP, but have no internet access.

Full story.
I have Ubuntu server (20.04.4), which is also my Internet router. I've setup PXE. Clients can boot by network. They get proper IP, but cannot download ISO file.
Clients are regular PC and VM (VirtualBox).

What I've done:
- setup DHCP server (working fine, IP is assigned)
- setup IPTABLES - network traffic for that machines when booted to other OS is working  fine (yes, they are getting same IP by DHCP as when booted by PXE)
- setup PXE server[INDENT]- pxelinux.0 was copied from /usr/lib/PXELINUX
- .c32 files to /tftp folder from /usr/lib/syslinux/modules/bios
[/INDENT]
[INDENT]- clients boot, PXE menu is displayed; they get proper IP from DHCP
[/INDENT]
- copied initrd and vmlinux files from [http://releases.ubuntu.com/focal/ubuntu-20.04.4-live-server-amd64.iso](http://releases.ubuntu.com/focal/ubuntu-20.04.4-live-server-amd64.iso) (from /casper/)

pxelinux.cfg/default:
```
LABEL Ubuntu
MENU LABEL Ubuntu 20.04 SERVER
KERNEL /ubuntu/vmlinuz
INITRD /ubuntu/initrd
APPEND root=/dev/ram0 ramdisk_size=1500000 ip=dhcp url=http://releases.ubuntu.com/focal/ubuntu-20.04.4-live-server-amd64.iso

```

Result of booting:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290208&stc=1[/IMG]

Thanks for any help.


edit: 
client IP: 10.0.0.41
router: 10.0.0.1

ip route from client booted by PXE:
```
10.0.0.0/24 dev enp0s3 scope link  src 10.0.0.41
```

---

---

### Post by karolkopytko on 2022-04-02
Shame on me.
I've set up ISC-DHCP-SERVER incorrectly.

In dhcpd.conf I had 
```
option broadcast-address 10.0.0.1;
```
not
```
option broadcast-address 10.0.0.255;
```

After that change default ip route is added to clients.

---

