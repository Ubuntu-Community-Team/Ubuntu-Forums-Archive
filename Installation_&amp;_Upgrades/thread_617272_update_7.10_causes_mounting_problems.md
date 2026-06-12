---
title: "update 7.10 causes mounting problems"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by Recon20k on 2007-11-19
I recently installed the 7.1 update and its causing me problems with matlab7.4.

I get an 'error creating the child process for this terminal' message when i try loading it.

The normal solution for this is:

sudo mount -a

and usually all is fine, but now when i try this i get the following error message:


mount: wrong fs type, bad option, bad superblock on 143.239.130.101:/usr/local,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

mount: wrong fs type, bad option, bad superblock on 143.239.130.43:/usr/local/matlab74,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

If i enter dmesg | tail the out put is as follows:

dmesg | tail
[ 42.014651] Failure registering capabilities with primary security module.
[ 42.279774] Bluetooth: Core ver 2.11
[ 42.279824] NET: Registered protocol family 31
[ 42.279826] Bluetooth: HCI device and connection manager initialized
[ 42.279828] Bluetooth: HCI socket layer initialized
[ 42.294686] Bluetooth: L2CAP ver 2.8
[ 42.294690] Bluetooth: L2CAP socket layer initialized
[ 42.558814] Bluetooth: RFCOMM socket layer initialized
[ 42.558827] Bluetooth: RFCOMM TTY layer initialized
[ 42.558828] Bluetooth: RFCOMM ver 1.8

Any help with this one would be greatly appreciated, i desperately need this programme to work right now!!

---

### Post by Recon20k on 2007-11-21
does anyone have any ideas with this one??

---

### Post by Newbie1978 on 2007-11-21
Well after a lot of frustration I discover that my new laptop don't work with Linux (hardware issues) this are my specs HP Pavilion Entertainment-center notebook PC DV6660se 64-bit 1.9 GHz AMD Turion 64 X2 TL-58 processor, 250 GB hard drive, 2 GB RAM Nvidia GeForce Go 7150 graphics if anyone manage to install a Linux distro in this model please help me

---

