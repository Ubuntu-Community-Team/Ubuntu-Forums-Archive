---
title: "libvirt-daemon-system failed to setup while updating 20.04. What this logs means?"
date: 2020-07-23
forum: Installation &amp; Upgrades
---

### Post by pranav.bhattarai on 2020-07-23
Should I be worried about anything? Is there something I can do?
All I did was "sudo apt update && sudo apt upgrade". 
And in middle of the update, I got this message saying:
```

Setting up libvirt-daemon-system (6.0.0-0ubuntu8.2) ... 
Job failed. See "journalctl -xe" for details. 

```
```

pranav@exam ~> journalctl -xe | grep "libvirt" 
Jul 23 20:03:37 exam audit[41000]: AVC apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirtd" pid=41000 comm="apparmor_parser" 
Jul 23 20:03:37 exam kernel: audit: type=1400 audit(1595513917.944:57): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirtd" pid=41000 comm="apparmor_parser" 
Jul 23 20:03:37 exam audit[41000]: AVC apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirtd//qemu_bridge_helper" pid=41000 comm="apparmor_parser" 
Jul 23 20:03:37 exam kernel: audit: type=1400 audit(1595513917.968:58): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirtd//qemu_bridge_helper" pid=41000 comm="apparmor_parser" 
Jul 23 20:03:39 exam systemd[1]: libvirtd-ro.socket: Succeeded. 
-- The unit libvirtd-ro.socket has successfully entered the 'dead' state. 
-- Subject: A stop job for unit libvirtd-ro.socket has finished 
-- A stop job for unit libvirtd-ro.socket has finished. 
-- Subject: A stop job for unit libvirtd-ro.socket has begun execution 
-- A stop job for unit libvirtd-ro.socket has begun execution. 
Jul 23 20:03:39 exam systemd[1]: libvirtd-ro.socket: Socket service libvirtd.service already active, refusing. 
-- Subject: A start job for unit libvirtd-ro.socket has failed 
-- A start job for unit libvirtd-ro.socket has finished with a failure. 
-- Subject: A stop job for unit libvirtd.service has begun execution 
-- A stop job for unit libvirtd.service has begun execution. 
Jul 23 20:03:39 exam systemd[1]: libvirtd.service: Succeeded. 
-- The unit libvirtd.service has successfully entered the 'dead' state. 
-- Subject: A stop job for unit libvirtd.service has finished 
-- A stop job for unit libvirtd.service has finished. 
Jul 23 20:03:39 exam systemd[1]: libvirtd-admin.socket: Succeeded. 
-- The unit libvirtd-admin.socket has successfully entered the 'dead' state. 
-- Subject: A stop job for unit libvirtd-admin.socket has finished 
-- A stop job for unit libvirtd-admin.socket has finished. 
-- Subject: A stop job for unit libvirtd-admin.socket has begun execution 
-- A stop job for unit libvirtd-admin.socket has begun execution. 
Jul 23 20:03:39 exam systemd[1]: libvirtd.socket: Succeeded. 
-- The unit libvirtd.socket has successfully entered the 'dead' state. 
-- Subject: A stop job for unit libvirtd.socket has finished 
-- A stop job for unit libvirtd.socket has finished. 
-- Subject: A stop job for unit libvirtd.socket has begun execution 
-- A stop job for unit libvirtd.socket has begun execution. 
-- Subject: A start job for unit libvirtd.socket has finished successfully 
-- A start job for unit libvirtd.socket has finished successfully. 
-- Subject: A start job for unit libvirtd-admin.socket has finished successfully 
-- A start job for unit libvirtd-admin.socket has finished successfully. 
-- Subject: A start job for unit libvirtd-ro.socket has finished successfully 
-- A start job for unit libvirtd-ro.socket has finished successfully. 
Jul 23 20:03:39 exam systemd[1]: libvirtd.service: Found left-over process 2640 (dnsmasq) in control group while starting unit. Ignoring. 
Jul 23 20:03:39 exam systemd[1]: libvirtd.service: Found left-over process 2641 (dnsmasq) in control group while starting unit. Ignoring. 
-- Subject: A start job for unit libvirtd.service has begun execution 
-- A start job for unit libvirtd.service has begun execution. 
-- Subject: A start job for unit libvirtd.service has finished successfully 
-- A start job for unit libvirtd.service has finished successfully. 
Jul 23 20:03:39 exam dnsmasq[2640]: read /var/lib/libvirt/dnsmasq/default.addnhosts - 0 addresses 
Jul 23 20:03:39 exam dnsmasq-dhcp[2640]: read /var/lib/libvirt/dnsmasq/default.hostsfile 
pranav@exam ~>  



```

---

