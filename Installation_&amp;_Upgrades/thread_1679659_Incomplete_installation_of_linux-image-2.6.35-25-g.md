---
title: "Incomplete installation of linux-image-2.6.35-25-generic-pae"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by Serenety Valley on 2011-02-01
I have made the same mistake as shown in this thread:

[http://ubuntuforums.org/showthread.php?t=1649664&highlight=2.6.35-25-generic-pae](http://ubuntuforums.org/showthread.php?t=1649664&highlight=2.6.35-25-generic-pae)

except with linux-image-2.6.35-25-generic-pae.

Even worse than that when the upgrade froze I waited for a couple of hours without being able to move the mouse or turn off the laptop by holding down the power button. I had to unplug the power and remove the battery in order to reboot.

When I rebooted I got a message similar to the command prompt below but I can't remember it exactly.
I then entered into recovery mode I could choose from:

linux-image-2.6.35-25-generic-pae
linux-image-2.6.35-25-generic-pae (recovery)
linux-image-2.6.35-24-generic-pae
linux-image-2.6.35-24-generic-pae (recovery)
linux-image-2.6.35-23-generic-pae
linux-image-2.6.35-23-generic-pae (recovery)

I chose 24 and it started up as usual. I then ran synaptic pacage manager and re-installed linux-image-2.6.35-25-generic-pae, header 2.6.35-25-generic-pae and one other 2.6.35-25-generic-pae pacage.

Upon turning on now either in Recovery or just turning on I get the message:

> Ubuntu 10.10 bob-R580 tty1

bob-R580 login:user
password:*******

Last Login: Tue Feb 1 14:02:40 GMT 2011 on tty1
Linux bob-R580 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux

Ubuntu 10.10

Welcome to Ubuntu!
*Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

user@bob-R580:~$
Pleeeeeeaaase help!

---

### Post by mörgæs on 2011-02-01
Is there any particular reason that you will run 25 and not 24?

---

### Post by Serenety Valley on 2011-02-02
It automatically updated to 25. I will happily go back to 24 if possible.

---

### Post by mörgæs on 2011-02-02
You just pick -24 from the list which appears at boot time. 

When a -26 comes around, you could give it a try.

---

### Post by Serenety Valley on 2011-02-02
No list now appears at boot time - it goes straight to the command line.

Should I try the advice in the thread that I quoted in my first post? as all of this is done in the terminal

---

### Post by mörgæs on 2011-02-02
You could try that. Sikander gives good advice. 

If the menu does not appear, just push left-shift at the beginning of the boot.

---

### Post by Serenety Valley on 2011-02-03
> **mörgæs said:**
> If the menu does not appear, just push left-shift at the beginning of the boot.

THANK YOU!THANK YOU!THANK YOU!THANK YOU!THANK YOU!THANK YOU!THANK YOU!THANK YOU!THANK YOU!THANK YOU!THANK YOU!THANK YOU!THANK YOU!

I can now use linux-image-2.6.35-24-generic-pae!

Is there any way to uninstall linux-image-2.6.35-25-generic-pae without uninstalling linux-generic-pae or linux-image-generic-pae so it will automatically boot into linux-image-2.6.35-24-generic-pae?

---

### Post by mörgæs on 2011-02-03
You are welcome :-)

I don't know how, sorry. 

If it was my machine, I would just let it run as it is. When -26 is released, you will automatically be able to boot into this one without selecting from the menu.

---

