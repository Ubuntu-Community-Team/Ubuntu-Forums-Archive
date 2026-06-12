---
title: "Ubuntu Server Installation: NO CD, NO floppy, NO usb."
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by WolfLust on 2011-02-10
Hello all,

I have an old Intel server with Centos running on it, and I would like to remove Centos and replace it with Ubuntu Server 10.04 LTS 32bit.

This server cannot boot from USB, CD, nor floppy.

The BIOS doesn't even have these features, and doesn't offer a Network Boot feature. However, by hitting F12 I can attempt to Netboot (which currently doesn't boot).

I installed dhcp/tftp on my gateway with no luck. 

There's no relevant error logs on my gateway.

Here's a sample of my dhcp config:

```
ddns-update-style interim;
allow booting;
allow bootp;

subnet 192.168.0.0  netmask 255.255.255.0 {
        range 192.168.0.10 192.168.0.13;
        option routers 192.168.0.1;
        option broadcast-address 192.168.0.255;
         }
#columbia is the name of the server I would like to replace Centos with Ubuntu on it.
host columbia {
  filename "ubuntu/install/netboot/pxelinux.0";
  next-server 192.168.0.1;
  hardware ethernet 00:07:E9:04:1D:5E;
  fixed-address 192.168.0.3;
}

# DNS IP:
option domain-name-servers 192.168.0.1;

```

And here's a copy of my TFTP settings:

```
service tftp
{
        disable = no
        socket_type             = dgram
        protocol                = udp
        wait                    = yes
        user                    = root
        server                  = /usr/sbin/in.tftpd
        server_args             = -v -s /tftpboot
        per_source              = 11
        cps                     = 100 2
        flags                   = IPv4
}

```

Both dhcp and tftp are surely running.



Now, if you could offer a different method of performing this installation then it's no problem (such as via Grub if possible). Whatever gets it done :P

Much thanks and please let me know if you need anything else.

---

### Post by dino99 on 2011-02-10
if netinstall cant be done, then maybe you can take the hdd into an other pc to make the ubuntu installation then reinstall the hdd on that server

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by perspectoff on 2011-02-10
> **dino99 said:**
> if netinstall cant be done, then maybe you can take the hdd into an other pc to make the ubuntu installation then reinstall the hdd on that server



+1

Moving the hdd to another PC, installing, and moving it back ends up being the easiest solution by far. I've resorted to it several times.

---

### Post by WolfLust on 2011-02-10
Sounds the simplest :D

Wouldn't that created conflicts regarding MOBO/CPU info if I install it on one PC then move it to another?

---

### Post by WolfLust on 2011-02-10
I re-installed DHCP and TFTP from scratch, re-wrote the config for both, and kept re-trying netboot till it eventually worked.

I would've used your recommendation but this is the only SCSI HDD and the only SCSI compatible hardware that I have around here.

Installation is around 63% now. *fingers crossed*.

Much thanks!!

---

