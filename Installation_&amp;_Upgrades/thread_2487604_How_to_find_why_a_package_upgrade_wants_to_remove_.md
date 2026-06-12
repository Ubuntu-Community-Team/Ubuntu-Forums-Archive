---
title: "How to find why a package upgrade wants to remove a lot other packages"
date: 2023-06-09
forum: Installation &amp; Upgrades
---

### Post by jagsdesai on 2023-06-09
OS: Ubuntu MATE 23.04 Lunar

After upgrading Ubuntu MATE 22.10 Kinetic to 23.04 Lunar, package `dhcpcd-base` upgrade wants to remove network-manager, ubuntu-minimal, isc-dhcp-client, and 17 other packages (screenshot attached).

I like to find out why? Result for `apt depends` and `apt-rdepneds` does not list any of the packages `apt upgrade` wants to remove.

Is there any `apt` command or something to find why `apt upgrade` wants to remove whole bunch of packages?

```
$ apt depends dhcpcd-base

dhcpcd-base
  Depends: adduser
  Depends: libc6 (>= 2.34)
  Depends: libudev1 (>= 183)
  Conflicts: <dhcp-client>
    isc-dhcp-client
  Breaks: dhcpcd5 (<< 9.4.1-2)
  Recommends: wpasupplicant
  Replaces: <dhcp-client>
    dhcpcd-base
    isc-dhcp-client
  Replaces: dhcpcd5 (<< 9.4.1-2)
$

$ apt rdepends dhcpcd-base

dhcpcd-base
Reverse Depends:
  Depends: dhcpcd
$
```

Any help is greatly appreciated. Many thanks in advance.

---

### Post by #&amp;thj^% on 2023-06-09
Picture don't work well if you want others to help you, terminal output in code tags is preferred here  in UF
Lets do that now OK? OK!
```
cd
sudo apt dist-upgrade -s >upgrade.txt
```
That command just acts as a Dry run, and nothing will change.
The part we want is in your home folder named "upgrade.txt" and it will be long so just attach (Attachment) it in your next post
I made a sample of mine to help.

---

### Post by jagsdesai on 2023-06-09
@1fallen Thanks for the reply.

Attaching the `upgrade.txt` file and posting it in here too, as it did not come out that long.

```
sudo apt dist-upgrade -s >upgrade.txt

Reading package lists...Building dependency tree...
Reading state information...
Calculating upgrade...
The following packages have been kept back:
  dhcpcd-base
The following packages will be upgraded:
  plexmediaserver
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Inst plexmediaserver [1.32.2.7100-248a2daf0] (1.32.3.7162-b0a36929b Artifactory:public [amd64])
Conf plexmediaserver (1.32.3.7162-b0a36929b Artifactory:public [amd64])
```

I just like to know why `apt upgrade` wants to remove 20 packages, **IF I upgrade `dhcpcd-base` from version 9.4.1-4 to 9.4.1-19**.

Here's the complete list of packages that `apt upgrade` will remove **IF **I upgrade `dhcpcd-base`:

```
gnome-network-displays
guestfish
guestfs-tools
guestmount
isc-dhcp-client
libguestfs-hfsplus
libguestfs-perl
libguestfs-reiserfs
libguestfs-tools
libguestfs-xfs
libguestfs-0
network-manager
network-manager-gnome
network-manager-openvpn
network-manager-openvpn-gnome
network-manager-pptp
network-manager-pptp-gnome
network-manager-strongswan
ubuntu-minimal
virt-p2v
```

---

### Post by #&amp;thj^% on 2023-06-11
Sorry for my my late reply.
And your sure those weren't replaced already with the upgrade?

I really don't see anything wrong with what you have shown us so far.
As for "IF I upgrade `dhcpcd-base` from version 9.4.1-4 to 9.4.1-19." that is in a *phased* state and is real good idea to wait until they send it out to your
regular system-ugrades naturally.
Just some info from my system:
```
apt show dhcpcd-base
Package: dhcpcd-base
Version: 9.4.1-24
Priority: optional
Section: universe/net
Source: dhcpcd5
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Martin-Éric Racine <martin-eric.racine@iki.fi>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 525 kB
Provides: dhcp-client
Depends: adduser, libc6 (>= 2.34), libudev1 (>= 183)
Recommends: wpasupplicant
Suggests: resolvconf | openresolv | systemd-resolved
Breaks: dhcpcd5 (<< 9.4.1-2)
Replaces: dhcpcd5 (<< 9.4.1-2)
Homepage: https://roy.marples.name/projects/dhcpcd
Download-Size: 216 kB
APT-Sources: http://archive.ubuntu.com/ubuntu devel/universe amd64 Packages
Description: DHCPv4 and DHCPv6 dual-stack client (binaries and exit hooks)
 dhcpcd provides seamless IPv4 and IPv6 auto-configuration:
  * DHCPv4 client
  * DHCPv6 client with Prefix Delegation (PD) support
  * IPv4 LL support (ZeroConf)
  * IPv6 SLAAC support
  * ARP address conflict resolution
  * ARP ping profiles
  * Wireless SSID profiles
 .
 This package provides the binaries, exit hooks and manual pages.
 .
 It offers a dual-stack substitute for ISC DHCP Client (dhclient) on systems
 where interfaces are configured by ifupdown via </etc/network/interfaces>
 using the DHCP method.
 .
 The init.d script and systemd service required for systems without ifupdown
 are packaged separately as dhcpcd.
 .
 Since Debian 12 (Bookworm), dhcpcd uses Predictable Network Interface Names
 on Linux ports. See NEWS.Debian for more details.


```
I'm not using it ATM so:
```
apt policy dhcpcd-base
dhcpcd-base:
  Installed: (none)
  Candidate: 9.4.1-24
  Version table:
     9.4.1-24 500
        500 http://archive.ubuntu.com/ubuntu devel/universe amd64 Packages

```
I guess I should also add I'm running "devel-sources" on mine and yours looks great for Lunar
```
 dhcpcd-base | 9.4.1-4  | kinetic/universe | amd64, arm64, armhf, ppc64el, riscv64, s390x
 dhcpcd-base | 9.4.1-19 | lunar/universe   | amd64, arm64, armhf, ppc64el, riscv64, s390x
 dhcpcd-base | 9.4.1-24 | mantic/universe  | amd64, arm64, armhf, ppc64el, riscv64, s390x

```

---

