---
title: "Can't turn off computer after upgrading to 11.04"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2011-05-03
After I upgraded to Ubuntu 11.04, I could normally turn off my computer.

Every time when I tried to turn off the computer by pressing the 'shut down the computer' button at the upper right corner of the screen and selecting 'Shut down', it will first appear as if it is shutting down normally, but in less than half minute, it stops at a console-like screen with the last few lines of text
```

gnal 15, shutting down

init: dbus main process (775)
      killed by TERM signal
init: Disconnected from system bus

```
and then stopped there. I then have to manually and physically power off the computer.

Any suggestions?

---

### Post by Physicist on 2011-05-06
Bump; nobody has this issue?

---

### Post by onefish on 2011-05-06
Solution: Don´t turn off your computer. ;)

---

### Post by Physicist on 2011-05-06
To avoid wasting electricity, I must turn it off. :P

---

### Post by danellisuk on 2011-06-25
I've started noticing shutdown problems on Ubuntu 11.04, this is a particular problem as the machine runs MythTV and needs to shutdown reliably by itself.

In-case we have any correlation on hardware, this is a summary of the machine:-

[LIST]
[*]Antec Fusion Remote Veris Black case with LCD and Remote
[*]Gigabyte GA-MA78LMT-US2H Motherboard
[*]KWorld PC1602T Dual DVB Tuner
[*]Asus GT 430 1GB DDR3 (Connected via HDMI)
[/LIST]

This is what the display showed during a particular test using 'sudo reboot':-

```

The system is going down for a reboot NOW!
acpid: exiting

init: ssh main process (717) terminated with status 255
init: tty4 main process (938) killed by TERM signal
 * Stopping web server apache2     init: tty5 main process (943) killed by TER
M signal
init: tty2 main process (973) killed by TERM signal
init: tty3 main process (974) killed by TERM signal
init: tty6 main process (979) killed by TERM signal
init: cron main process (994) killed by TERM signal
init: Disconnected from system bused by TERM signaling down...fied domain[ OK ]

```

I think the last entry has been overwritten as it does not look valid.  Next I need to determine how to diagnose this type of problem.  It is a bit tricky when you can't control the machine.  At some point I will start unplugging various components, but this is still tricky as the shutdown problem is not consistent.

---

