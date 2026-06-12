---
title: "PXE installation problem"
date: 2017-02-06
forum: Installation &amp; Upgrades
---

### Post by michele.123456 on 2017-02-06
I've setup a PXE server and http server to install ubuntu 14.04 via http (I used linux&initrd.gz from the netboot folder of the ubuntu-14.04-server-amd64.iso).
This is my txt.cfg:
label install
    menu label Install
    menu default
    kernel linux
    append vga=788 initrd=initrd.gz locale=en_US console-setup/layoutcode=sl keymap=sl debian-installer/keymap=sl auto url=http://my_server_ip:my_server_port/my.seed

Inside my.seed I added the line:
d-i live-installer/net-image string [http://my_server_ip:my_server_port/iso/install/filesystem.squashfs](http://my_server_ip:my_server_port/iso/install/filesystem.squashfs)
Kernel and ramdisk are loaded and the installation starts to "Loading additional components " from the my_server_ip:my_server_port server.
filesystem.squashfs is never downloaded.
Then the installations fails with the message
  
[!!] Install the base system
Debootstrap Error
Failed getting Release file [http://my_server_ip:my_server_port/.../dists/trusty/Release](http://my_server_ip:my_server_port/.../dists/trusty/Release)
In the log I have some error:
base-installer: error: exiting on error base-installer/debootstrap-failed
....
What I expected is that instead of loading .debs files it should get the filesystem.squashfs from http and load it, but this never happened. 
Am I missing anything or doing anything wrong?
Thanks

---

