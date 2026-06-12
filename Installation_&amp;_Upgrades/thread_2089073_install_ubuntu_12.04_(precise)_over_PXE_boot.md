---
title: "install ubuntu 12.04 (precise) over PXE boot"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by mrstaun on 2012-11-28
I have managed to get a working PXE boot (using Windows Deployment Services with a little hack) but facing annoying issues during the install setup.
 
During the install process I cannot get the installer to use my local FTP (I have extracted the ISO and copied the files to my FTP.). It fails and keep asking me for a mirror.
 
If I type in my FTP host and the directory manually it works
 
I am using a preseed file with this content
 
```
d-i debian-installer/locale string en_US
d-i console-keymaps-at/keymap select da
d-i keyboard-configuration/xkb-keymap select da
d-i netcfg/choose_interface select auto
### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
d-i mirror/protocol string ftp
#d-i mirror/country string manual
d-i mirror/http/hostname string 10.10.10.158
d-i mirror/http/directory string /alternate
# Suite to install.
d-i mirror/suite string precise
# Suite to use for loading installer components (optional).
#d-i mirror/udeb/suite string precise
```
 
The install is called from the WDS-menu like this
 
```
 LABEL Ubuntu 12.04 64bit auto
 MENU LABEL Ubuntu12.04 64bit Server auto
 KERNEL knl/alternate12.04
 APPEND auto=true priority=critical netcfg/get_hostname=VM-00006 preseed/url=ftp://10.10.10.158/config/simple.cfg vga=normal initrd=img/initrd-alternate12.04.gz

```
 
Does anyone have a working PXE-boot installation with either a Kickstart or Preseed file that fully automates the ubuntu installation
 
I found my problem. Had to change the preseed file like this (change http to ftp) :-)
 
```

d-i mirror/protocol string ftp
#d-i mirror/country string manual
d-i mirror/**ftp**/hostname string 10.10.10.158
d-i mirror/**ftp**/directory string /alternate/
d-i mirror/http/proxy string [http://10.1.1.2:8081/](http://10.1.1.2:8081/)

```

---

