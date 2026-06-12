---
title: "PXE boot diskless server - LiveCD on nfsroot"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by new2xen on 2008-02-29
Hello all,

I would like to setup diskless clients that boot over PXE and run the root on NFSroot mounted.  I attempted to following the instructions from the Wiki:  [https://wiki.ubuntu.com/LiveCDNetboot](https://wiki.ubuntu.com/LiveCDNetboot) and I am currently stuck.

Setup:  PXE, TFTP, NFS and DHCP server is setup (I am able to use the setup to do diskless clients with Fedora6.).  I am currently testing how to build Ubuntu diskless client utilizing the Live CD distro.

1.  /pxelinux.cfg/default contains the following:

DEFAULT vmlinuz-2.6.22-ub 
APPEND root=/dev/nfs nfsroot=192.168.16.5:/export/images/ubuntu710_x86-64 initrd=initrd.img ip=dhcp

The files kernel and initrd are in the /tftpboot directory:

ls /tftpboot
pxelinux.cfg
initrd.img
vmlinuz-2.6.22-ub
pxelinux.0

2.  NFS PXE and TFTP boot setup is all fine (as I mentioned diskless boot works with a fedora image).

3.  Upon PXE booting a diskless client is able to:  get DHCP IP address, get the initrd, loads drivers, etc.... then after a while it gets stuck with the following messages scrolling until it reaches the (initramfs) prompt.

Begin :  Running /scripts/nfs-premount ....
Done.
Mount:  Device or resource busy.
Done.
Begin:  Running /scripts/nfs-bottom ....
Done.
Mount:  Device or resource busy.
Done.
Begin:  Running /scripts /init-bottom ...
Done.
| 
|
more other messages scrol, until this one disconcerting message appears:

target FS does not have /sbin/init

then the prompt:

#(initramfs)

.........................................................

Is there something I am missing in the steps I based my configuration upon? 

thanks in advance,

Vince.

---

### Post by dannyboy1121 on 2008-03-15
This forum is great!! 2 weeks and no reply. Did you ever get this working?

|'ve got a diskless server running on 7.04 so I have some experience. All I can say is that when I set mine up, there was no nfs boot time support in the kernel. I had to compile my own and switch nfs on as a boot time option.

The reason I'm browsing the forum now is that I'm checking to see if it's now included.

---

