---
title: "error in installation of VPN client"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by sangirasha on 2007-06-09
HI

i am using ubuntu on my personal laptop. i want to do my office work for that i need to install a VPN client. the VPN client provided by the company says that the installer is not compatible with multiprocessor kernels. when i uname ubuntu it says SMP (is it a type of multiprocessor kernel) kernel.

so at the time of installation i am getting error that the cisco module can't be created.
can you help me out in installing the same.

regards,
sudarshan

---

### Post by Michael Matthews on 2007-06-09
Your company supports Linux as VPN  ckient? How progressive!
My company it is windows only:(

But you might want to confirm what OS this SW actually supports.

---

### Post by sunken on 2007-07-15
ok, I did like this:
Text in *italic* is yours to find out

[LIST=1]
[*]install vpnc with synaptic
[*]open terminal, type **sudo pico /etc/vpnc/default.conf**
An example of default.conf:
[B]IPSec gateway *ip.to.vpn.server*
IPSec ID *VPNservergroupname*
IPSec obfuscated secret *cryptedpasswordfrompcffile*
Xauth interactive[/B]
[*]**ctrl+x**
[*]**y**
[*]**sudo vpnc-connect**
[*]enter your vpn user name, **enter**
[*]enter pin code or what ever kind of system you have, **enter**. Now you're inside vpn tunnel
[*]after you're done, **sudo vpnc-disconnect**
[/LIST]

---

