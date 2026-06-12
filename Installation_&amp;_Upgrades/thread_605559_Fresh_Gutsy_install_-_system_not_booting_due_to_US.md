---
title: "Fresh Gutsy install - system not booting due to USB problem"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by aeolos on 2007-11-07
After a fresh install of Gutsy, my system hangs at startup. Starting without splash-screen so I could see some log messages told me this:

```
USB 1-1: Device not accepting address 2, error -62
```

Shortly followed by

```
Hub 3-1:1.0: Cannot enable port 2. Maybe the USB cable is bad?
```

The last message then floods my terminal. I'm running a clear vanilla install of Gutsy off the installation cd, on an AMD A8R-MVP motherboard and a K8 processor. Anyone able to help me? I've got a suspicion it's got to do with the usb kernel module, because it worked flawlessly in earlier versions of Ubuntu.

Also, booting with parameters "noapic" "irqpoll" "noirqdebug" doesn't solve the problem.

Thanks in advance.

---

### Post by Pumalite on 2007-11-07
Disconnect all devices connected to your computer, disable floppy in BIOS if you have a floppy and try again.

---

### Post by aeolos on 2007-11-07
Doesn't work. Neither should it be the solution in my opinion: the exact same hardware configuration worked in earlier versions and disconnecting hardware shouldn't be the solution to a malfunctioning kernel module (if that's the case) If I hadn't tried this yet, I wouldn't have posted. 

I wonder if anyone else is experiencing the same problems and if someone has a solution...

---

### Post by Pumalite on 2007-11-07
The kernel is not maulfunctioning. I have Gutsy installed in 5 different computers and all work fine.

---

### Post by aeolos on 2007-11-08
Ok, after fiddling with startup parameters and whatnot I am now able to get into my system. Everything works fine, except for the fact that my terminal (tty1) is flooded with the same message over and over again. Doesn't matter which port I plug something into (doesn't matter what I plug in, either), it keeps spamming. I've got a suspicion it's got something to do with ehci_hcd. 

After killing this kernel module, the spamming stops and all works fine. According to launchpad, a bug with this module is fixed the next kernel. Thanks for your time.

---

