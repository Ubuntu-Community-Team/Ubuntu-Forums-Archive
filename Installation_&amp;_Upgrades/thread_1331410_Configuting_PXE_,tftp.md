---
title: "Configuting PXE ,tftp"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2009-11-19
I am setting up a tftp server want to know which directory/file I need to give the path of ISO on my NFS

---

### Post by Lars Noodén on 2009-11-19
How are you planning to deploy tftp?  If you have not made a choice yet, then I would recommend starting with dnsmasq.  

Are you trying to set up the ability to netboot the installation cd?

---

### Post by tapas_mishra on 2009-11-19
> **Lars Noodén said:**
> How are you planning to deploy tftp?  If you have not made a choice yet, then I would recommend starting with dnsmasq.  

Are you trying to set up the ability to netboot the installation cd?
Yes I am setting the ability to netboot the installation CD so need to know if I use NFS to host the images whats the problem or do I need to use apache or ftp necessarily if yes then some hint
the client machine is booting and asking me to enter hostname of the mirror from which ubuntu to download I want to do it locally from a locally mounted ISO

---

### Post by Lars Noodén on 2009-11-21
Ok the netboot itself goes via PXE and tftp.

That will load the installer image.  

The installer will then eventually start looking for packages, that's where you can use your cd or cd image, along with ftp, http or both.  

1) Install a web server, get it running.  Choose apache, lighttpd, or nginx.  It doesn't matter in this context at all which one.  

2) In the document root make a directory on which to mount the  cd or cd image.
```

sudo mkdir --mode=755 /var/www/ubuntu

```
3) Mount the cd image or cd .
```

# For a cd image:
sudo -o loop /home/me/ubuntu-9.10-server-amd64.iso /var/www/ubuntu

# For an actual cd, check for the right device name (e.g. from fstab):
sudo /dev/scd0  /var/www/ubuntu

```

4) For the ftp service, use **only** anonymous FTP.  Proftp and vsftp are two choices.  Set the home directory for the ftp user to the document root of your web server. 
```

sudo usermod -d /var/www ftp

```
You may need to add *pub* or other subdirectories using symlinks.

If all that is correct connecting to your server with FTP or HTTP should get you the contents of the CD.

---

### Post by Lars Noodén on 2009-11-21
If you have the cd or cd image mounted in /var/www/ubuntu, then you will have material for netboot here: /var/www/ubuntu/install/netboot/

If you are using dnsmasq for dhcp, pxe and tftp, then you must point the configuration file to the right boot image.  There are step by step directions for pxe booting with dnsmasq, very few steps actually.  

/etc/dnsmasq.conf should have something like this
```

# Enable dnsmasq's built-in TFTP server
**enable-tftp**

# Set the root directory for files availble via FTP.
**tftp-root**=/var/www/ubuntu/install/netboot

# Set the boot file name
**dhcp-boot**=ubuntu-installer/i386/pxelinux.0

```

YMMV.

If you are installing to a server, ie. a machine wasting no resources on graphics cards, then you should point to pxelinux.cfg.serial-9600 instead.

---

### Post by tapas_mishra on 2009-11-21
> **Lars Noodén said:**
> If you have the cd or cd image mounted in /var/www/ubuntu, then you will have material for netboot here: /var/www/ubuntu/install/netboot/

That is exactly where the problem is the CD I am mounting is not having a  install/netboot folder instead it has a directory named casper where it has initrd and vmlinuz some where I read for this I need a Live CD of Ubuntu
in the install directory I have following only 

```

root@tapas-laptop:/mnt/install# ls
mt86plus  README.sbm  sbm.bin

```

Just check the following link I downloaded netboot from Ubuntu  Jaunty repositories from here 
[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/)
they have an image named mini.iso I am not clear on what is that 


and thanks for the following tip
```

If you are installing to a server, ie. a machine wasting no resources on graphics cards, then you should point to pxelinux.cfg.serial-9600 instead.
```

---

### Post by tapas_mishra on 2009-11-22
Finally I found a solution the CDs named alternate have the netboot folder this is what is needed

---

### Post by tapas_mishra on 2010-05-15
I kept in /var/lib/tftpboot the files related to installtion 
the TFTP settings for booting via network
Following changes were made to config files


First file
/etc/inted.conf
```

tftp dgram udp wait root /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot
## netbios-ssn stream tcp nowait root /usr/sbin/tcpd /usr/sbin/smbd

```

Second file
/etc/default/atftp
```

USE_INETD=true
OPTIONS="--tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5 /var/lib/tftpboot"

```

Third file
/etc/default/tftp-hpa
```

#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"

```
Fourth file I touched was 
/etc/default/xinetd
```

# Default settings for xinetd. This file is sourced by /bin/sh from
# /etc/init.d/xinetd

# enable xinetd Inetd compat mode
INETD_COMPAT=Yes

# Options to pass to xinetd
#
# -stayalive comes by default : it can be removed if xinetd is expected
# not to start when no service is configured
#
XINETD_OPTS="-stayalive"

```



Then 5th file 
/etc/dhcp3/dhcpd.conf
/etc/dhcpd.conf
```

ddns-update-style none;
allow booting;
allow bootp;

option domain-name "www.yourdomainhere.com";
#option domain-name-servers ns1.example.org, ns2.example.org;

option domain-name-servers 4.2.2.6;

default-lease-time 600;
max-lease-time 7200;
log-facility local7;


# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

subnet 192.168.1.0 netmask 255.255.255.0 {
}

# A slightly different configuration for an internal subnet.
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.4 192.168.1.250;

option domain-name-servers 4.2.2.6;
option domain-name "internal.example.org";
option routers 192.168.1.250;
option broadcast-address 192.168.1.255;
default-lease-time 600;
max-lease-time 7200;
}
next-server 192.168.1.45;
filename "pxelinux.0";
option domain-name-servers 4.2.2.6;
option domain-name "internal.example.org";
option routers 192.168.1.250;
option broadcast-address 192.168.1.255;
default-lease-time 600;
max-lease-time 7200;
}
next-server 192.168.1.45;
filename "pxelinux.0";
```
Where next-server is IP of your DHCP server.

---

