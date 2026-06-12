---
title: "Updates on Ubuntu 12.04.1"
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by dalewis62 on 2013-06-01
I have been getting the following errors whenever I install updates.  To try and resolve I have tried to purge the old versions, force reinstall and to no avail the errors continue.  Does anyone have any ideas on how to solve this problem?                                                                                                                                                                                         Preparing to replace cups 1.5.3-0ubuntu6 (using .../cups_1.5.3-0ubuntu8_amd64.deb) ...
invoke-rc.d: initscript cups, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript cups, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/cups_1.5.3-0ubuntu8_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace samba 2:3.6.3-2ubuntu2.4 (using .../samba_2%3a3.6.3-2ubuntu2.6_amd64.deb) ...
invoke-rc.d: initscript nmbd, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript nmbd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/samba_2%3a3.6.3-2ubuntu2.6_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
invoke-rc.d: initscript smbd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace telepathy-gabble 0.16.0-0ubuntu2 (using .../telepathy-gabble_0.16.0-0ubuntu3_amd64.deb) ...
Unpacking replacement telepathy-gabble ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/cups_1.5.3-0ubuntu8_amd64.deb
 /var/cache/apt/archives/samba_2%3a3.6.3-2ubuntu2.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ibjsb4 on 2013-06-01
First try cleaning /var/cache/apt/archives.

```
sudo apt-get clean
sudo apt-get update
```

Do any good?

#7
[URL="https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands"]https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)
[/URL]

---

### Post by dalewis62 on 2013-06-01
Thanks for the suggestion.  I have tried it and some ideas from the thread you attached and still no joy.  I still get the error rc.d cannot STOP error when I try updating these packages.

---

### Post by fantab on 2013-06-02
Try:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

If you still get errors post the output of *sudo apt-get update* here

---

