---
title: "PXE install 12.04: can't add local mirror manually"
date: 2014-03-29
forum: Installation &amp; Upgrades
---

### Post by henrylaw on 2014-03-29
Trying to enable network (PXE) install from a local server. The initial boot works all right but I can't get it to find the complete contents of the ISO, either by NFS or HTTP.  I've found and used/modified many sources of info but currently I'm working off [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet), where it says 'When asked to select a mirror, go to the top of the list and select "Enter Manually"', but there's no "enter manually" option.  What am I doing wrong?

The TFTP configuration (dnsmasq) points to /home/tftpboot.  The default PXE config /home/tftpboot/pxelinux.cfg is a symbolic link to ./ubuntu-installer/i386/pxelinux.cfg/, in which the "default" file is```

DEFAULT ubuntu-12.04
LABEL ubuntu-12.04
      kernel ubuntu-installer/i386/linux
      append root=/dev/nfs netboot=nfs nfsroot=10.18.78.254:/home/iso/ubuntu-12.04.4-alternate-i386 initrd=ubuntu-installer/i386/initrd.gz
```
The directory /home/iso/ubuntu-12.04.4-alternate-i386 is validly accessible by nfs; I've checked it from another machine on the network.

ubuntu-installer/i386/linux is from the netboot.tar.gz for the relevant release.

The PXE boot completes, I can see the "linux" kernel being transferred by TFTP, and the installation dialog begins ... language, keyboard, host name, network config etc.  But then it comes to "Select a mirror", which is where I should be able to point the installation to my local server (10.18.78.254) but it just has two internet mirrors and won't let me add my own.

---

### Post by henrylaw on 2014-04-14
Well!  It's terribly simple: the place to enter your own mirror is _at the top of the list, out of sight_.  The installer helpfully positions the list to a sensible value for your own country, of course, so you don't see the "enter manually" option.  Page up madly and there it is ...

---

