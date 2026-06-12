---
title: "ATI FireGL 3600 drivers wont install"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by DyBurke on 2012-05-24
So, I just installed the 12.04 LTS but I did it by installing over my old install, but keeping my (seperate) /home and /tmp partitions.  All seems to be well except I can't seem to upgrade my graphics card driver.  There are tons of errors printed in /var/log/jockey.log so I will try to make it so you don't have to read the whole thing.

First things:
I'm using gnome-shell
I have an ATI FireGL v3600


I think the problem lies somewhere in fglrx_updates as it seems to be nonexistent, but in reality I have no idea:
```
2012-05-24 12:37:32,123 DEBUG: fglrx_updates is not the alternative in use
2012-05-24 12:37:32,149 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf

```

Then it segways into errors that get really repetative, but this seemed important:
```
2012-05-24 12:37:32,403 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-24 12:37:33,361 DEBUG: Shutting down
2012-05-24 12:38:32,812 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725864c>
2012-05-24 12:38:33,674 DEBUG: reading modalias file /lib/modules/3.0.0-19-generic-pae/modules.alias
2012-05-24 12:38:33,734 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-05-24 12:38:33,734 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-05-24 12:38:33,752 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-05-24 12:38:33,760 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-05-24 12:38:33,762 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

```

Any help is much appreciated and if you need more info, just let me know.  Thanks guys and happy days! :guitar:

---

