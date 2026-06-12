---
title: "Update broke touchpad functions"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Tompalaz on 2010-03-31
Hey.
After todays updates some functions for my touchpad stopped working such as two-finger scrolling.
I'm on a MacBook so my "two-finger" right-click is also gone.

When I go to System -> Settings -> Mouse the touchpad section is gone :confused:

I think it all stopped working after two updates of 
xserver-xorg-video-vmware and xserver-xorg-input-vmmouse

Why do I even get updates for vmware?!

I've tried a reinstall of Beta 1

Anyone with the same problem or better, is there a fix for this?

---

### Post by mortti on 2010-03-31
I experience quite similar problems in my Asus EeePC 901, and most probably after the same updates today.

For exception I can see the touchpad page in the mouse settings, but two-finger scrolling, tap-click and the balanced control of my mouse by touchpad in general is totally broken right now.

A plain clear bug, I assume? The reporting system seems to be down though?

---

### Post by SushiR on 2010-03-31
Same here, Eee 901. And Launchpad is down for maintenance...narf

Forgot to mention that I'm on Kubuntu

---

### Post by Tompalaz on 2010-03-31
Good, then I'm not alone. Hopefully it will be fixed soon.

---

### Post by miegiel on 2010-03-31
I can barely use the touchpad here (xubuntu 10.04). :( If I tap the pad the mouse pointer dives in the top right corner most of the time, sometimes to the bottom left corner and sometimes it doesn't jump but still doesn't do any clicks. Of course 2 finger scrolling doesn't work either and the pointer is jumpy as hell.

---

### Post by miegiel on 2010-03-31
Launchpad is no longer read only, has anyone reported this yet ?

I guess I should add:
```
user@machine:~$ uname -srvmpio
 ________________________________________
/ Linux 2.6.32-18-generic-pae #27-Ubuntu \
| SMP Fri Mar 26 21:21:16 UTC 2010 i686  |
\ unknown unknown GNU/Linux              /
 ----------------------------------------
        \   ^__^
         \  (OO)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

user@machine:~$ sudo lshal | grep -B2 -A5 -i touch

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'  (string)
  input.device = '/dev/input/event7'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  linux.device_file = '/dev/input/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4/input/input7/event7'  (string)
```

---

### Post by mortti on 2010-03-31
There seems to be two new bug-reports that both have probably the same problem:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/552490](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/552490)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/552524](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/552524)

---

### Post by miegiel on 2010-03-31
Yay fixed \\:D/ with latest updates.

---

### Post by mortti on 2010-03-31
Yep, the new update, xserver-xorg-input-synaptics package (version 1.2.2-1ubuntu1), as also referred in the bug thread [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/552490](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/552490) seems to do the trick.

[I]Edit: 

Confirmed for Ubuntu 10.04 Netbook Remix on Asus Eee PC 901.
If the update also solved the problem with MacBook, then I guess this thread could be marked as solved?[/I]

---

### Post by dino99 on 2010-03-31
> **miegiel said:**
> Launchpad is no longer read only, has anyone reported this yet ?

I guess I should add:
```
user@machine:~$ uname -srvmpio
 ________________________________________
/ Linux 2.6.32-18-generic-pae #27-Ubuntu \
| SMP Fri Mar 26 21:21:16 UTC 2010 i686  |
\ unknown unknown GNU/Linux              /
 ----------------------------------------
        \   ^__^
         \  (OO)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

user@machine:~$ sudo lshal | grep -B2 -A5 -i touch

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'  (string)
  input.device = '/dev/input/event7'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  linux.device_file = '/dev/input/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4/input/input7/event7'  (string)
```

are you cracking our toy  :o
better to call the boss before desaster  :shock:

---

