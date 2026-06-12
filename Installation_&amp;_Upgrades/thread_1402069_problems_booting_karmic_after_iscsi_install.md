---
title: "problems booting karmic after iscsi install"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by runelind on 2010-02-08
Having previously booted my htpc off a USB flashdisk, I wanted to try iSCSI as I believe my flashdrive is slowly dying. I pxebooted the installer and logged into the iscsi target during the installation process, everything went fine so far. The trouble started when I attempted to boot the current system, it would just go into an endless loop of trying to load off iSCSI, and no debug messages could be seen.

My iSCSI server is running off FreeBSD 8 using isc-dhcpd and the built in tftp server. Here is the relevant info:

iSCSI server IP 10.50.3.5

#/tftpboot/ubuntu-installer/i386/pxelinux.cfg/default

include ubuntu-installer/i386/boot-screens/menu.cfg
default ubuntu-installer/i386/boot-screens/vesamenu.c32
prompt 0
timeout 30

LABEL 1
        MENU LABEL ^Ubuntu Linux 9.10
        MENU DEFAULT
        KERNEL 10.50.3.5::/boot/vmlinuz-2.6.31-19-generic
        APPEND ip=dhcp root=/dev/sda0 ISCSI_INITIATOR=iqn.1994-04.org.netbsd.iscsi-target ISCSI_TARGET_NAME=iqn.1994-04.org.netbsd.iscsi-target:target3 ISCSI_TARGET_IP=10.50.3.5 ISCSI_TARGET_PORT=3260 initrd=initrd3-ng.img
  



#dhcpd.conf
group {
                next-server 10.50.3.5;
                filename "pxelinux.0";
                option root-path "iscsi:10.50.3.5::::iqn.1994-04.org.netbsd.iscsi-target:target3";
                host htpc-wired
        {
                hardware ethernet 00:01:2E:26:2F:E4;
                fixed-address 10.50.3.203;
        }
}
]




When I try to PXE boot the system, it just boots into the graphical installer with my custom Ubuntu 9.10 as an option, but when I pick that option nothing happens. Because it goes into the graphical (text-based) installer, there are no debug messages.

Has anyone done anything like this that can point me in the right direction?

Thanks

---

