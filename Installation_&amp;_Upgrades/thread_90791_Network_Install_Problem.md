---
title: "Network Install Problem"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by esvan on 2005-11-15
Hi,

I have been trying to install Ubuntu 5.10 over my LAN on my laptop.
I want to install it on my laptop through a network boot with my slackware box acting as DHCP and FTP server providing the install. 
I seem to be running in some problems along the way though, specifically when my laptop tries to load pxelinux.cfg/default after connecting. Here's what I've done up till now;

First off I downloaded the .iso (well duh :P), mounted it on /var/lib/tftpboot/ubuntu/ and then I set up DHCP on my slackware system with the following config:

```
ping-check = 1;
filename="ubuntu/install/netboot/pxelinux.0";
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.15;
}
ddns-update-style ad-hoc;
```

after that I started tftpd with the following command:
/usr/sbin/in.tftpd -l -s /var/lib/tftpboot

Then I booted my laptop over my LAN, everything went fine at first. It got an IP address assigned through dhcp, it logged into my ftp server just fine. It found the pxelinux.0 file and ran it.
After this it tried to load pxelinux.cfg/default but seemingly couldn't find it. Allthough it is very much present in the folder.

Here is what it says:

```
--Snip--

My IP Address seems to be C0A8010F 192.168.1.15
ip=192.168.1.15:0.0.0.0:0.0.0.0:255.255.255.0
TFTP prefix: ubuntu/install/netboot/
Trying to load: pxelinux.cfg/01-00-a0-cc-de-21-39
Trying to load: pxelinux.cfg/C0A8010F
Trying to load: pxelinux.cfg/C0A8010
Trying to load: pxelinux.cfg/C0A801
Trying to load: pxelinux.cfg/C0A80
Trying to load: pxelinux.cfg/C0A8
Trying to load: pxelinux.cfg/C0A
Trying to load: pxelinux.cfg/C0
Trying to load: pxelinux.cfg/C
Trying to load: pxelinux.cfg/default
Could not find kernel image: linux
boot: 
```

I'm a bit at a loss at what could be the issue, I've searched a while now and haven't really got any further. I hope some of you can shed some light on it maybe.

I have been semi-following this how-to: [http://gridpt1.fe.up.pt/mlopes/blog/index.php/ubuntu-network-install/](http://gridpt1.fe.up.pt/mlopes/blog/index.php/ubuntu-network-install/)

thanks.

---

### Post by esvan on 2005-11-16
anyone? :(

---

### Post by bram on 2008-02-22
After looking around for a while I found this, thanks to Geert Stappers stappers at stappers.nl 

 You have a incomplete configured DHCP server, 
 add the "next server" command in dhcpd.conf.
 [http://syslinux.zytor.com/archives/2005-September/005879.html](http://syslinux.zytor.com/archives/2005-September/005879.html)

So basically add to your host definition in the dhcpd.conf :
 next-server <ip of your dhcphost>;

And restart the service.
Reboot the host that has to netboot and everything should work.

It worked for me :)

Bram

---

