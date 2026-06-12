---
title: "Ubuntu 14.04 LTS Server.  Preseed issues."
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by scott-ehas on 2014-04-25
Hello,

I am having a few issues with the 14.04 LTS Preseed configurations.  The Preseed configurations have worked with the previous LTS releases.   The current issue is with the /etc/network/interfaces file.   At the current moment I am using the "d-i preseed/late_command string in-target" command to pull in the "interfaces" file with a preset network configuration.   However, on first boot the /etc/network/interfaces file get's completely overwritten.  I have tried the following:

apt-get -y --purge remove isc-dhcp-client isc-dhcp-common resolvconf

I was able to prevent the /etc/network/interfaces script from being overwritten by applying chattr +i flags.  This is not preferred, and a very hackish way to prevent this file from being overwritten.  Can anyone assist me with a proper resolution.  

Thanks.

---

### Post by GNwMQth on 2014-04-28
Same issue here.  I tracked it a bit father--it looks like /tmp/connection_type is getting created in the udeb/installer environment even though I'm not using NetworkManager.  This causes /usr/lib/finish-install.d/55netcfg-copy-config to overwrite /target/etc/network/interfaces.  My hack is to cp /target/etc/network/interfaces /etc/network/interfaces at the end of my d-i preseed/late_command string.


> **scott-ehas said:**
> Hello,

I am having a few issues with the 14.04 LTS Preseed configurations.  The Preseed configurations have worked with the previous LTS releases.   The current issue is with the /etc/network/interfaces file.   At the current moment I am using the "d-i preseed/late_command string in-target" command to pull in the "interfaces" file with a preset network configuration.   However, on first boot the /etc/network/interfaces file get's completely overwritten.  I have tried the following:

apt-get -y --purge remove isc-dhcp-client isc-dhcp-common resolvconf

I was able to prevent the /etc/network/interfaces script from being overwritten by applying chattr +i flags.  This is not preferred, and a very hackish way to prevent this file from being overwritten.  Can anyone assist me with a proper resolution.  

Thanks.

---

### Post by scott-ehas on 2014-04-28
Hello,

I found the same solution in another thread, and copied the interface file to outside the target directory.  No a perfect solution, but better than creating a post install script or using chattr.

Thanks.

---

### Post by patrickt333 on 2014-05-17
> **scott-ehas said:**
> Hello,

I found the same solution in another thread, and copied the interface file to outside the target directory.  No a perfect solution, but better than creating a post install script or using chattr.

Thanks.

This is not working for me and it's maddening for a lot of reasons, chiefly the pure idiocy of blindly overwriting the interfaces file after a preseed install.  Can someone tell me what's wrong here?
```

d-i preseed/late_command string \
  in-target wget http://10.254.254.9/preseeds/ubuntu-stock.sh -O /tmp/ubuntu-stock.sh ; \
  in-target wget http://10.254.254.9/preseeds/common.sh -O /tmp/common.sh ; \
  in-target chmod a+x /tmp/ubuntu-stock.sh /tmp/common.sh ; \
  in-target /tmp/post-install-stock.sh ; \
  cp /target/etc/network/interfaces /etc/network/interfaces


```
All my scripts are working flawlessly and exiting properly, but when it boots the interfaces file is still configured for DHCP.  I've stopped the install prior to boot and confirmed that my scripts ARE properly modifying the interfaces file before it's blindly overwritten by the OS install.   Here's what is looks like in /var/log/installer/syslog

May 17 16:15:23 preseed: running preseed command preseed/late_command: in-target wget [http://10.1.0.9/installs/ubuntu-stock.sh](http://10.1.0.9/installs/ubuntu-stock.sh) -O /tmp/ubuntu-stock.sh ; in-target wget [http://10.1.0.9/installs/common.sh](http://10.1.0.9/installs/common.sh) -O /tmp/common.sh ; in-target chmod a+x /tmp/ubuntu-stock.sh /tmp/common.sh ; in-target /tmp/ubuntu-stock.sh ; cp /target/etc/network/interfaces /etc/network/interfaces

---

