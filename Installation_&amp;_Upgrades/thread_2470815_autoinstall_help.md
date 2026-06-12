---
title: "autoinstall help"
date: 2022-01-12
forum: Installation &amp; Upgrades
---

### Post by andrew_meyer2 on 2022-01-12
Hello, 
I am trying to get autoinstall working with adding users but running into some issues.  This is all for my home lab.  But I can't get it to create the users.  If I remove the user-data and leave the identity it works fine.  I am very new to cloud-init and subiquity.  



```

#cloud-config
autoinstall:
  debug: true
  disable_root: false
  password: $6$HASH
  apt:
    geoip: true
    preserve_sources_list: false
    primary:
    - arches: [amd64, i386]
      uri: http://us.archive.ubuntu.com/ubuntu
    - arches: [default]
      uri: http://ports.ubuntu.com/ubuntu-ports
  package_update: true
  package_upgrade: true
  packages:
    - linux-generic-hwe-20.04
  power_state:
  mode: reboot
  identity:
       hostname: ubuntu01
       password: $6$HASH
       realname: Real Name
       username: username1
#  kernel:
#    kernel: {package: linux-generic-hwe-20.04}
  keyboard: {layout: us, toggle: null, variant: ''}
  locale: en_US.UTF-8
  network:
    ethernets:
      ens160: {dhcp4: true}
    version: 2
  ssh:
    allow-pw: true
    authorized-keys: []
    install-server: true
  user-data: # cloud-config data goes under this heading
    timezone: America/Chicago
    locale: en_US.UTF-8
#    hostname: valleylodge
    groups:
      - name: sysadmin
        gid: 1100
    users:
      - default
      - name: root
        lock-passwd: false
        passwd: $6$hash
        primary_group: root
        ssh_pwauth: yes
      - name: username
        gecos: "Real Name"
        primary_group: sysadmin
        groups: sudo
        lock-passwd: false
        passwd: "hash key" # shadow password hash
        shell: /bin/bash
        ssh_pwauth: true
        ssh_authorized_keys:
           - ssh-rsa fdsfasfdsfasdfsdfsa
        sudo: "ALL=(ALL) NOPASSWD:ALL"
        uid: 9000
  storage:
    config:
    - {ptable: gpt, path: /dev/sda, wipe: superblock-recursive, preserve: false, name: '',
      grub_device: true, type: disk, id: disk-sda}
    - {device: disk-sda, size: 1048576, flag: bios_grub, number: 1, preserve: false,
      grub_device: false, type: partition, id: partition-0}
    - {device: disk-sda, size: 2147483648, wipe: superblock, flag: '', number: 2,
      preserve: false, grub_device: false, type: partition, id: partition-1}
    - {fstype: ext4, volume: partition-1, preserve: false, type: format, id: format-0}
    - {device: disk-sda, size: 51536461824, wipe: superblock, flag: '', number: 3,
      preserve: false, grub_device: false, type: partition, id: partition-2}
    - name: vg_root
      devices: [partition-2]
      preserve: false
      type: lvm_volgroup
      id: lvm_volgroup-0
    - {name: lv_root, volgroup: lvm_volgroup-0, size: 3221225472B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-0}
    - {fstype: ext4, volume: lvm_partition-0, preserve: false, type: format, id: format-1}
    - {path: /, device: format-1, type: mount, id: mount-1}
    - {name: lv_usr, volgroup: lvm_volgroup-0, size: 8589934592B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-1}
    - {fstype: ext4, volume: lvm_partition-1, preserve: false, type: format, id: format-2}
    - {path: /usr, device: format-2, type: mount, id: mount-2}
    - {name: lv_var, volgroup: lvm_volgroup-0, size: 8589934592B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-2}
    - {fstype: ext4, volume: lvm_partition-2, preserve: false, type: format, id: format-3}
    - {path: /var, device: format-3, type: mount, id: mount-3}
    - {name: lv_var_log, volgroup: lvm_volgroup-0, size: 4294967296B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-3}
    - {fstype: ext4, volume: lvm_partition-3, preserve: false, type: format, id: format-4}
    - {path: /var/log, device: format-4, type: mount, id: mount-4}
    - {name: lv_var_log_audit, volgroup: lvm_volgroup-0, size: 2147483648B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-4}
    - {fstype: ext4, volume: lvm_partition-4, preserve: false, type: format, id: format-5}
    - {path: /var/log/audit, device: format-5, type: mount, id: mount-5}
    - {name: lv_home, volgroup: lvm_volgroup-0, size: 10737418240B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-5}
    - {fstype: ext4, volume: lvm_partition-5, preserve: false, type: format, id: format-6}
    - {path: /home, device: format-6, type: mount, id: mount-6}
    - {name: lv_tmp, volgroup: lvm_volgroup-0, size: 5368709120B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-6}
    - {fstype: ext4, volume: lvm_partition-6, preserve: false, type: format, id: format-7}
    - {path: /tmp, device: format-7, type: mount, id: mount-7}
    - {name: lv_opt, volgroup: lvm_volgroup-0, size: 5368709120B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-7}
    - {fstype: ext4, volume: lvm_partition-7, preserve: false, type: format, id: format-8}
    - {path: /opt, device: format-8, type: mount, id: mount-8}
    - {name: lv_swap, volgroup: lvm_volgroup-0, size: 2147483648B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-8}
    - {fstype: swap, volume: lvm_partition-8, preserve: false, type: format, id: format-9}
    - {path: '', device: format-9, type: mount, id: mount-9}
    - {path: /boot, device: format-0, type: mount, id: mount-0}
    swap: {swap: 0}
  updates: security
  runcmd:
   #- sudo perl -i -pe 's/disable_root: 1/disable_root: 0/' /etc/cloud/cloud.cfg
   - sudo perl -i -pe 's/#PermitRootLogin .*/PermitRootLogin without-password/' /etc/ssh/sshd_config
   #- sudo perl -i -pe 's/.*(ssh-rsa .*)/\1/' /root/.ssh/authorized_keys
   - sudo systemctl restart ssh # optional command
  version: 1

```

---

### Post by andrew_meyer2 on 2022-01-13
Nevermind.  Figured it out.

---

