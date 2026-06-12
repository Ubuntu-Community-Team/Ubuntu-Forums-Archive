---
title: "Ubuntu 22.04.4 server autoinstall; no DNS server set automatically in installation en"
date: 2024-07-30
forum: Installation &amp; Upgrades
---

### Post by xnobodyx on 2024-07-30
Hello,

Working on setting up a uefi netboot ubuntu 22.04.4 server autoinstall. the install fails when running *curtin command apt-config* with 'no mirror is usable'. 

The 22.04.4 server install environment gets a working ip with DHCP and can ping WAN IP addresses, however no dns nameserver is set up despite being specified in the autoinstall file. If a dnsserver is manually set in tty2 with *sudo resolvectl dns enp0s31f6 10.10.0.1* before the initial apt-config times out, then the install proceeds with no other issues.

The network section of the autoinstall yaml file is:

```
  network:
    version: 2
    ethernets:
      enp0s31f6:
        match:
          macaddress: XX:XX:XX:XX:XX:01
        dhcp4: false
        addresses:
          - 10.10.0.3/16
        routes:
          - to: default
            via: 10.10.0.1
        nameservers:
          search:
            - domain.com
          addresses:
            - 10.10.0.1
      enp0s31f6:
        match:
          macaddress: XX:XX:XX:XX:XX:02
        dhcp4: false
        addresses:
          - 10.10.0.4/16
        routes:
          - to: default
            via: 10.10.0.1
        nameservers:
          search:
            - domain.com
          addresses:
            - 10.10.0.1
```

after booting the installer environment and checking the /etc/netplan directory there are two netplan yaml files: 00-installer-config.yaml and 50-cloud-init.yaml.dist-subiquity

00-installer-config.yaml contains the correct config for the ethernet adapter based off the mac address from the network section of the autoinstall file, including the dns server:

```
  network:
    version: 2
    ethernets:
      enp0s31f6:
        match:
          macaddress: XX:XX:XX:XX:XX:01
        dhcp4: false
        addresses:
          - 10.10.0.3/16
        routes:
          - to: default
            via: 10.10.0.1
        nameservers:
          search:
            - domain.com
          addresses:
            - 10.10.0.1
```

50-cloud-init.yaml.dist-subiquity has an entry for the ethernet adapter with dhcp and the autoinstall specified dns server, but then has additional zz-all-en and zz-all-eth entries. i'm wondering if these general entries are overriding dns?

```
network:
  ethernets:
        enp0s31f6:
          critical: true
          dhcp-identifier: mac
          dhcp4: true
          nameservers:
            addresses:
              - 10.10.0.1

        zz-all-en:
          dhcp4: true
      match:
        name: en*

        zz-all-eth:
          dhcp4: true
      match:
        name: en*
  version: 2
```

If relevant here is the tftp grub entry as well:

```
menuentry "Ubuntu 22.04.4" {
        set gfxpayload=keep
        linux   vmlinuz root=/dev/ram0 ramdisk_size=1500000 url=http://10.10.0.2/ubuntu-22.04.4-live-server-amd64.iso ip=dhcp autoinstall cloud-config-url=http://10.10.0.2/autoinstall.yaml ---
        initrd  initrd
}
```

any help is greatly appreciated

---

### Post by euol on 2024-08-04
The 50-cloud-init.yaml.dist-subiquity file with DHCP configurations might be overriding your DNS settings from 00-installer-config.yaml. Make sure you have only one netplan configuration file, in this case 00-installer-config.yaml

---

### Post by xnobodyx on 2024-08-06
> **euol said:**
> The 50-cloud-init.yaml.dist-subiquity file with DHCP configurations might be overriding your DNS settings from 00-installer-config.yaml. Make sure you have only one netplan configuration file, in this case 00-installer-config.yaml

A bit stumped about how to handle this for the installation environment before autoinstall starts.

Since *sudo resolvectl dns enp0s31f6 10.10.0.1* gets the install working I tried adding that the early-commands section of autoinstall.yaml but it doesn't seem to have an effect.

I also tried testing in tty2:

```
rm -f /etc/netplan/50-cloud-init.yaml.dist-subiquity
netplan apply
```

but netplan returns "Cannot call Open vSwitch: ovsdb-server.service is not running.

---

