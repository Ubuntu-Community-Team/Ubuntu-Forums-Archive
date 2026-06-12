---
title: "unable to do unattended build of ubuntu 18 over pxe"
date: 2019-01-18
forum: Installation &amp; Upgrades
---

### Post by chrysek on 2019-01-18
I have no idea what I am missing with ubuntu 18. I created preseed.cfg file, pretty much tried few examples from the net plus my old ubuntu 16
I did download latest iso from ubuntu (18.04.1), unpacked it and I did put it on my tftp/nfs server.

then in my pxe boot I did specify all the parameters. Anyway here is what I have

LABEL Ubuntu 18.04.1 - testing 10
	kernel boot/ubuntu/18.04.1/casper/vmlinuz
	append ip=dhcp boot=casper auto url=http://10.10.10.10/tftpboot/boot/ubuntu/18.04.1/casper/preseed.cfg netboot=nfs nfsroot=10.10.10.10:/tftpboot/boot/ubuntu/18.04.1/ initrd=boot/ubuntu/18.04.1/casper/initrd debug-ubiquity automatic-ubiquity debconf/priority=critical locale=en_US console-setup/ask_detect=false console-setup/layoutcode=us netcfg/choose_interface=auto toram acpi=off --

I did try pretty much so many APPEND options but none seem to work, I always get to the welcome screen where I need to select language, network, packages, user setup etc.

Please help, I am loosing my mind with this setup.

Regards,

Chris

---

### Post by chrysek on 2019-01-18
[SIZE=3][FONT=arial]so I found somewhere that ubuntu live server image does support now [COLOR=#242729]subiquity installer? and it does not support [/COLOR][/FONT][/SIZE][COLOR=#242729][FONT=Arial][SIZE=3][FONT=arial]Debian installer anymore? Is that correct?[/FONT][/SIZE]

[/FONT][/COLOR]

---

### Post by chrysek on 2019-01-18
I don't now wha tI am doing wrong, maybe its just my bad luck with this v18.
I did try to download the alternative 18.04 version, but there is no casper, so I can only do the netboot, but I have issue with interface, I am unable to select different interface other than eno1 on my system. I have server with enp4s0f1 interface and I need to select that one somehow, I did try to append different keywords to make it recognize it, but it only does go trough checking the network dhcp/static ip on eno1 only.

what are my options? I can't seem to be able to use live server image to do unattended build, I did try to follow steps found in documents, this forum and web, but I am unable to get rid of the screen where I need to select languages, when I try alternate image I am stuck with wrong interface which is not connected to the network and never will. Can someone point me to the way or help me with unattended build of 18.04 server (not the desktop) please.

---

