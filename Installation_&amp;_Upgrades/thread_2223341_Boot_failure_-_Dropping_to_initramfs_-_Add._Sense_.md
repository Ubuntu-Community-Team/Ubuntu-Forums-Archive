---
title: "Boot failure - Dropping to initramfs - Add. Sense: Unrecovered read error"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by sassi.matias on 2014-05-10
[COLOR=#000000][FONT=verdana]Hello everyone,

I can't boot to Ubuntu anymore in my HP DV7 Pavillion laptop. I upgraded to 14.04 recently and also have been using Vagrant to load some Virtual Machines (don't really know if this last info is useful). I've been having some problems with my AC adapter jack, causing the laptop to suddenly shut down, perhaps being this the root cause (corrupted boot or something). Whenever I try to boot the following message appeared:


[/FONT][/COLOR]```
[FONT=courier new] Gave up waiting or root device. Common Problems
- Boot args (cat /proc/cmdline)
- check rootdelay = '(did the system wait long enough?)
-missing modules (cat /proc modules; is /dev)
Alert! /dev/mapper/ubuntu--vg-root does not exist. Dropping to a shell
[COLOR=#000000]
[/COLOR][/FONT][COLOR=#000000][FONT=verdana][FONT=courier new]BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1)
built in shell (ash)
enter 'help' for a list of built in commands
(initramfs)_[/FONT]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=verdana]

I booted from a USB stick (unetbootin) and was able to get into Ubuntu succesfully (using the Try Ubuntu option). Performed a boot fix using Boot Repair and this is the output:

[/FONT][/COLOR][http://paste.ubuntu.com/7440054/](http://paste.ubuntu.com/7440054/)
[COLOR=#000000][FONT=verdana]

I also did a Disk Self Test (using Disks from Unity launcher) and found 2 bad sectors. In the SMART Attributes I see that "Airflow Temperature" is in red with a "Failed in the past" message.

When I rebooted again, the error message was gone:

 [/FONT][/COLOR][COLOR=#000000][FONT=verdana]Alert! /dev/mapper/ubuntu--vg-root does not exist. Dropping to a shell [/FONT][/COLOR][COLOR=#000000][FONT=verdana]

But a new error drops me to initramfs again.

The new message contains this text several times (with different numbers in it each time)

```

[FONT=courier new]Add. Sense [/FONT][/FONT][/COLOR][FONT=courier new]Unrecovered read error - auto rellocate failed
[/FONT][COLOR=#000000][FONT=verdana][FONT=courier new]sd 0:0:0:0 [sda] CDB:
Read(10): 28 00 00 07 b0 00 00 00 08 00
end_request: I/O error, dev sda, sector 503814
Buffer I/O error on device dm-0, logical block 0
ata1: EH complete
hidraw: raw HID events driver (C) Jiri Kosina
usbcore: registered new interface driver usbhid
ubhid: USB HID core drive
[/FONT][/FONT][/COLOR]
```
[COLOR=#000000][FONT=verdana]
and then the initramfs message again.

Is there a way to fix my boot in order for me to backup some important data that I was working with ? This is my main concern right now, to recover some projects. Also, having bad sectors in my HDD means that I should buy a new one right?

[/FONT][/COLOR][COLOR=#000000][FONT=verdana]Any insight would be greatly appreciated. Thanks in advance![/FONT][/COLOR][COLOR=#000000][FONT=verdana]
Matias.-
[/FONT][/COLOR]

---

