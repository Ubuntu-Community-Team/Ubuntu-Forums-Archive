---
title: "Latitude 2100 Karmic Upgrade Touchpad Problem"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by pdemchick on 2010-02-26
My Dell Latitude 2100 worked fine with the pre-installed Ubuntu 9.04.  I upgraded to 9.10 and the touchpad stopped working.  Restored to factory condition and it again worked fine.  I re-did the upgrade, this time asking it not to delete the obsolete items.  Same problem.  Any suggestions would be appreciated.

---

### Post by rijidij on 2010-03-09
Hi,
I don't mean to hijack your thread, but I'm having the same problem with my Sony Vaio VGN-T2XP.
It worked fine under Jaunty, but since doing an in-place upgrade to Karmic the touchpad is non-responsive.

Here is my lshal output:
```
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.linux.driver = 'psmouse'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input_0'
  info.callouts.add = {'hal-probe-vmmouse'} (string list)
  info.capabilities = {'input', 'input.mouse', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'AlpsPS/2 ALPS GlidePoint'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input_0'  (string)
  input.device = '/dev/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'AlpsPS/2 ALPS GlidePoint'  (string)
  input.x11_driver = 'synaptics'  (string)
  linux.device_file = '/dev/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input8/event8'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.callouts.add = {'hal-probe-vmmouse'} (string list)
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'PS/2 Mouse'  (string)
```

There is also no "Touchpad" tab under System->Preferences->Mouse.

I hope somebody can help.

TIA,
Craig

---

### Post by rijidij on 2010-03-09
Still looking for a more permanent solution, but for now I have got it working by editing my xorg.conf file as per this thread: [Clicky]("http://ubuntuforums.org/showthread.php?t=1366507").

Cheers,
Craig

---

### Post by rijidij on 2010-03-10
**Doh!** 
I was using the wrong version of the kernel... :-\" 

Solved by an upgrade to Grub2, and update.
I also had to remove my previous edit to xorg.conf

---

