---
title: "trying to autoinstall ubuntu 20 and failing with packages"
date: 2020-06-14
forum: Installation &amp; Upgrades
---

### Post by exm1110b on 2020-06-14
hi.. i've been trying to use auto install on ubuntu 20, along with packer and vmware vsphere, 
however every time i try to use "packages" it's crashes, or hangs i can't get any logs from it 

when it hangs it hands on subiquity mirror failing .

is it possible to configure the  renderer to be NetworkManager? 

```

#cloud-config
autoinstall:
  version: 1
  locale: en_US
  keyboard:
    layout: en
    variant: us
  network:
    network:
      version: 2
      ethernets:
        ens33:
          dhcp4: true
  storage:
    layout:
      name: lvm
  identity:
    hostname: aes
    username: aeroscout
    password: crypted
  ssh:
    install-server: yes
    allow-pw: true
  user-data:
    package_update: true
    disable_root: false
  packages:
    - net-tools
  late-commands:
    - echo 'aeroscout ALL=(ALL) NOPASSWD:ALL' > /target/etc/sudoers.d/aeroscout
  error-commands:
    - sudo tar c /var/log/installer | nc 192.168.100.35 8000

```

---

