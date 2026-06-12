---
title: "LTSP -  PXE - trying to load pxelinux.cfg/default"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by fusionp on 2012-09-05
Hi all, just searching for some help on what to check on my ltsp setup. I have configured my ltsp server with dhcp, and can verify that it is working as I have connected a laptop to the lan and receive the correct IP address and details.

However when I connect my thin client, it boots, receives it's IP, then begins loading, I receive the below message, however it does not progress from here.

Trying to load: pxelinux.cfg/default                        ok

These are the steps I followed.

"
sudo apt-get install nfs-kernel-server
sudo apt-get install ltsp-server-standalone openssh-server
sudo ltsp-build-client
sudo ltsp-update-sshkeys
sudo ltsp-update-image
Open the /etc/default/tftpd-hpa and edit first line Run_Daemon to &#8220;Yes&#8221; in place of NO.Save and Exit.
Now Open the /etc/ltsp/dhcpd.conf and change some values to the file as below.uncomment value next-server and put the server ip infromt of it ( next-server 192.168.0.1; )
add these two values below that :
allow booting;
allow bootp;
now go to the last line of the dhcpd.conf and it has a default value : filename ( &#8221;/ltsp/i386/nbi.img&#8221;; ) change that to ( filename &#8220;pxelinux.0&#8243;; )
Once done save and exit and restart the dhcp server /etc/init.d/dhcp3-server restart"

Any ideas of what I may try...I've searched but haven't found much, and I'm quite new to Linux so any help much appreciated.

---

### Post by Hawkier on 2012-09-24
man, just use this tutorial
[How to create a Ubuntu 12.04 x64 LTSP server with 32bit thin clients]("http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients")

you dont need to install nfs-kernel-server because its not used, nbd-server will be installed with ltsp-standalone.

and when you build your image use 32 bits architeture to clients:

```
ltsp-build-client --arch i386
```
att,
Luiz

---

