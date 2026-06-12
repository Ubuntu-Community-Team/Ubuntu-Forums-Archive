---
title: "VMWare won't run after 7.10 upgrade"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by supaphly42 on 2007-10-29
I've been running VMWare since I first installed Ubuntu with no problems. I started with Edgy, then upgraded to Fiesty. Now that I've upgraded to Gutsy, VMWare won't load. I get the following error:
```
Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.
```
I did some research, and one site said to run:
```
/etc/init.d/vmware-player start
```
but that gives the output:
```

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

```
Any ideas? Thanks!

---

### Post by Aron Schatz on 2007-10-29
What version of VMWare is it?

I don't know if the player is the same as the server, but server needs the networking module rebuilt on every new kernel.

Maybe that needs to be done for the player as well...

---

### Post by supaphly42 on 2007-10-29
Product: VMWare Player
Version: 1.0.2 build-29634

---

### Post by Cornerville on 2007-10-29
I had the same problem with vmware server.  It has been removed from the vmware repository so you can't remove it and reload it from there.  You can, however, remove the version you have and go to the VMware site and download the new version, which is 1.04 in tarball format.  Unpack it and run runme.pl and it should work.  It did for me.  There are several threads on this forum that give more detailed instructions.

---

### Post by sum][one on 2007-10-29
sudo vmwaver-config --compile

try this one.. usually you have to do that after every kernel update.. to recompile vmware kernel drivers.. 

hope this helps.

---

