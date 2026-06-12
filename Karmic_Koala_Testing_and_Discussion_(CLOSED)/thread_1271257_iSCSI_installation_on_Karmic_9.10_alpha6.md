---
title: "iSCSI installation on Karmic 9.10 alpha6"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sub.mesa on 2009-09-20
Hello forum,

Any users here who tried using iSCSI to make a diskless Ubuntu desktop system? It would solve alot of my headaches, and so i'm investigating this possibility. I did so after having heard iSCSI support in one of the karmic alpha's was improved. 

Now i downloaded and tested the 6th alpha of karmic amd64 iso using virtualbox 3.0.6 VM, and it works but there is no option to install to an iSCSI server on the network, not even after installing the open-iscsi packages using synaptic.

So if anyone could explain how iSCSI support for Ubuntu works i would be grad, i didn't found to much info about this using Google strangely - something that is generally not a good sign of its support. Any feedback is welcome. :)

---

### Post by sub.mesa on 2009-09-20
Oh i forgot, some links:

[https://wiki.ubuntu.com/Installer/iSCSI](https://wiki.ubuntu.com/Installer/iSCSI)
[https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/236640](https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/236640)
[https://blueprints.launchpad.net/ubuntu/+spec/foundations-karmic-iscsi-installer-support](https://blueprints.launchpad.net/ubuntu/+spec/foundations-karmic-iscsi-installer-support)

The release notes say:

> The iSCSI installation process has been improved, and no longer requires iscsi=true as a boot parameter; the installer will offer you the option of logging into iSCSI targets if there are no local disks, or you can select "Configure iSCSI" in the manual partitioner. 

Putting the root filesystem on iSCSI is now supported.

My experience is otherwise, in the partition manager there is no option at all when no disks are detected. I think it should display a friendly message saying "Oops no disk found, this can be due to several reasons:
- Your harddrive is not detected properly (submit hardware information link)
- Your harddrive is not properly connected or has malfunctioned
- You want to use iSCSI to install to another computer on the local network (advanced)

Just an example, but it would be both user friendly and offer power users to click that iSCSI button/link very fast and enter the required info for the iSCSI authentication and proceed with the partitioner.

---

### Post by nivex on 2009-10-01
You said you tried installing open-iscsi with synaptic, leading me to believe that you tried from the Desktop CD.  I was told that only the Server CD has the necessary bits to do the iSCSI install.

That said, I had tried alpha3, alpha4, and just tried the beta Server CD this afternoon and could not get it to prompt me for iSCSI information at all.  I'll probably file a bug for this and refer back here.  I imagine they're a bit tired of hearing from me :)

---

### Post by sub.mesa on 2009-10-02
I got feedback on my bug report, which is located here:
[https://bugs.launchpad.net/ubuntu/+bug/435290](https://bugs.launchpad.net/ubuntu/+bug/435290)

Apparantly this was a bug and its been fixed and should be in the next beta releases of karmic. I'll try the desktop edition again to see if this works now.

IMO, the server edition is the one that would be the iSCSI-target; and the desktop edition would use the iSCSI-initiator. I guess iSCSI should just work on both cd types. I do agree that regular computer users shouldn't be bothered with iSCSI questions per-default, which might confuse even experienced users thinking to believe this is about SCSI disks; while iSCSI is a SAN protocol.

---

### Post by sub.mesa on 2009-10-08
I thought it not working on the desktop ISOs was a bug as well, and i was confused with the alternate ISO thinking it was the server one. Anyway i apologise since a karmic server daily build ISO did allow me to use iSCSI.

In fact, it went fairly easy, it autodetected my iSCSI-target and installed happily to it. However, rebooting ofcourse didn't work yet -- i had to make it boot from network too. I had hoped to get this working and report back, but i guess i could use some help with this, since im kind of stuck.

I managed to setup TFTP service and DHCP service correctly so PXE network boot now works, using pxelinux i created a nice menu which can load Ubuntu from the network, or Memtest86. When loading Ubuntu, it can load the kernel but the kernel won't pick up the iSCSI device as the root device, and panics thereafter.

Since i don't get any message about iSCSI during boot process (though i can't scroll back due to the panic it seems), i believe the kernel is not aware it needs to boot from iSCSI. Though there is some documentation about Ubuntu and iSCSI, most of it is focused on systems with a local disk as opposed to diskless systems. So i couldn't find enough information.

I believe i need an initrd image with modules for iSCSI support. I guess the initrd has to be the same of that of the current kernel, or distribution. So i have to use the cd to create one. But how? And my second issue is with the contents of the pxelinux configuration file (/pxelinux.cfg/DEFAULT), currently i use:

```
DEFAULT vesamenu.c32
PROMPT 0
MENU TITLE PXE Network boot
TIMEOUT 30

LABEL 1
  MENU LABEL ^Ubuntu Linux 9.10
  MENU DEFAULT
  KERNEL 10.10.0.23::/linux
  APPEND root=/dev/sda0 ISCSI_INITIATOR=iqn.2999-09.jp.ne.peach.istgt ISCSI_TARGET_NAME=iscsi:10.10.0.23::::iqn.2007-09.jp.ne.peach.istgt ISCSI_TARGET_IP=10.10.0.23 ISCSI_TARGET_PORT=3260
  INITRD initrd 
  IPAPPEND 1

LABEL 2
  MENU LABEL ^Memory Test
  KERNEL 10.10.0.23::/mt86plus

LABEL disk
  MENU LABEL ^Local hard drive
  LOCALBOOT 0
```

and my dhcpd.conf contains:

```
host 10.10.0.24
{
 # PXE
 hardware ethernet <MAC ADDR removed for privacy>;
 fixed-address 10.10.0.24;
 filename "/pxelinux.0";
 option root-path "iscsi:10.10.0.23::::iqn.2007-09.jp.ne.peach.istgt";
 next-server 10.10.0.23;
}
```

The files on TFTP server are: initrd, linux, mt86plus, pxelinux.0, vesamenu.c32, pxelinux.cfg (directory) containing file "default". This file is the configuration file for pxelinux. I don't know if the contents are correct, first i need an iSCSI capable initrd file so the kernel can try to login with iSCSI which hasn't happened since the install. The install was easy, booting afterwards is the hard part. :)

