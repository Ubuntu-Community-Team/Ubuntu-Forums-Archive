---
title: "Installing TO network share?"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by OlegVekhov on 2007-07-24
Hello world! :)

I have 1 gb hard drive on my PC and 200GB on my Server...

Can I install Ubuntu, or, may be, other linux distro, to partition on my server (via NFS, SMB, iSCSI or ATAoE)?

Thats means I want /root on my HDD, and other mounts (/var /usr /home) on server HDD space.

Thanks for your answers!

---

### Post by iduriduridur on 2007-07-28
I think you might want to look at openfiler for this it does everything except ATAOE and is really easy to setup since it is like an appliance. 


I use this at work and it is very nice. 

Openfiler is a Storage Management Operating System. It is powered by the Linux 2.6 kernel and Open Source applications such as Apache, Samba, LVM2, ext3, Linux NFS and iSCSI Enterprise Target. Openfiler combines these ubiquitous technologies into a small, easy to manage solution fronted by a powerful web-based management interface. Openfiler allows you to build a Network Attached Storage (NAS) and/or Storage Area Network (SAN) appliance, using industry-standard hardware, in less than 10 minutes of installation time.

[http://www.openfiler.com/](http://www.openfiler.com/)

---

