---
title: "apt-get segfaults after last update"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by jstoner on 2010-02-22
This morning, I started applying the latest patches to my 9.10 desktop. Updated Firefox, no problem. Installed the list of "new installs" (alien, rpm, postfix, etc.), no problem. Updated Google Chrome, no problem. After that, Update Manager failed to start. I still had several updates to apply, like libxml2 and metacity. I could launch Synaptic but it crashed when I manually marked metacity for update. I tried using apt-get manually (sudo apt-get update) and found segfault messages in syslog:

Feb 22 10:06:23 rumadum kernel: [ 1968.878041] apt-get[2668]: segfault at 7f19f8e00b38 ip 00007f19f44d6ab5 sp 00007ffff7035b80 error 4 in libapt-pkg-libc6.10-6.so.4.8.1[7f19f4488000+bc000]

I ran "sudo apt-get clean" followed by another update = segfault. I rebooted. Same symptoms - Update Manager fails to start, apt-get segfaults.

I disabled the Google Chrome repository - and everything worked. I re-enabled the Google Chrome repository and everything still appears to be working. I applied all available updates after disabling the Chrome repository so could not test an actual update, but Update Manager doesn't crash.

So while my immediate problem is resolved, could this crop up again? Is it worth submitting more detailed info for a developer to look at?

Running 64-bit Karmic Koala (this system has been upgraded since 7.04, which seems like forever ago.)
AMD Sempron(tm) Processor 2500+
1 GB ram
apt 0.7.23.1ubuntu2

---

### Post by water-man on 2010-03-09
Hi Jef,

Sounds like the same problem as I'm currently having after the latest updates. Not just with Update, but also with Synaptic and Software Center:
Mar  9 17:15:29 ubuntu-laptop kernel: [ 5745.338487] software-center[10669]: segfault at a50f3e68 ip b5ba6a8c sp bff6e040 error 4 in libapt-pkg-libc6.10-6.so.4.8.1[b5b71000+bd000]
Mar  9 17:15:42 ubuntu-laptop kernel: [ 5758.109116] synaptic[10698]: segfault at c0070790 ip b77eea48 sp bfb97070 error 5 in libapt-pkg-libc6.10-6.so.4.8.1[b77b9000+bd000]
Mar  9 17:15:53 ubuntu-laptop kernel: [ 5769.541761] update-manager[10720]: segfault at bf871790 ip b61baa48 sp bf9ad860 error 4 in libapt-pkg-libc6.10-6.so.4.8.1[b6185000+bd000]

I'm also using Chrome and other Google apps (Picasa, Earth), so I'm interested in your cure for this problem.
Could share details?

Thanks
Herman
:frown:

---

