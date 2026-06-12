---
title: "VMWare Tools"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by Tobywuk on 2007-11-25
I have just installed the latest vershion  of ubuntu on my mac inside WMWare Fushion.

It says on the bottom that it would be a good idea to install VMware tools so it works better. I click install and it seems to mount what Ubuntu thinks is a CD on the desktop. inside I have a .rpm and a .tar.gz file.

I am new to ubuntu, how do I install these VMWare tools?

---

### Post by ruggersway on 2007-11-26
Here is a link  [http://www.vmware.com/support/gsx3/doc/tools_install_lin_gsx.html]("http://www.vmware.com/support/gsx3/doc/tools_install_lin_gsx.html")

Follow the instructions there for more details.  Basically, Ubuntu should auto mount the disc - cd to /media/cdrom (or appropriate mount dir), unpack the tar.gz then cd to unpacked dir

$ cd vmware-tools-distrib/
$ sudo ./vmware-install.pl
$ sudo vmware-config-tools.pl

Hope this helps.

---

