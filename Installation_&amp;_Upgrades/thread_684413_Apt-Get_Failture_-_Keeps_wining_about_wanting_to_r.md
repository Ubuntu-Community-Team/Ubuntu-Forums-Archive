---
title: "Apt-Get Failture - Keeps wining about wanting to reinstall limewire, but can't."
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Maube-Not on 2008-02-01
After trying to install Limewire, (first Frostwire, but it ignored me) Synaptitude have been flipping out. I get an updates icon on the taskmenu saying:
Code:

An error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong.
The error message was: 'Unknown Error. '<type
'exceptions.SystemError'>'(E:The package limewire-basic needs to be reinstalled, but i can't find an archive for it.)'

I tried downloading the Limewire deb from the limewire homepage, but it doesn't install with this message:

Point-And-Click installation with the .deb;

Could not open LimeWireLinux.deb
The package might be corrupted or you are not allowed to open the file.
Check the permissions of the file.



I did check, and granted both my group and user read+write permission, and checked the Execute box. Same error message.


Terminal installation with ./LimeWireLinux.deb is not possible. Nothing happens. Output:

$ ./LimeWireLinux.deb
./LimeWireLinux.deb: line 1: syntax error near unexpected token `newline'
./LimeWireLinux.deb: line 1: `!<arch>'


Updates is possible, but when i open Synaptic i get:
E: The package limewire-basic needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Testing installation gives:
~$ sudo apt-get install frostwire
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package limewire-basic needs to be reinstalled, but I can't find an archive for it.

---

### Post by zvacet on 2008-02-01
```
sudo apt-get --purge remove** packagename**
```

or 

```
sudo dpkg --remove --force-remove-reinstreq **packagename**
```

In your case packagename =exact name of limewire

This will remove limewire,but you can try to reinstall it with

```
sudo apt-get install --reinstall **packagename**
```

---

