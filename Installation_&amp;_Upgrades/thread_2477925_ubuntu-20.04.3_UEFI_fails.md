---
title: "ubuntu-20.04.3 UEFI fails"
date: 2022-08-11
forum: Installation &amp; Upgrades
---

### Post by jaiminmpatel on 2022-08-11
i'm trying to build Ubuntu on HP DL380 Gen9 using UEFI boot, and i'm having problem figuring out why it's failing on 001-configure-apt/cmd-in-target
i have tried various things but i'm not able to figure it out.

here is my userdata file

```
#cloud-config Generic UEFI profile

autoinstall:
  version: 1
  ssh:
    install-server: yes
    allow-pw: no


  locale: en_US.UTF-8


  keyboard:
    layout: us
    variant: us

timezone: US/Eastern

grub:
    reorder_uefi:false
  storage:
    layout:
      name: lvm
    config:
    - {ptable: gpt,
      path: /dev/sda, preserve: false, name: '', grub_device: false, type: disk, id: disk-sda}
    - {device: disk-sda, size: 536870912, flag: boot, number: 1, preserve: false, grub_device: true,
      type: partition, id: partition-sda1}
    - {device: disk-sda, size: 1073741824, wipe: superblock, flag: linux, number: 2,
      preserve: false, grub_device: false, type: partition, id: partition-sda2}
    - {fstype: ext4, volume: partition-sda2, preserve: false, type: format, id: format-0}
    - {device: disk-sda, size: 145165910016, wipe: superblock, flag: linux, number: 3,
      preserve: false, grub_device: false, type: partition, id: partition-sda3}
    - name: vg0
      devices: [partition-sda3]
      preserve: false
      type: lvm_volgroup
      id: lvm_volgroup-0
    - {name: root, volgroup: lvm_volgroup-0, size: 34359738368B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-0}
    - {fstype: ext4, volume: lvm_partition-0, preserve: false, type: format, id: format-2}
    - {path: /, device: format-2, type: mount, id: mount-2}
    - {name: home, volgroup: lvm_volgroup-0, size: 10737418240B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-1}
    - {fstype: ext4, volume: lvm_partition-1, preserve: false, type: format, id: format-3}
    - {path: /home, device: format-3, type: mount, id: mount-3}
    - {name: var, volgroup: lvm_volgroup-0, size: 10737418240B, wipe: superblock,
      preserve: false, type: lvm_partition, id: lvm_partition-2}
    - {fstype: ext4, volume: lvm_partition-2, preserve: false, type: format, id: format-4}
    - {path: /var, device: format-4, type: mount, id: mount-4}
    - {path: /boot, device: format-0, type: mount, id: mount-0}
    - {fstype: vfat, volume: partition-sda1, preserve: false, type: format, id: format-partition-sda1}
    - {path: /boot/efi, device: format-partition-sda1, type: mount, id: mount-1}


  network:
    version: 2
    renderer: networkd
    ethernets:
      eno1:
        dhcp4: no
        addresses: [x.x.x.x/24]
        gateway4: x.x.x.x
        nameservers:
          addresses: ['x.x.x.x', 'x.x.x.x']

  proxy: [http://x.x.x.x:3142](http://x.x.x.x:3142)

pacakges:
     - build-essential
     - ethtool
     - libpcap-dev
     - valgrind
     - vim
     - ladvd
     - git
     - ifupdown
     - mlocate
     - emacs-nox
     - ansible
     - nfs-common
     - chrony

  package_update: true
  package_upgrade: true

  runcmd:
    - [ wget, "http://172.16.22.22/ubuntu-20.04.3-generic/ubuntu-20.04-generic-install.sh", -O, /root/ubuntu-20.04-generic-install.sh ]
    - [ sh, -c, "chmod 755 /root/ubuntu-20.04-generic-install.sh && /root/ubuntu-20.04-generic-install.sh" ]

logs
2022-08-11 09:09:47,358 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks/001-configure-apt/cmd-in-target: FAIL: curtin command in-ta
2022-08-11 09:09:47,359 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks/001-configure-apt: FAIL: running '/snap/subiquity/2651/bin/ity-configure-apt /snap/subiquity/2651/usr/bin/python3 true'
2022-08-11 09:09:47,359 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks: FAIL: configuring installed system
2022-08-11 09:09:47,769 DEBUG subiquitycore.utils:83 arun_command ['systemd-cat', '--level-prefix=false', '--identifier=subiquity_log.2466', '/snap/subiquity/2651/usr/bin/pyt '-m', 'curtin', '--showtrace', '-c', '/var/log/installer/subiquity-curtin-install.conf', 'install'] exited with code 3
2022-08-11 09:09:47,770 ERROR root:39 finish: subiquity/Install/install/curtin_install: FAIL: Command '['systemd-cat', '--level-prefix=false', '--identifier=subiquity_log.246snap/subiquity/2651/usr/bin/python3', '-m', 'curtin', '--showtrace', '-c', '/var/log/installer/subiquity-curtin-install.conf', 'install']' returned non-zero exit status 3.
2022-08-11 09:09:47,773 DEBUG subiquitycore.common.errorreport:384 generating crash report
2022-08-11 09:09:47,778 INFO subiquitycore.common.errorreport:407 saving crash report 'install failed crashed with CalledProcessError' to /var/crash/1660208987.773840666.instil.crash
2022-08-11 09:09:47,778 ERROR root:39 finish: subiquity/Install/install: FAIL: Command '['systemd-cat', '--level-prefix=false', '--identifier=subiquity_log.2466', '/snap/subi2651/usr/bin/python3', '-m', 'curtin', '--showtrace', '-c', '/var/log/installer/subiquity-curtin-install.conf', 'install']' returned non-zero exit status 3.
```