Some official documentation about the required files/setup after installing root to iSCSI would be nice, i couldn't find too much reliable info on the web.

Maybe with somebody's help, i can make diskless ubuntu desktop a reality. :)

---

### Post by sub.mesa on 2009-10-15
ouch, i've been at this for too long. But it still does not work. Currently i've progressed to the part of creating an initrd from scratch with their own init file. It looks good; it tries to load iscsi modules and connect to the iSCSI server; but its halted because a kernel driver doesn't work.

It exits with the error "-1 Unknown symbol in module". Not much info on the web, though i suspect this is a module from a different kernel version or something. But, i got all files from an installed Ubuntu 9.10 daily snapshot; there should be no change between kernel and modules.

Anyone can help here? These messages i get when booting via PXE network, left some non-relevant stuff out:

```

Loading libcrc32c.ko module
insmod: error inserting `/lib/modules/libcrc32c.ko`: -1 Unknown symbol in module
Loading crc32c.ko module
Loading mii.ko module
Loading 8139too.ko module
[ ... ] 8139too Fast Ethernet driver 0.9.28
Loading e100.ko module
[ ... ] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[ ... ] e100: Copyright(c) 1999-2006 Intel Corporation
Loading e1000.ko module
(.. removed some lines ..)
Loading tulip.ko module
Loading tg3.ko module
Loading scsi_transport_iscsi.ko module
[ ... ] Loading iSCSI transport class v2.0-870.
Loading libiscsi.ko module
Loading iscsi_tcp.ko module
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_segment_done
[ ... ] iscsi_tcp: Unknown symbol iscsi_segment_seek_sg
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_segment_unmap
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_hdr_recv_prep
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_cleanup_task
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_conn_setup
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_r2tpool_alloc
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_r2tpool_free
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_task_xmit
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_recv_skb
[ ... ] iscsi_tcp: Unknown symbol iscsi_segment_init_linear
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_conn_get_stats
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_task_init
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_dgst_header
[ ... ] iscsi_tcp: Unknown symbol iscsi_tcp_conn_teardown
insmod: error inserting `/lib/modules/iscsi_tcp.ko`: -1 Unknown symbol in module
Mounting /proc filesystem
warning: can't open /etc/fstab: No such file or directory
(.. removed some lines ..)
iscsistart: transport class version 2.0-870. iscsid version 2.0-870
iscsistart: version 2.0-870
iscsistart: Logging into <target address>
iscsistart: initiator reported error (12 - iSCSI driver not found. Please make sure it is loaded, and retry the operation)
(.. removed some lines ..)
```How can the iscsi modules be not compatible with the shipped kernel? Did i do something wrong? Anyone who has ever done this before? Anyone at all who has a working iSCSI-on-root setup on Ubuntu?

