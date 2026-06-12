---
title: "adapt installed clonezilla image (hosts, hostname, network interface)"
date: 2012-07-25
forum: Installation &amp; Upgrades
---

### Post by go4unkwn on 2012-07-25
hello ubuntu experts

I manage about 30 pc's at a little school.
some of this pc's have to be configured using static network interfaces others could be configured using dhcp. additionally i have to say that these pc's are in different subnets.

til now i make for each subnet a clonezilla image that can be restored using an usb stick.
but after the restore i have to adapt each pc in relation to hostname and host entries (and the network settings in case of static network settings).

in order to facilitate the setup process i have in mind to write a bash script that runs when the pc boots for the first time after a clonezilla restore (and only then).

my question are:
a) how and when do i have to include this script into the boot process of a pc?
b) is there a way to create an network interface config file with someting like if [mac address] then; ....; fi

any hint is welcome!

kind regards, go4unkwn

---

