---
title: "Doesnt let me log in :("
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by riddem on 2011-10-25
Hi. some days ago I upgraded happily to 11.10. But as I reastarted the  machine, and logged in, I could no longer get on wireless. After much  trial ands error I found that it was probably some driver that was not  effected. So I tried to sort it out.. Then as I start up anew, it goes  through the regualr motions, all the way unto the Ubuntu load screen.  Then I get a long string saying things like: ...
* Stopping System V runlevel compability       [ok]
                                      fsck from util-linux 2.19.1
udevd[343]: SYSFS{}= will be removed in a future udev version, please  use ATTR{}= to match the event device, or ATTRS{}= to match a parent  device, in lib/dev/udev/rules.d/45-hpdjconsole.rules:6  (and rules 9,  12, and 15)

Further it goes on to say that:
/dev/sda5: clean, 324189/36249600 files, 73689112/144979200 blocks (check in 3 mounts)
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 *starting apparomor profiles            [ok]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * stopping failsafe boot delay
 * stopping System V initalistaion
Stopping stopping stopping, a whole lot of things... 
(I havee to handtype this- But I hope anyone here  get the general idea and have some useful tips to a total greenhorn like me:razz:)
In advance, Thanks!

---

### Post by 2F4U on 2011-10-25
Try the key combination Ctrl-Alt-F1 (or F2, ..) and see if you can get to a virtual console and login. You will then be able to look into some log files to see what goes wrong:
- type dmesg
- cat /var/log/Xorg.0.log
- cat .xsession_errors

---

### Post by riddem on 2011-10-25
Whew! Thansk for reply! I get a lot of code by typing dmesg... I supoose by "cat" you meant I should put dmesg i nfront of the commandos? More code... What shall I do.. retype any specifics for you?

From what I can read it says it failed to map virtual space, couldnt get adress for reserved range, and couldnt allocate to requested local FB memory
Gart initialization failed also.. as did GAL
CMMQS initialization failed
some handles are not valid
IRQ 51 is disabled
and it ends on a sombre note saying 14.320643] init: lightdm main process (1127) terminated with status 1.
and some errors to remount..

I`m ot terribly helpful here I`m sure, but if you can give me som advice on how to proceed I would be very happy to oblige.

Thanks!

---

