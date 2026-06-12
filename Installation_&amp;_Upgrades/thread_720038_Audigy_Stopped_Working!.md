---
title: "Audigy Stopped Working!"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by Cresho on 2008-03-09
using hardy heron alpha 6 and audigy stoped working after update.   I know its not the darn hardware because I reinstalled.  after reinstall, it worked fine but after this last update as of today, it was shot to hell!

This is crazy!

anyway, I tried using the comprehensive audio fix from the forums and its still a no go!  this is what I&#4611;&#4712; stupid scim!!   pops up and types my stuff in arabic!  anyway, I did a lspci -v and this is what Ihave

01:09.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
	Subsystem: Creative Labs Unknown device 1001
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at 9000 [size=64]
	Capabilities: <access denied>


it works in windows and not no more in linux!

---

### Post by Tomana on 2008-03-09
go to Volume Control > File > Change Device > then select your Audigy card

moving right along ...

Volume Control > Switches Tab > uncheck Audigy Analog/Digital Output Jack

Reboot  (log out/in might work but I haven't tried it so I don't know for sure)

see if any of that helps

---

### Post by Cresho on 2008-03-10
nope...Icant even select the device in default mixer tracks under sound preferences.  the volume will not launch due to no hardware 


I tried what you said before and that was a no go.  the other step was to uninstall alsa and reinstall it into the kernel..that awas a no go

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Tomana on 2008-03-10
Most interesting that the volume control will not launch because of no hardware, since
the hardware shows when you run lspci -v

Personally, I would just save anything important to a CD or DVD and format the hard drive
and re-install Ubuntu.  Maybe a Ubuntu Guru will come along soon and give you a quick fix.

Cheers

---

### Post by Cresho on 2008-03-11
I found out the problem, since I'm using the alpha 6 hardy heron, a new kernel was installed so my grub automatically runs that.  So from further reading in another thread, I realized that I needed to use the older kernel in the grub menu.  I booted up with the older kernel and sound was working.  So I modified grub and added pound signs to remove the new kernel from grub menu list. :)  The new kernel is just...new!  So until they work on that further, ill be using the older one.

---

