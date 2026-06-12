---
title: "Trying to install server"
date: 2013-02-27
forum: Installation &amp; Upgrades
---

### Post by toddadvecor on 2013-02-27
We inherited an old Dell poweredge 2650 and I'm trying to install Server 12.04.2 on it. It's for an internal project so while I'd rather a newer server, guess there wasn't any money in the budget for it. Fine. Problem is that the CD Rom drive is dead and the bios won't boot from USB.

I configured a PXE server and it connects to that fine and appears to run the installer ok. 

I used the steps from [http://is.gd/GflK14](http://is.gd/GflK14) & [http://is.gd/cyExSQ](http://is.gd/cyExSQ) to get the PXE server running. Had to change some of the variables, like the iso I got doesn't have a 'casper' directory everything is in 'install'. Stuff like that.

Anyway, the install stops at mounting the CD Rom drive (yeah, because it's dead). But I don't get why if I'm running the PXE install it's even balking at that.

I feel like I'm so freking close but I'm missing something easy. Has this happened to anyone else?

---

### Post by CharlesA on 2013-02-27
You might have better luck with the miniiso.

Have you tried disabling/unplugging the broken CD drive before trying to install?

Have you tried this?
[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

---

### Post by toddadvecor on 2013-02-28
Thanks for your reply. I tried  taking the dead CD drive out but that didn't seem to be it. I got it to work by directing the 'initrd' to the 'install/netboot/ubuntu-installer/i386/initrd.gz' instead of just 'install/initrd.gz'

A couple of odd hurdles later it's up and running. Now I just have to figure out why I'm getting an unresolved host error when trying to apt-get install things.

I'm normally a developer/programmer so this is a bit out of my wheelhouse. I appreciate the reply though!

---

### Post by darkod on 2013-02-28
Sounds like you don't have DNS server set correctly. Did you use static IP on the server as you should? Did you set dns servers?

---

### Post by MAFoElffen on 2013-02-28
So it sounds like a non-working CD drive. It sounds like the BIOS doesn't support USB boot or does it?

Does it have a working floppy drive? If so, even from a bios that doesn't support usb boot...  you could boot a grub floppy image and from there boot your usb device with the server install ISO... Or boot the iso image file directly. 

Charles-
Nice interesting read... but wasn't that for installing Ubuntu through a working Ubuntu server running PXE Server services? (separate box on the network...)

DNS problems during the install... Hmmm.  Goes along with what I think CharleA meant to post:
[https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)
which has directions for setting up the temp local dhcp IP ranges, connection checks and setting up the gateway through the server that PXE is booting from and using to go "through" for the install. Then when PXE boots from the attached box, it goes through that server, which is already connect to the outside world.. Just what I was thinking on that...

---

### Post by CharlesA on 2013-02-28
I was mostly posting the link so they could have a base for getting PXE working, but I think your link works better. :)

---

### Post by MAFoElffen on 2013-02-28
> **CharlesA said:**
> I was mostly posting the link so they could have a base for getting PXE working, but I think your link works better. :)
Yes... But the PXE Server would have already have assumed DNS and Internet connections working already.

So the PXE client's DNS problem might be in how that PXE "server" is gateway configured for it's PXE clients. (As in those instructions)

---

