---
title: "Network install issues"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by innovativerc on 2006-10-08
Hi

i am trying to install ubuntu from network, as PC im installing on has no floppy drive, CD drive etc so trying to boot from network to get things going.

i have followed this site for all info on setting things up (DHCP,TFTP etc)
[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

i am trying to install ubuntu-6.06.1

i downloaded the ISO but this did not have the NETBOOT files under install folder, so i got the netboot files from here
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/netboot.tar.gz)


the system will start to boot up from the LAN but it is getting stuck part way through on pxelinux.cfg/default file

here is output from system i am installing on..

> 
PXE entry point found (we hope) at 9E68:00F6
My IP address seems to be C0A8015A 192.168.1.90
ip=192.168.1.90:0.0.0.0:192.168.1.1:255.255.255.0
TFTP prefix: netboot/
trying to load: prelinux.cfg/01-00-40-63-cb-32-ec


this is where it gets stuck at 
trying to load: prelinux.cfg/01-00-40-63-cb-32-ec


logs in /var/log/messages from server system
> Oct  8 21:01:31 localhost dhcpd: DHCPDISCOVER from 00:40:63:cb:32:ec via eth0
Oct  8 21:01:32 localhost dhcpd: DHCPOFFER on 192.168.1.90 to 00:40:63:cb:32:ec via eth0
Oct  8 21:01:33 localhost dhcpd: DHCPREQUEST for 192.168.1.90 (192.168.1.12) from 00:40:63:cb:32:ec via eth0
Oct  8 21:01:33 localhost dhcpd: DHCPACK on 192.168.1.90 to 00:40:63:cb:32:ec via eth0
Oct  8 20:01:33 localhost in.tftpd[6138]: RRQ from 192.168.1.90 filename netboot/pxelinux.0 
Oct  8 20:01:33 localhost in.tftpd[6138]: tftp: client does not accept options 
Oct  8 20:01:33 localhost in.tftpd[6139]: RRQ from 192.168.1.90 filename netboot/pxelinux.0


Thanks for any help
Rob

---

### Post by somnoliento on 2006-10-29
Rob

The PXE boot should realize that there's no pxelinux.cfg/<MAC> and move on to asking for pxelinux.cfg/default

(The "client does not accept options" message is common and harmless)

Did you check permissions on the files (and dirs) under the TFTP root?

What is the section for this host on your dhcpd.conf file?

---

