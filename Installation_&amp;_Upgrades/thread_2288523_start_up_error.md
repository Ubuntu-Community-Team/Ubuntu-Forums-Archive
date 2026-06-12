---
title: "start up error"
date: 2015-07-28
forum: Installation &amp; Upgrades
---

### Post by micknotten on 2015-07-28
My Asus laptop stucks in startup:
[   0.023512] Ignoring BGRT: invalid status 0 (expected 1)
[   0.742970] ACPI PCC probe failed.
starting version 219 
welcome to emergency mode! ....
...
try again to boot into default mode. 

This works, it starts up as usual.
What can I do to get rid of this startup error?
I'm using version 15.04

Thanks, Mick

---

### Post by dino99 on 2015-07-28
with new kernels comes new handled features; but some complaints are logged, and might have been silenced, when the kernel does not find a valid chipset providing these features. These 'warnings/errors' are simple disturbing 'info' and should not be the 'stuck' reason for your system: run journalctl to glance at something else that could explain your issue

[http://ubuntuforums.org/showthread.php?t=2264380](http://ubuntuforums.org/showthread.php?t=2264380)

---

### Post by grahammechanical on 2015-07-28
Ubuntu 15.04 is the first version of Ubuntu to use SystemD as an init system and the message "starting version 219" is referring to SystemD. It is nothing to worry about. That message will not be there in 15.10.

The same could also be said about the message "ACPI PCC probe failed." That also disappears from 15.10. I saw those two messages for most of the development period of 15.04 and for the early part of the development period of 15.10. They are now gone. And they never stopped Ubuntu from loading. They may have delayed the loading of Ubuntu but they did not stop it.

I never did see the message "Ignoring BGRT." Is Ubuntu loading? Is Ubuntu working correctly when it does load?

Regards.

---

### Post by micknotten on 2015-08-01
Hi, thanks for you responses and sorry I'm reacting so late...

I ran the journal report; the red lines were, apart from the already mentioned ones. " fsck failed with error code 4", "failed to start File system check on boot device" and "failed to start console system startup logging". Further more, I don't know if this has something to do with it, I get now and then a system error' or better crash report. It is this package: "virtualbox-dkms 4.3.10-dfsg-1ubuntu5 [origin unknown]" 
I don't have the slightest idea how to solve this...As I understand for the startup error I have to wait till the next release?
Thanks for helping! 
Mick

---

### Post by arlenn2 on 2015-12-21
do you dual boot with windows 8. 8.1, 10?

Set windows to shutdown completely 
[http://windowsten.info/tutorials/5767-how-to-fully-shut-down-windows-10](http://windowsten.info/tutorials/5767-how-to-fully-shut-down-windows-10)

Windows 8 is identical.

---

