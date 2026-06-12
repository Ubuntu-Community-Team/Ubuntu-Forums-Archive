---
title: "KVM instance creation fails on 10.04."
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by mc0001 on 2010-11-01
Hi guys,
I'm trying to install a virtual 10.04 image on a 10.04 server host, and the method I used that worked with 9.10 now fails. For example, I try to install with the following virt-install command (as root):


virt-install --name=star3--escience --connect=qemu:///system --ram=3000 --vcpus=1  --disk path=/disk2/images/star3--escience_60GB_Ubunut10-04.qcow2,size=60 --noautoconsole --os-type=linux --os-variant=ubuntulucid --accelerate --cdrom=/home/mc321/ISOs/ubuntu-10.04.1-server-amd64.iso --network=bridge:br0 --vnc

This fails with the errors:

========

Starting install...
Creating storage file sta 100% |=========================|  60 GB    00:00
ERROR    internal error unable to start guest: libvir: QEMU error : cannot set ownership on /home/mc321/ISOs/ubuntu-10.04.1-server-amd64.iso: Permission denied

Domain installation may not have been
 successful.  If it was, you can restart your domain
 by running 'virsh start star3--escience'; otherwise, please
 restart your installation.
ERROR    internal error unable to start guest: libvir: QEMU error : cannot set ownership on /home/mc321/ISOs/ubuntu-10.04.1-server-amd64.iso: Permission denied
Traceback (most recent call last):
  File "/usr/bin/virt-install", line 943, in <module>
    main()
  File "/usr/bin/virt-install", line 839, in main
    start_time, guest.start_install)
  File "/usr/bin/virt-install", line 894, in do_install
    dom = install_func(conscb, progresscb, wait=(not wait))
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 660, in start_install
    return self._do_install(consolecb, meter, removeOld, wait)
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 758, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1097, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error unable to start guest: libvir: QEMU error : cannot set ownership on /home/mc321/ISOs/ubuntu-10.04.1-server-amd64.iso: Permission denied

=======

I can't understand why it complains about permissions on that ISO file, as I'm running as root and that file exists:

# ls -al /home/mc321/ISOs/
total 1375048
drwxr-xr-x  2 mc321 mc321      4096 2010-11-01 08:38 .
drwxr-xr-x 12 mc321 mc321      4096 2010-11-01 09:00 ..
-rw-r--r--  1 mc321 mc321 715644928 2010-08-16 11:19 ubuntu-10.04.1-server-amd64.iso
-rw-r--r--  1 mc321 mc321 691011584 2010-01-25 18:53 XtreemOS-2.0-x86_64.iso

In fact, that XtreemOS iso (a Mandriva derivative) is what I installed successfully as a quest OS on the same machine when it was running 9.10.

Am I going mad?? Any help appreciated.

Ta,
m

---

### Post by mc0001 on 2010-11-01
Sigh, if only I'd spent another few minutes googling. I'll answer my own question and say that it was the libvirt config file in the upgrade that screwed things up. Its description, and solution, are given here:
[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/599910](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/599910)

m

---

