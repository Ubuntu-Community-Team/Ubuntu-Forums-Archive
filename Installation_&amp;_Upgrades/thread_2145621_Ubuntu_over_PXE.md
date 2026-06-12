---
title: "Ubuntu over PXE"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by jamesaepp on 2013-05-16
[COLOR=#222222][FONT=Times New Roman][SIZE=2]The goal: Boot Ubuntu 12.04 over network using NFS, TFTPD-HPA, and dhcp

DHCP is provided by a pfsense router. This has been forwarded to the IP and filename pxelinux.0
TFTPD-HPA is started by init.d and NFS is by itself to start.

In /etc/inetd.conf I have: 
 [COLOR=#000000]
tftp    dgram    udp   wait    root    /usr/sbin/in.tftpd/usr/sbin/in.tftpd -s /var/lib/tftpboot

I installed nfs-kernelserver and in /etc/exports I added this:

/var/lib/tftpboot/0      192.168.1.0/24(ro,sync,insecure,all_squash)[/COLOR][/SIZE][/FONT][/COLOR]

[FONT=Times New Roman][SIZE=2]Under the /var/lib/tftpboot/ folder, I have some stuffs:
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
/var/lib/tftpboot/[/SIZE][/FONT] 
   [FONT=Times New Roman][SIZE=2]<DIR> 0[/SIZE][/FONT] 
   [FONT=Times New Roman][SIZE=2]pxelinux.0[/SIZE][/FONT] 
   [FONT=Times New Roman][SIZE=2]<DIR> pxelinux.cfg[/SIZE][/FONT] 
   [FONT=Times New Roman][SIZE=2]<DIR> syslinux
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
The 0 folder will contain all future media
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]The pxelinux.0 originated from the syslinux folder (see below)
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]The pxelinux.cfg folder has the default file in it for initial connection
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]The syslinux folder has all files originally found in /usr/lib/syslinux/*[/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=2]            The pxelinux.0 file was copied from here.
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
After that, in the 0 directory I extracted all of the files from the ubuntu iso to a folder called ubuntu
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
I then copied the vmlinuz and initrd.lz files from /var/lib/tftpboot/0/ubuntu/casper to /var/lib/tftpboot/0/ubuntu
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
My pxelinux.cfg/default is as follows:
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
UI syslinux/menu.C32
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]PROMPT 0
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
LABEL UBUNTU[/SIZE][/FONT] 
       [FONT=Times New Roman][SIZE=2]MENU LABEL UBUNTU[/SIZE][/FONT] 
       [FONT=Times New Roman][SIZE=2]KERNEL 0/ubuntu/vmlinuz[/SIZE][/FONT] 
       [FONT=Times New Roman][SIZE=2]APPEND boot=casper netboot=nfs nfsroot=192.168.1.184:/var/lib/tftpboot/0/ubuntu initrd=0/ubuntu/initrd.lz
[/SIZE][/FONT][COLOR=#222222][FONT=Times New Roman][SIZE=2]
When I boot a client, however, I get this: [http://i.imgur.com/5hkRUkD.png](http://i.imgur.com/5hkRUkD.png) (This occurs on both VMs and real machines) Typing results in nothing, but the keyboards are not the issue, as if one of laptops turns off one of its screens, I can activate it by using a keypress.

[/SIZE][/FONT][/COLOR]

---

### Post by dslowik on 2013-06-05
You didn't copy everything over to [COLOR=#000000][FONT=Times New Roman]var/lib/tftpboot/0/ubuntu[/FONT][/COLOR].  A .disk folder was missed.

---

