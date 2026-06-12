---
title: "Unable to boot into ubuntu after installing wubi on a windows 7 machine"
date: 2013-11-01
forum: Installation &amp; Upgrades
---

### Post by swkimani on 2013-11-01
I have just installed wubi 12.04.2 on a partition separate from where windows 7 is installed. When I try to reboot after installation, I get an error that the windows disc is missing. After I exit and get to the page where I have to select either windows or ubuntu, I get the following error message if I select ubuntu:

"File: \ubuntu\winboot\wubildr.mbr
Status: OXC0000098
The selected application could not be loaded because the application is missing or corrupt."

Could this be because wubi is on a different partition? If that is the case, how can I resolve the problem without interfering too much with windows?

Your advice will be so much appreciated.

Thanks.

---

### Post by bcbc on 2013-11-02
Your computer is probably booting using UEFI in which case Wubi won't work. You can check this in a number of ways, from a CMD.EXE prompt (make sure you Run as Administrator) you can enter:
```
bcdedit
```

And look for bootmgfw.efi or winload.efi in the output. If you find these, then you can't use Wubi and installing it on the C: partition won't help. PS to uninstall Wubi go to Control Panel, Add or remove programs, and double click on Ubuntu.

---

