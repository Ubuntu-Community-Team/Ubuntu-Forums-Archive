---
title: "HELP! Can't uninstall VMWare"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by icephoenix on 2008-04-27
Trying to unistall VMWare and getting funky error :(

```

(Reading database ... 136553 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--purge):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

What can I do to fix that?

---

