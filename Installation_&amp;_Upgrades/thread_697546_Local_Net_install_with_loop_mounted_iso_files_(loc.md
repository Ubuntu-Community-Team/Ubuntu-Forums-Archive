---
title: "Local Net install with loop mounted iso files (localnetinstall)"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by flygin on 2008-02-15
I don't know if I carry owls to Athens... but it just worked:

loop mounting a CD image (iso) and performing a netinstall without connection to the internet (localNetinstall).


I first loop mounted the iso file.
then I changed the path for tftp-hpa directly to the netboot directory on the iso (/usr/sbin/in.tftpd -l -s /home/ith/iso/mp-ubuntu-6.10-server-i386/install/netboot). udhcpd points to pxelinux.0 

To offer the loop mounted iso image on http, I used kpf (root directory is the mount point for the loop)

it booted straight.

when it asked for a mirror, I entered 
192.168.0.1:8003 (server ip with port)

next window, I replaced the string "/ubuntu/" with:
//
this is the secret! (at least for me it was ....) without the slashes it does not accept the previous settings and defaults archive.ubuntu..... with the slashes it swallowed it!

there were a few "retry"s needed when loading but it worked (maybe speed problem).

A loop mounted iso file (ubuntu 6.10 server) 
pxe boot (udhcpd and tftpd-hpa)

so, loop mounted iso-image for local netinstall (without internet)

(haven't finished the installation, was just a test machine) 

updates follow

let me know if a full description is needed or I just missed the right page ....

---

