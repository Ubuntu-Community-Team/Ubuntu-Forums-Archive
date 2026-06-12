---
title: "Ubuntu 10.04 decided that it does not like my Video Card"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by webster922 on 2010-05-01
Hello - I installed Ubuntu 10.04 the day it came out onto my HP Pavilion a1206n (AMD64 Processor, 4 GB RAM, ATI Radeon Xpress 200 Graphics). All was going fine for a couple of sessions. Ubuntu could boot itself and run in full graphics mode. Now, for whatever reason, it will not run in full graphics mode.

First of all, after booting through GRUB, I can see the purple Ubuntu boot screen in full resolution for a few seconds. Then a console comes up saying > [     12.345678] Serial 8250 : too much work for irq17This is not a new message. When Ubuntu was working it would give me this message before booting too. After listing many irq17 lines, Ubuntu goes to low graphics mode (the one with with the X cursor) saying this:

> 
Ubuntu is running in low graphics mode

Your screen, graphics card, and input device settings could not be configured correctly.You will need to configure these yourself.I press OK with the X cursor and it gives me 5 options:

> What would you like to do?

*Run Ubuntu in low-graphics mode for just one session
*Reconfigure graphics
*Exit to console
*Troubleshoot the error
*Restart XI have tried all options but have not had any luck. The Running in low-graphics option just sends me to a list of too much work for irq17 errors. The Restart X option deos the same. I don't know why it started doing this after it was fully functioning. Any help getting my Ubuntu installation is greatly appreciated.

---

### Post by P4man on 2010-05-01
Now thats an error I havent seen yet. I googled a bit on it, and it seems related to a buggy.. fax/modem! I got that from here:
[http://lists.linuxcoding.com/rhl/2007q3/msg00657.html](http://lists.linuxcoding.com/rhl/2007q3/msg00657.html)

Can you go in to the bios and disable the (fax) modem? Im assuming you dont need it anyhow?

---

### Post by webster922 on 2010-05-01
I went into my BIOS and found I/O Device configuration. Under it was Parallel Port Configuration and a little option where I could choose between IRQ7 (Default) or IRQ5. I just disabled the parallel port altogether as I know I don't use it. But same problem. What's weird is that Ubuntu worked fine for probably 10-15 bootups/restarts. Then it decides that it cannot boot.

Maybe the I/O Device Configuration was not the correct option under my BIOS. Any other suggestions to turn off my modem? If I remember correctly I think it is a Motorola SM56 (or something along those lines).

---

### Post by P4man on 2010-05-01
If you see any serial ports to disable, it would be a better thing to attempt.


BTW does the Exit to console give you a working console? If so, have a look at

```
dmesg
```

maybe there is another hint in there.

---

### Post by webster922 on 2010-05-01
dmesg runs a list and stops after a long line of "too much work for irq17"s. The final listed is [   28.237872] serial8250 : too much work for irq17

Do you think it would help if I simply removed the modem?

---

### Post by P4man on 2010-05-01
is it removable? If so, sure, go ahead and try.

---

### Post by webster922 on 2010-05-01
I removed the modem (which was listed as a Motorola under XP but is actually an ASUS) and no more irq17 error! However Ubuntu still will not agree with my graphics card and wants to run in low graphics mode. Now when I press 'Run in low graphics mode' or 'Restart X' it only shows a blinking underscore (_). After that, nothing.

---

### Post by P4man on 2010-05-01
Did you try installing the ati proprietary driver? (it doesnt support your card)

Either way if you can access the console, try this:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by webster922 on 2010-05-01
No, I did not. It did work for a couple of reboots though. Do you think I should just reinstall 10.04?

---

### Post by webster922 on 2010-05-02
With my corrupt XP drive, I finally had a reason to upgrade to Windows 7. Now I can use EasyBCD with 7 rather than grub.bin with boot.ini in XP.

I reinstalled 10.04 too and am hoping that it lasts more than a couple of reboots.

Thanks for all your help P4man.

---

