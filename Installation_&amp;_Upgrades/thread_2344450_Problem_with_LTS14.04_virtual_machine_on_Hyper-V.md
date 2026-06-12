---
title: "Problem with LTS14.04 virtual machine on Hyper-V"
date: 2016-11-25
forum: Installation &amp; Upgrades
---

### Post by Crispness on 2016-11-25
Hi

I have been installing a new 14.04LTS virtual machine on a Hyper-V host.
The host is a Win2012 R2 Standard Hyper-V and the initial installation seems to work fine using the ubuntu-14.04.2-desktop-i386.iso

But one installed and restarted, and after installing a bunch of stuff needed for this machine
[LIST]
[*]openssh-server
[*]nfs-common
[*]rpcbind
[*]xinetd
[*]ksh
[*][openjdk-7-jdk]("http://apt.ubuntu.com/p/openjdk-7-jdk")
[*]subversion
[/LIST]
and then restarting, each time I try to update, either from command-line or the desktop, the system is happy to shutdown, but won't restart.

Luckily I have a pre-update backup that I can restore, but I don't want to run an un-updateable system.

Any suggestions on what I should be doing to try and get these updates on, and the machine to reboot safely?
TIA

---

