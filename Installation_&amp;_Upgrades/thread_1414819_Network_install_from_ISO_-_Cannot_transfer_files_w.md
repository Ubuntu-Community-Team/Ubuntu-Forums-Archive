---
title: "Network install from ISO - Cannot transfer files with Apache Http - Please help!"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by Zalanthas on 2010-02-24
Hi,

I have tftpd-hpa and dhcp3-server up and running.

I just want to install server edition via network, from the host machine (my laptop, running ubuntu 9.10) with an ISO file (ubuntu 8.04 32-bit server edition). 

I managed to boot the client machine with pxe-netboot technique, but instead downloading all the files from internet, I need to do this process directly from ISO.

To transfer ISO from host to client, I also installed Apache. I unpacked ISO file into /var/lib/tftpboot/server/

I created a link to the Apache root: /var/www
```

ubuntu@ubuntu:/var/www$ ls
returns => index.html  server

```server folder is the place where I unpacked the ISO.

My dhcp3-server has this setup and it works well with netboot, but I don't know how to add Apache to the formula to transfer the iso file from host to client.

Firewall is disabled.

This is my edited /etc/dhcp3/dhcpd.conf file.
```

host pxeinstall {
  hardware ethernet 00:06:29:DE:E3:CD;

  fixed-address 192.168.2.4; (client IP)

  next-server 192.168.2.2; (host IP)

  filename "/server/install/netboot/pxelinux.0"; (relative to tftpboot)
}

subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.2 192.168.2.5;
  option routers 192.168.2.1;
}

```
When I pxe-boot the client, the process comes to a halt when tftp server is trying to access to pxelinux.0 file.

I got thls error:
PXE-T00: Permission denied
PXE-E36: Error received from TFTP server


I have no experience with Apache... so I think there is a problem with my IP addresses.. Do I need to use 127.0.1.1 instead of 192.168.2.1 (my routers IP)?


Any help is appreciated.

PS: I am a novice :)

Thanks.

---

### Post by yogesh.girikumar on 2010-02-24
Hi,


       Make sure that the permissions for the files and directories are set to allow access from outside. Something like 655 should do.
   ```
$ sudo chmod -R 655 /var/lib/tftpboot/server/
```      You can do it without an Apache server.


       See: [http://ubuntuforums.org/showthread.php?t=1413126](http://ubuntuforums.org/showthread.php?t=1413126)

---

### Post by Zalanthas on 2010-02-24
That is the best documentation on the subject I've seen so far. It is clean and to the point. Many thanks.

Could you add your guide to the ubuntu installation documentation section in the website? I am sure many will benefit out of it.

I just have one question:

Is it possible to use ISO while netbooting? After I netboot with pxelinux.0, I don't want to download all the files off of Internet, I would like to use the ISO file that I already saved to the host machine.

---

### Post by yogesh.girikumar on 2010-03-01
Hi,


       Yes! It is possible to use ISO for netbooting. You have to have an alternate install ISO for this. Here is a snippet of the directory tree structure for an alternate installation ISO ( two levels deep ).
   ```
.
|-- README.diskdefines
|-- cdromupgrade
|-- dists
|   |-- karmic
|   |   |-- Release
|   |   |-- Release.gpg
|   |   |-- main
|   |   `-- restricted
|   |-- stable -> karmic
|   `-- unstable -> karmic
|-- doc
|   `-- install
|       `-- manual
|-- install
|   |-- README.sbm
|   |-- initrd.gz
|   |-- mt86plus
|   |-- netboot
|   |   |-- pxelinux.0 -> ubuntu-installer/i386/pxelinux.0
|   |   |-- pxelinux.cfg -> ubuntu-installer/i386/pxelinux.cfg
|   |   |-- ubuntu-installer
|   |   `-- version.info
|   |-- sbm.bin
|   `-- vmlinuz
|-- isolinux
```     You can see that most of the files that we fetched from the internet are available in the ISO itself. You can copy these files to the /tftpboot directory. The files needed for this are found under the directory "install/netboot".


       The .deb files necessary for the basic installation are present in the 'pool' folder and are fetched during the installation. Any extra packages to be installed can be fetched from the Internet.

---

