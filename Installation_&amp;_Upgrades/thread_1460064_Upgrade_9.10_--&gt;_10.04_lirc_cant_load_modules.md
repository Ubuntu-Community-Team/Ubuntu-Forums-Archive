---
title: "Upgrade 9.10 --&gt; 10.04 lirc cant load modules"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by TSlackM on 2010-04-22
Hi, i have a problem with lirc not starting in the new 10.04 rev

when i restart lirc it says:
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

dmesg says:
lirc_imon: disagrees about version of symbol lirc_register_driver
lirc_imon: Unknown symbol lirc_register_driver

only way i found to fix this is to reinstall lirc, lirc-modules and lircx not sure if i need to 
reinstall all of them but when i do i can start lirc again and everything is fine until i reboot
 and get the same error once again.

any tips on how to fix this?


Solved Thanks to andla:
sudo mv  /lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko  ~/. 
sudo dpkg-reconfigure lirc-modules-source

---

### Post by finn on 2010-04-30
I have the same problem with a Mythbuntu that I just upgraded from 9.10 to 10.04.

Some particulars that I noticed are:
[LIST]
[*]lirc worked after the first reboot without a problem
[*]the next time I rebooted, I got to mythfrontend, but no lirc was running
[*]ssh'ing in and running 'sudo /etc/init.d/lirc restart' followed by 'sudo /etc/init.d/gdm restart' resolves the problem until the next reboot
[/LIST]

I suspect the new boot optimisations are at fault here, somehow lirc does not get started in time before the window manager and mythfrontend are started.  There seems to be no good documentation at the moment on how to force the system to wait for lirc to be running before starting the frontend.

Edit: since the updates on 05 May 2010, lircd runs by itself after a reboot, without me having to restart it.

---

### Post by andla on 2010-05-01
I had the same problems after upgrade to 10.04. For me the problem was caused by a outdated lirc_imon.ko module located in */lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_imon/ * This module  caused the lirc-modules-source pkg not to rebuild a new lirc_imon.ko. 
So my solution to the prolem was: 
sudo mv /lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko ~/. 
sudo dpkg-reconfigure lirc-modules-source

---

### Post by TSlackM on 2010-05-01
Thanks!, its now working great again.

---

### Post by drumz on 2010-05-08
I'm running into the same problem on my 9.10 -> 10.04 upgrade.  I removed /lib/modules/2.6.32-21-generic/ since I don't have that kernel installed.  I've tried reinstalling lirc, etc. and I get the same thing:

dmesg output:
```
[  804.806758] lirc_imon: disagrees about version of symbol lirc_register_driver
[  804.806762] lirc_imon: Unknown symbol lirc_register_driver
```

So I did this:

```
locate lirc_imon.ko
```
looked at the results and did this:

```
ls -l /lib/modules/2.6.32-22-generic-pae/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko /var/lib/dkms/lirc/0.8.6/2.6.32-22-generic-pae/i686/module/lirc_imon.ko /var/lib/dkms/lirc/0.8.6/build/modules/lirc_imon.ko
-rw-r--r-- 1 root root 38964 2010-04-28 14:42 /lib/modules/2.6.32-22-generic-pae/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko
-rw-r--r-- 1 root root 38728 2010-05-08 22:03 /var/lib/dkms/lirc/0.8.6/2.6.32-22-generic-pae/i686/module/lirc_imon.ko
-rw-r--r-- 1 root root 38728 2010-05-08 22:03 /var/lib/dkms/lirc/0.8.6/build/modules/lirc_imon.ko
```

Noticing the wrong filesize in /lib/modules I did this:

cp /var/lib/dkms/lirc/0.8.6/build/modules/lirc_imon.ko /lib/modules/2.6.32-22-generic-pae/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko

and i was able to modprobe the module and start lirc

and now lirc starts on boot again.

---

### Post by WolverineFan on 2010-09-10
The solution here looks like it will fail every time there's a kernel upgrade.

I would suggest trying to remove lirc-modules-source.  It shouldn't be necessary for the lirc_imon driver unless you're installing from a PPA.

But then I've been wrong before :)

---

