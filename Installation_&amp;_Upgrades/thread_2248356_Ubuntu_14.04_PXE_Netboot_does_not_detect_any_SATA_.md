---
title: "Ubuntu 14.04 PXE Netboot does not detect any SATA hard drives"
date: 2014-10-14
forum: Installation &amp; Upgrades
---

### Post by chris303 on 2014-10-14
Hi there,

I have set up a DHCP / TFTP / HTML server client for PXE netbooting and I successfully installed Ubuntu 12.04 LTS on a dedicated machine on my network completely hands off with a preseed configuration. Now I would like to upgrade the machine running DHCP / TFT / HTML server to install Ubuntu 14.04 LTS on my dedicated machine. I have upgraded the netbooter to 14.04 on my TFTP server and mounted the Ubuntu 14.04.01 LTS server ISO on my HTML server. Now everything works during the network installation until the installer reaches the step where the hard drives shall be detected. There, no hard drives are detected (I have two SATA HDDs on my dedicated machine) and I also checked this via the build in console and there are no hard drives (e.g. /dev/sda).

So I tried a lot of things to solve that problem but I ended up by installing Ubuntu 14.04.01 LTS server via an USB stick and that worked fine (hdds are detected). So there must be some issue with the netboot 14.04 installer or maybe a kernel option that I am missing. In the following code there are my current kernel parameters:

```

default install-14.04-hands-off
label install-14.04-hands-off 
        menu label ^Install 14.04 Hands Off
        kernel ubuntu-installer/amd64/linux
    append vga=normal biosdevname=0  initrd=ubuntu-installer/amd64/initrd.gz netcfg/choose_interface=eth0  netcfg/no_default_route=true netcfg/get_nameservers=192.168.1.100  netcfg/get_hostname=ubuntu domain=example.com locale=en_US.UTF-8  debian-installer/country=US debian-installer/language=en  debian-installer/keymap=de-latin1-nodeadkeys  console-keymaps-at/keymap=de-latin1-nodeadkeys auto-install/enable=true  preseed/url=192.168.1.100/pre.seed DEBCONF_DEBUG=5

```

Any idee how to solve that problem or what I have to check that the hard disks are detected when installing ubuntu via PXE boot?

---

