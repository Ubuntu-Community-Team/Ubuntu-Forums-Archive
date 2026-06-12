---
title: "Can't install usb-creator nor gddrescue"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2018-05-13
I am running Xubuntu 17.04 and am trying to create a bootable USB thumb drive for Xubuntu 18.04.  I got it downloaded.  I tried to install usb-creator (to create the bootable thumb drive) into xubuntu 17.04 using Synaptic, but it wouldn't install.  I got ```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/udisks2/gir1.2-udisks-2.0_2.1.8-1ubuntu1_amd64.deb
  404  Not Found [IP: 91.189.91.26 80]
```.  Can anybody tell me how to get this installed????

---

### Post by monkeybrain20122 on 2018-05-14
*buntu 17.04 has reached end of life since Jan, there is no more supported and all the packages have been removed from server. Don't know about xubuntu but isn't start up disk creator already installed?

---

### Post by again? on 2018-05-14
> **Ralph L said:**
> I am running Xubuntu 17.04 and am trying to create a bootable USB thumb drive for Xubuntu 18.04.  I got it downloaded.  I tried to install usb-creator (to create the bootable thumb drive) into xubuntu 17.04 using Synaptic, but it wouldn't install.  I got ```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/udisks2/gir1.2-udisks-2.0_2.1.8-1ubuntu1_amd64.deb
  404  Not Found [IP: 91.189.91.26 80]
```.  Can anybody tell me how to get this installed????

Just use dd to write to USB.
```
sudo dd bs=4M if=[COLOR="#696969"]/path/to/iso[/COLOR] of=[COLOR="#696969"]/dev/sdX[/COLOR] status=progress && sync
```
Use the path to your ISO and replace /dev/sdX with your USB drive. (*******double check you are using right drive *******)

To show USB drive....
```
sudo fdisk -l
```

---

### Post by Ralph L on 2018-05-14
Thanks to you guys for responding.  I really appreciate it!!!

Guber2:  Your solution worked perfectly.  I got the thumb drive loaded, it booted up and I installed xubuntu 18.04.

Thanks again

---

