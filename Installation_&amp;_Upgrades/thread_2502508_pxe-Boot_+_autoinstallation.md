---
title: "pxe-Boot + autoinstallation"
date: 2024-11-18
forum: Installation &amp; Upgrades
---

### Post by leof22 on 2024-11-18
Hello everyone,


I want to boot Ubuntu via PXE on the network and perform an automatic installation. The PXE boot also works, but unfortunately the yaml configuration file is not passed directly to the installer. If I specify the path [http://172.20.0.2/user-data](http://172.20.0.2/user-data) during the installation process, the file is verified and everything works.


I installed everything according to these instructions: ipxe, dnsmasq (DHCP and TFTP server), nfs-kernel-server (NFS server) and ngingx (web server)


My /pxeboot/config/boot.ipxe looks like this:
```
[COLOR=#000000][FONT=&amp]set server_ip  172.20.0.2[/FONT][/COLOR]
set root_path  /pxeboot

menu Select an OS to boot
item ubuntu-24.04-desktop-amd64         Install Ubuntu Desktop 24.04 LTS
item ubuntu-24.04-server-amd64         Install Ubuntu Server 24.04 LTS

#choose --default ubuntu-24.04-server-amd64 --timeout 0 option && goto ${option}
choose --default exit --timeout 1000 option && goto ${option}

:ubuntu-24.04-desktop-amd64
set os_root os-images/ubuntu-24.04-desktop-amd64
kernel tftp://${server_ip}/${os_root}/casper/vmlinuz
initrd tftp://${server_ip}/${os_root}/casper/initrd
imgargs vmlinuz initrd=initrd boot=casper maybe-ubiquity netboot=nfs ip=dhcp nfsroot=${server_ip}:${root_path}/${os_root} cloud-config-url=http://${server_ip}/autoinstall.yaml autoinstall debug
#imgargs vmlinuz initrd=initrd boot=casper maybe-ubiquity netboot=nfs ip=dhcp nfsroot=${server_ip}:${root_path}/${os_root} autoinstall "ds=nocloud-net;s=http://${server_ip}" debug [COLOR=#000000][FONT=&amp]boot[/FONT][/COLOR]
```

In /var/www/ is the file meta-data:
```

instance-id: iid-local01
local-hostname: ubuntu
```


and both the user-data and the autoinstall.yaml have the following content (simple config for testing):
```

#cloud-config
autoinstall:<
  version: 1
  identity:
    hostname: ubuntu
    username: Test
    password: '$GEHEIMER HASH'
```

I have [uploaded all the log files]("https://nextcloud.fuehringers.de/s/6YaNyBrq2Xce5H6") that I copied from the client to be installed.
Do you have any idea why this is happening? Where can I find a log that shows why the auto-installation file is not loading directly?


Thanks and best wishes!

---

