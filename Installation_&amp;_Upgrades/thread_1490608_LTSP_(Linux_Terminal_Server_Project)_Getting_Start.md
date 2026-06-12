---
title: "LTSP (Linux Terminal Server Project) Getting Started - Help!"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by webkris on 2010-05-22
As a way to save money and introduce Linux to a corporate environment - I'm testing LTSP in Ubuntu 10.04

**Here's what I've found, what I fixed, and what I'm stuck on:**

First - the install has been covered elsewhere, but I grabbed the Alternate .iso and hit F4 at the first screen. Then selected Install LTSP Server

**Ubuntu 10.04 Linux Terminal Server Project Issues**
[B]#1
The DHCP client is set to boot the image from i386.tmp and not i386.[/B] This causes "file not found" on PXE boot.
There is NO i386.tmp directory - yet the dhcpd.conf file points to it. This one took me a while to figure out and I almost gave up on LTSP because of it.
Changing this in dhcpd.conf allows PXE boot.
*sudo pico /etc/ltsp/dhcpd.conf*

```

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 10.0.1.0 netmask 255.255.255.0 {
    range 10.0.1.100 10.0.1.150;
    option domain-name "example.com";
    option domain-name-servers 8.8.8.8;
    option broadcast-address 10.0.1.255;
    option routers 10.0.1.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {

```

[B]#2
No GATEWAY in IP settings in the config.[/B] *This _may_ have been because I tried to configure the eth0 with the GUI before figuring out that it was messing with my LTSP network settings.*
At first I thought it was no DNS and those are set default to look at the host machine.
So I set DNS to 8.8.8.8 - nothing.
Then I looked over:
*cat etc/network/interfaces*
and didn't find a gateway! - so I added it:

```
auto eth0
iface eth0 inet static
  address 10.0.1.155
  gateway 10.0.1.1
  netmask 255.255.255.0
  network 10.0.1.0
  broadcast 10.0.1.255
```

[B]#3
Scrambled login screen and terminal screen.[/B]
This is on a brand new WYSE C10LE tested with several monitors.
HOW DO I TROUBLESHOOT THIS??
Remember the xorg.conf is all made on the fly and stored in the LTSP directories. So editing the servers xorg is doing nothing.
There is some documentation at the end of the LSTPManual.pdf that talks about xorg and chroot and dual monitors - but I just don't know where to start...

*(side note - I have tested this image FINE with an old WYSE x150SE thin client and a VirtualBox net boot. So I know it works!)*

[IMG]http://planetkris.com/misc/LTSP_Ubuntu_scramble.jpg[/IMG]

***I hit CTRL-ALT-F1 and instead of text - I get this...***

[IMG]http://planetkris.com/misc/LTSP_Ubuntu_term_scramble.jpg[/IMG]

- Kris

---

### Post by webkris on 2010-06-19
**TINY UPDATE** - after doing some PXE boot work with Damn Small Linux, I think you can edit the VGA option in the 'default' config for PXE boot. I'm sure there are similar 'append' commands that will help get this working in Ubuntu. Researching now...
Any additional thoughts / suggestions would be appreciated!

pxelinux.cfg example
```
DEFAULT linux24
APPEND ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=792 initrd=minirt24.gz nomce noapic quiet BOOT_IMAGE=knoppix
TIMEOUT 300
```

**SIDELINE** - if you are frustrated like me trying to find help with [LTSP here's what I've suggested]("http://ubuntuforums.org/showthread.php?t=1513563"). If you think that will work, post up!
[http://ubuntuforums.org/showthread.php?t=1513563](http://ubuntuforums.org/showthread.php?t=1513563)

- Kris

---

