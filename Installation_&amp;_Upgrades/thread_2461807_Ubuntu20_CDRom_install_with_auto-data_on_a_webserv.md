---
title: "Ubuntu20 CDRom install with auto-data on a webserver"
date: 2021-05-07
forum: Installation &amp; Upgrades
---

### Post by jakl-zhaw on 2021-05-07
Hello

I would like to auto install my Ubuntu from CDRom ( iso as cdrom attached ) using a user-data stored on a webserver from a previous installation.

I'm struggeling with the IP-parameters during the boot-prompt. 
I've tried the following ip-params to bring up the ens160 interface:

ip=*ip*::*gateway*:*netmask*:*hostname*:*interface*:none

or this annotation:

ip=1.2.3.4 netmask=255.255.255.0 gateway=1.2.3.1 

Then, if I start the installation, I've got the error that says:
ipconfig: can't parse the ip adress

As params for the user-data I used :
autoinstall ds=nocloud-net;s=https://1.2.3.5/

Also tried to use ks= Param for kickstart, but again, I cannot assign any IP or even bring up that interface during the initial-install-boot.

Tried to add those values before the "---" and after ... same result.

Any help would be apprciated.

Stefan

---

