---
title: "Help: Dapper won't boot!"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by rfrey74 on 2006-06-16
Hey all,

I upgraded to Ubuntu 6.06 LTS and had no problems.  The only wierd thing that happened is that during boot up, starting PCMCIA services failed.  With Ubuntu 5.10, the boot process never did any thing with PCMCIA.  Anyway, that didn't stop my system from booting, and I don't think I use PCMCIA anyway, so I ignored it.

Just this morning, I got an upgrade alert, and so I upgraded.  Most of it was Gnome upgrades, but there was a new kernel in the upgrades as well.  After I upgraded, I was prompted to reboot.  So I did.  During reboot, it gave me the message about PCMCIA failing, but right after that, it tried to load manual drivers.  Unfortunately, at that point it dumped me to a terminal view to tell me that loading manual drivers failed, and the booting process halted.

What should I do about this?

Here is the kernel in question
2.6.15-25-686

My system:
nForce DDR400 mobo w/2.0 GHz Athlon XP and 1.5 GB RAM
WD 200 GB HDD
Turtle Beach sound card
ATI Radeon video card and TV Wonder Pro card (fglrx)
Netgear ethernet card

As an addendum, kernel 2.6.15-25-386 does boot just fine.  However, I would still like to get the 686 kernel working.  Any help will be greatly appreciated.  Thanks in advance.

---

### Post by rfrey74 on 2006-06-16
Here is a little more information on the problem.  The boot up process looks like this:
```

* Reading files needed to boot...            [ok]
* Preparing restricted drivers ...           [ok]
* Start basic networking...                  [ok]
* Starting kernel event manager...           [ok]
* Loading Hardware Drivers...
devd-event[3035]: run_program: '/sbin/modprobe' abnormal exit
                                             [ok]
* Loading PCMCIA services...                [fail]
* Loading manual drivers...
devd-event[3398]: wait_for_sysfs: waiting for '/sys/devices/platform/i82365.0/bs' failed

```
"Loading manual drivers..." is the log_begin_msg in the module-init-tools start up script.  This script apparently opens the /etc/modules file and iterates through modprobing the modules listed in that file.  Unfortunately, I don't think its having much success even reading the file.

contents of my /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
fglrx

I hope this additional information helps in diagnosing the problem.  Thank you in advance for all your help.

As an addendum, it turns out that the directory i82365.0/ does not exist on my machine.  That would explain the error.  How do I fix it?

---

### Post by rfrey74 on 2006-06-17
Still looking for help on this one.  If you have any ideas on how to get the 686 kernel to boot, don't be shy.  I realy would appreciate help with this issue.  Thanks in advance.

---

### Post by rfrey74 on 2006-06-17
OK, never mind. :-& 

I went into Synaptic and marked linux-image-2.6.15-25-686 for complete removal.  Then I rebooted the machine.  Then I did the following in the terminal.
```

# sudo apt-get install linux-686

```
Then I rebooted the machine once more.  I booted into the 686 kernel, and everything went fine.  I guess there was just a gremlin in the update.  When in doubt, reinstall.

---

### Post by jarkema on 2007-01-15
Just a reminder, don't remove your linux images if you don't have a previous install to fall back on.  I tried this solution after my first install and made my computer completely unbootable.  I had to reinstall ubuntu from scratch.  Luckily I had an install CD.

I didn't have any data on the computer yet, so all I lost was a couple of hours of time.

---

