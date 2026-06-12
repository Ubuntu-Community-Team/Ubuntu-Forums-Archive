---
title: "creating a url structure similar to Ubuntu mirrors for local install"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2011-03-18
I need to create an http url at my laptop to have a Ubuntu installation begin within my laptop on a Xen environment.
This is how the final thing will look like 
[http://bderzhavets.wordpress.com/2008/10/28/install-ubuntu-intrepid-server-pv-domu-at-xen-33-port-via-httpgetco-centos-52-dom0/](http://bderzhavets.wordpress.com/2008/10/28/install-ubuntu-intrepid-server-pv-domu-at-xen-33-port-via-httpgetco-centos-52-dom0/)
the host and client are both going to be my laptop,
I Google d and came across apt-mirror and some other packages.
I do not want to archive entire 15 GB Ubuntu repositories on my machine.
It is not possible to use a CD,ISO,loop mounted disk (reason mentioned below).
I have tried using netboot image on local machine which failed because 
if you are attempting to create a virtual machine on a hardware which does not support VT
virt-manager installer necessarily needs a URL of this sort 

[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/)

any other option to create guest OS is simply grayed out.
The unfortunate part is my Ethernet connections do not work when I boot with Xen-4.0 and a pv-ops Dom0 kernel from Jeremy's tree.Which is where I have to do this work.So I have to create a URL structure which is similar to Ubuntu mirrors.So how can I do this in bare minimum so that at least the console boots and once the console comes I can do some work.

---

