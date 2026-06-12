---
title: "ubuntu server 64bit Alpha 2 (candidate) no login after install"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by whoop on 2010-01-12
I installed ubuntu server 64bit Alpha 2 (the candidate for alpha 2 that is). 

The installation went successful, but when I start the system I get no login prompt.
It just states that the hard disk doesn't need checking (fsck messages), not even a blinking cursor. I can connect to the machine via ssh.

When I hold shift upon booting and choose recovery console (in grub) and choose for normal resume I do get a login prompt...

Any ideas?

Also I get the ubuntu logo on screen when booting the machine (bit strange for a server, but that could just be personal).

---

### Post by Ibidem on 2010-01-12
Hello,
You might try updating xserver-xorg-core & xserver-common.  There have been several reports of yesterday's version not working, but today's works alright.  The working version is ....ubuntu5,  while ubuntu4 doesn't work.
Hope this helps,
Ibidem

---

### Post by whoop on 2010-01-12
> **Ibidem said:**
> Hello,
You might try updating xserver-xorg-core & xserver-common.  There have been several reports of yesterday's version not working, but today's works alright.  The working version is ....ubuntu5,  while ubuntu4 doesn't work.
Hope this helps,
Ibidem

Thanks, but that's not it, system is fully updated, furthermore I am talking about ubuntu server here, which (hopefully) doesn't include any X components at all....

Just to make sure, it isn't some kind of (silly) feature I am not aware of, is it?

---

### Post by Puck7 on 2010-01-12
This has been confirmed in the #ubuntu-testing irc channel on freenode this morning, it is a bug. Sorry I can't provide a bug number for it.

---

### Post by whoop on 2010-01-12
> **Puck7 said:**
> This has been confirmed in the #ubuntu-testing irc channel on freenode this morning, it is a bug. Sorry I can't provide a bug number for it.

A cool, that's some info at least, cheers.

Ah, here is the report: [https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/506297](https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/506297)
Should have used google before posting here, sorry guys...

---

