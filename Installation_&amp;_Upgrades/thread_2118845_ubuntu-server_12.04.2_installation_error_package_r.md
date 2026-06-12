---
title: "ubuntu-server 12.04.2 installation error: package retrieval failed"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by surfer on 2013-02-22
i tried to install
ubuntu server 12.04.2 amd64 with unetbootin.

the install via unetbootin on a flash drive failed because a file could not be retrieved from the flash drive.

the file is:
pool/main/l/linux-lts-quantal/crypto-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_amd64.udeb

i checked and listed /cdrom/pool/.... and found that the file was there but the last character of the filename was missing; i.e. the listed file just read
/cdrom/pool/main/l/linux-lts-quantal/crypto-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_amd64.ude


is the filename too long or what is happening?

---

### Post by steeldriver on 2013-02-22
yes that issue seems to have been around for a while - some workarounds here

[http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r](http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r)

IIRC last time I encountered it, I ended up copying the whole ISO on to the USB as well and then pointing the install process at that when it got stuck - I can't remember the exact menu sequence to do that though

---

### Post by surfer on 2013-02-22
ok, thanks!

the "Startup Disk Creator" seems to do a better job. but the server version still did not work. i am installing the alternate iso now...

---