I'm getting the feeling i'm the only one in the world trying to make Ubuntu boot off the network using iSCSI. Ive also never heard of a single person who got this working. Yet -- the release notes say it should. But no body can tell how. :(

---

### Post by sub.mesa on 2009-10-15
Also, i could not find some modules, they are:

jbd.ko
mbcache.ko
ext3.ko

scsi_mod.ko
sd_mod.ko

Could it be these are integrated in the kernel, how can i check this?

---

### Post by sub.mesa on 2009-10-16
I've got this working! Finally, with alot of effort and some very long nights.. i can boot from PXE and mount iscsi disk as root. The solution was in the initrd file as i suspected. 

Also, i had to upgrade to the 15 october snapshot; earlier packages still contained bugs with iSCSI kernel modules giving unknown symbol errors, preventing mounting iscsi on root. I also had to re-install to my iscsi target, because the old packages were still preventing me from booting successfully from iSCSI. And the last hurdle was silencing /etc/network/interfaces file which was destroying my network interface killing the iSCSI linkup. You need a static IP configuration in this file.

I'll put up a tutorial as soon as i've got things sorted out. Right now i got the shell prompt and i'm doing "sudo apt-get install ubuntu-desktop" to get a desktop system from the ubuntu-server cd. Its not possible yet to install directly from the Ubuntu desktop cd; kind of a shame i think. No server wants it root mounted over network, but desktop/clients might.

---

### Post by sub.mesa on 2009-10-16
I do want to post my final pxelinux.cfg file though:

```
DEFAULT vesamenu.c32
PROMPT 0
MENU TITLE PXE Network boot
TIMEOUT 30

LABEL 1
  MENU LABEL ^Ubuntu Linux 9.10
  MENU DEFAULT
  KERNEL 10.10.0.23::/vmlinuz-2.6.31-14-server
  APPEND ip=bootp root=/dev/sda1 iscsi_initiator=iqn.ubuntu.istgt iscsi_target_name=iqn.2007-09.jp.ne.peach.istgt:disk0 iscsi_target_ip=10.10.0.23 iscsi_target_group=1 iscsi_target_port=3260 initrd=initrd-ng3.img

LABEL 2
  MENU LABEL ^Memory Test
  KERNEL 10.10.0.23::/mt86plus

LABEL disk
  MENU LABEL ^Local hard drive
  LOCALBOOT 0
```This will pick the local IP data from DHCP configuration, select 10.10.0.23 as the remote iSCSI server (the target), and load the initrd-ng3.img file as initial ramdisk. This file i had to create myself; the initrd file shipped with Ubuntu is unusable for iSCSI; you need to adapt it and bring all the modules and binaries in. All the pre-boot files (the pxelinux.cfg/vmlinuz-2.6.31-14-server/initrd-ng3.img should be on the TFTP server. In my case i'm using FreeNAS as server, which can do both TFTP and iSCSI-target.

Right now i'm going to stress test to see if this remains stable over time. Finally its possible; diskless ubuntu! Hurray!

---

