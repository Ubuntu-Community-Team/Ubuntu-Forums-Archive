---
title: "Currently using &quot;breezy&quot; but dont know how to upgrade"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by MangoChutney on 2006-10-08
Hey all. Im currently using 5.10 "Breezy Badger" and when i bring up my update manager it theres a button where i can upgrade to "dapper".

I click upgrade, it downloads the upgrade tool, then i get this error message 

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

Anyone know what this means?

(Oh and just incase you diddnt notice, im VERY new to linux so when you reply, think of me as a 4 year old retard. Then i may just understand what to do.)

Thanks!

---

### Post by Titus A Duxass on 2006-10-08
Try:
Open a terminal
type " sudo aptitude dist-upgrade"

---

### Post by MangoChutney on 2006-10-08
mangochutney@mangochutney:~$ sudo aptitude dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done


Then nothing...

---

### Post by MangoChutney on 2006-10-08
If i download Drapper, put it on a CD and install it that way will i be able to keep all my files / music / settings etc.

The reason im trying to upgrade "from inside" breezy is because i want it to do exactly that, just upgrade. I dont want it to re-install. Does anyone know what to do?

Since i dont really know what im talking about, the above writings probably make absolutley no sence i may sound like an idiot but please bear with me.

Thanks.

---

### Post by dcstar on 2006-10-08
> **MangoChutney said:**
> If i download Drapper, put it on a CD and install it that way will i be able to keep all my files / music / settings etc.

The reason im trying to upgrade "from inside" breezy is because i want it to do exactly that, just upgrade. I dont want it to re-install. Does anyone know what to do?

Since i dont really know what im talking about, the above writings probably make absolutley no sence i may sound like an idiot but please bear with me.

Thanks.

Have you read the thread at the top of this forum?

---

### Post by MangoChutney on 2006-10-08
> **dcstar said:**
> Have you read the thread at the top of this forum?

No i diddnt, see i told you i was a retard!

Ima go off, read it, try some stuff and probably break everything. See you guys around when i figure this stuff out.

---

