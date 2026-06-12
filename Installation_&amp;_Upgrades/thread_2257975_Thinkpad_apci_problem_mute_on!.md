---
title: "Thinkpad apci problem: mute on!"
date: 2014-12-23
forum: Installation &amp; Upgrades
---

### Post by wgw on 2014-12-23
I upgraded with a clean install of 14.04lts-64. When I first installed it, I got sound. Then I installed quite a few packages (most from here:  [http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr) ). Now my sound is dead.

The problem is that the /proc/acpi/ibm/volume is muted and the thinkpad audio control is readonly: 

```
bill@bill-laptop:~$  sudo cat /proc/acpi/ibm/volume
level:		12
mute:		on

bill@bill-laptop:~$  sudo echo unmute > /proc/acpi/ibm/volume
bash: /proc/acpi/ibm/volume: Permission denied
```

With a fresh install, I have on the other hand:

```
ubuntu@ubuntu:~$ sudo cat /proc/acpi/ibm/volume
level:		11
mute:		off
ubuntu@ubuntu:~$ sudo echo mute > /proc/acpi/ibm/volume
bash: /proc/acpi/ibm/volume: Permission denied
```

What could have set that volume control to mute? dmesg in both configurations (initial install and after other packages installed) is the same, read only:

```
[   27.317410] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
```

Is there any way to set that to mute: off?

---

### Post by wgw on 2014-12-24
I still don't understand this, but I found a fix at [http://ebb.org/bkuhn/blog/2014/06/08/volume-hotkeys-thinkpad-t60.html](http://ebb.org/bkuhn/blog/2014/06/08/volume-hotkeys-thinkpad-t60.html). 

It allows the buttons to unmute the thinkpad_apci module.

> 
To enable the volume control buttons:
sudo gedit /etc/rc.local
and add the line:
sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask 

---

### Post by tgalati4 on 2014-12-24
That is a common fix for thinkpads.  That fix is also used to help detect other Fn keys so they can be repurposed or assigned to other funtions.

---