---

### Post by jaiminmpatel on 2022-08-11
changed boot grub order under stroage as well but still no benefit with that.



  ```
storage:
    grub:
      reorder_uefi:false

new error is 

2022-08-11 10:48:22,237 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks/builtin/cmd-curthooks/install-grub: FAIL: installing grub to target devices
2022-08-11 10:48:22,238 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks/builtin/cmd-curthooks/configuring-bootloader: FAIL: configuring target system bootloader
2022-08-11 10:48:22,694 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks/builtin: FAIL: running 'curtin curthooks'
2022-08-11 10:48:22,694 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install/stage-curthooks: FAIL: configuring installed system
2022-08-11 10:48:23,007 ERROR root:39 finish: subiquity/Install/install/curtin_install/cmd-install: FAIL: curtin command install
2022-08-11 10:48:23,008 DEBUG subiquitycore.utils:83 arun_command ['systemd-cat', '--level-prefix=false', '--identifier=subiquity_log.2434', '/snap/subiquity/2651/usr/bin/python3', '-m', 'curtin', '--showtrace', '-c', '/var/log/installer/subiquity-curtin-install.conf', 'install'] exited with code 3
2022-08-11 10:48:23,009 ERROR root:39 finish: subiquity/Install/install/curtin_install: FAIL: Command '['systemd-cat', '--level-prefix=false', '--identifier=subiquity_log.2434', '/snap/subiquity/2651/usr/bin/python3', '-m', 'curtin', '--showtrace', '-c', '/var/log/installer/subiquity-curtin-install.conf', 'install']' returned non-zero exit status 3.
```

---

### Post by oldfred on 2022-08-11
Please use Code Tags for longer terminal or text output.
Easy to add with Forum's advanced Editor & # icon.

Do not know servers nor scripted installs.
What script are you using. 
I can move thread to server sub-forum if desired where those users may be able to help.

But I do not see you setting drive to gpt.
And the ESP - efi system partition must be FAT32.
The UEFI LVM installs I have seen have an ESP, a /boot and a partition for the LVM volume.
Do not confuse the ESP as FAT32 with esp,boot flags with /boot as ext4.

---

### Post by bingodingo on 2022-08-11
Does your system have a disk that curtin can install to?

---

