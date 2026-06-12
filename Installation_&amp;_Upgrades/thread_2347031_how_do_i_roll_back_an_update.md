---
title: "how do i roll back an update?"
date: 2016-12-20
forum: Installation &amp; Upgrades
---

### Post by flashingwings on 2016-12-20
Ubuntu Software icon broken after update, among other things: This seems to be the update that broke it: 
Start-Date: 2016-12-20  16:25:21Commandline: aptdaemon role='role-upgrade-system' sender=':1.83'
Upgrade: ifupdown:amd64 (0.8.10ubuntu1.1, 0.8.10ubuntu1.2), libwbclient0:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1, 2:4.3.11+dfsg-0ubuntu0.16.04.3), isc-dhcp-common:amd64 (4.3.3-5ubuntu12.4, 4.3.3-5ubuntu12.6), initramfs-tools-bin:amd64 (0.122ubuntu8.5, 0.122ubuntu8.7), samba-libs:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1, 2:4.3.11+dfsg-0ubuntu0.16.04.3), libsmbclient:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1, 2:4.3.11+dfsg-0ubuntu0.16.04.3), isc-dhcp-client:amd64 (4.3.3-5ubuntu12.4, 4.3.3-5ubuntu12.6), initramfs-tools-core:amd64 (0.122ubuntu8.5, 0.122ubuntu8.7), initramfs-tools:amd64 (0.122ubuntu8.5, 0.122ubuntu8.7)
End-Date: 2016-12-20  16:26:29

TIA

Learning...Chris

---

### Post by ian-weisser on 2016-12-20
The icon dies not mean 'something broke, undo it.' If it did, we would long ago have programmed the system to do so automatically.
Instead, icon usually means one of many possible problems that require your attention to fix. Many are very easy to fix.

Please open a terminal, and run:
```
sudo apt update
sudo apt upgrade
``` 

If an error occurs, then please cut-and-paste the entire session from the terminal into this thread.

---

