---
title: "Ubuntu 11.10 Command line only installation fails over and over again."
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by LinuxFan999 on 2011-10-31
I am testing the "Install a command-line system" mode on the Ubuntu 11.10 alternate CD, but it fails every time. I tested this on Virtualbox and Virtual PC 2007 on 2 different host computers, one running Windows Vista SP1 64bit, and another Running Windows 7 SP1 32bit. On Virtualbox, the install appears to finish, but after unmounting the ISO image and rebooting the Virtual machine, the cursor blinks a few seconds, then the Ubuntu boot screen appears for a split second, then a message from Virtualbox appears about pointer intergration, and I accept it. After accepting the message, I see the cursor blinking again, and after a few seconds, the Virtual HDD and network activity stops, and the cursor blinks continuously untill the VM is reset or turned off. In Virtual PC, a similar thing happens(except there is no message about pointer intergration). I haven't tested this on real hardware because I have none reserved for testing. Has anybody tested a similar setup and experienced it fail?

---

### Post by papibe on 2011-10-31
Try pressing Ctrl+Alt+F1. It should get you a text mode login screen.

There's a recurrent bug on the minimal install CDs. (More info here: [Bug #695658]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658"), [Bug #700686]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/700686"), and [Bug #831752]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/831752")).

To fix it, as explained in Bug #695658:
> (1) Edit /etc/grub.d/10_linux (e.g. "sudo nano -w /etc/grub.d/10_linux") and comment out the line containing "vt.handoff", or change the number from 7 to some lower number. (I tried it both ways; they both worked.)
(2) Run "sudo update-grub" to apply the new configuration.
(3) Reboot. A usable virtual terminal with a login prompt comes up automatically.
That way you should boot into a text mode console (as it should with a minimal install).

Try it out, and let us know how it went,
Regards.

---

### Post by LinuxFan999 on 2011-11-01
> **papibe said:**
> Try pressing Ctrl+Alt+F1. It should get you a text mode login screen.

There's a recurrent bug on the minimal install CDs. (More info here: [Bug #695658]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658"), [Bug #700686]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/700686"), and [Bug #831752]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/831752")).

To fix it, as explained in Bug #695658:

That way you should boot into a text mode console (as it should with a minimal install).

Try it out, and let us know how it went,
Regards.
Tried it just now and it worked. I was able to log in to my command line install, but I would like more instructions on the permanent fix.

---

### Post by MAFoElffen on 2011-11-01
> **LinuxFan999 said:**
> Tried it just now and it worked. I was able to log in to my command line install, but I would like more instructions on the permanent fix.
Two things currently work for that:

1. Open up /etc/grub.d/10_linux with privileges. > Go to line 69 > remove "vt.handoff=7" > Save and Exit.

2. Open up /etc/default/grub with privileges. > Go to end of file and add a separate line that says "linux_gfx_mode=text". > Save and exit

- Run "sudo update-grub" 

Sidenote- The correct way is broken at the moment --> The Kernel boot parameter "text" is supposed to boot an Ubuntu kernel into runlevel 2-4, multi-user text session.  I opened upstream bug on that for 3.x kernels = not working at all at the moment.

---

### Post by RouterRat on 2012-01-14
This did not fixed my problem.

I've tried setting it to a lower number didn't work.
Commented the whole line didn't work.

Added "linux_gfx_mode=text" didn't work

changed it to linux_gfx_mode="text" didn't work

changed to linux_gfx_mode=text didn't work.


In short it's not getting fixed on a Emachines E725 laptop.
10.04 works like a charm but I really wanted to get the new GUI.

The reason I tried ubuntu was I couldn't get wine working correctly on debian and I remember I've done it once in Ubuntu.

In short I'll never upgrade to the lates releases :) untill it's all good.

---

