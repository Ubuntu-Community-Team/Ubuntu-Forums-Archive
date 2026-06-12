---
title: "kernel panic with Ubuntu 6.06 install CD"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by dugh on 2006-09-05
I tried installing Ubuntu 6.06 on an emachines t6410 desktop (amd64) with samsung 17" lcd.  It kernel panics on install with the amd64 ubuntu cd.  Many others have apparently had this problem but I haven't seen the solution.  The cd isn't corrupt, it boots fine on my amd laptop.

I'll try the latest edgy knot 2 release, but I'd rather not have to use that.

the messages look like:
acpi_bus_scan
i_event_init
pci_mmcfg_read+239 
->kernel panic

More info: I am installing using an external dvd/cd drive.  I have no choice because the internal one was shredded by another cd.  Also I have a 2nd SATA drive connected, although the primary one is not SATA, and I am only installing to the primary drive.  Also there is a wireless pci card in the computer as well.  Lastly, I upgraded the ram recently, but there is nothing wrong with the ram as far as I can tell.

---

### Post by dugh on 2006-09-05
I ran the kernel with acpi=off noacpi and it got a little farther but then stopped with the error "device not accepting address".

---

### Post by dugh on 2006-09-06
With Ubuntu edgy knot 2, I get the error:
buffer I/O error on device sr0, logical block 175676

adding "irqpoll" to the boot options will probably fix that, but I'm probably just going with the older Ubuntu 5.10 instead.  That seems to be the solution other people have come up with.

---

### Post by dugh on 2006-09-06
One last update for others trying to install Ubuntu on an emachines amd64 desktop:

Trying Ubuntu 5.10, 6.06, and edgy knot 2, no options allow it to be installed.  Other people with similar machines cannot get any Linux distro installed on their emachine aside from damnedsmalllinux or puppy linux.

I disconnected the media card reader from the motherboard too (since that was a problem some people had), no help.

These are some of the different boot options I tried, which did not work:
irqpoll
acpi=off
noacpi
nolapic
pci=noacpi
ide=nodma
ide=reverse
pci=routeirq
acpi=routeirq

---

### Post by dugh on 2006-09-10
Knoppix 5.01 is booting and running just fine (just normal problems like I need to get the wireless card working).

It'd be nice if Ubuntu could do the same hardware detection stuff Knoppix does.

I also tried the i386 Ubuntu cd (edgy knot 2).  It gave a different error, but still had problems regardless of flags like pci=noacpi, acpi_skip_timer_override, enable_8254_timer , etc.

I'm not giving up on Ubuntu yet though, I'm waiting for an internal cdrom drive.  I'll see if booting from that makes any difference.

---

### Post by dugh on 2007-06-27
Ubuntu Edgy now works on our Emachines desktop.

Actually it works even better than on a brand new Dell laptop (D820).

---

### Post by soundcyst on 2007-12-25
I am a little new to Ubuntu, but thinking of switching my stepdad's computer over from Windows due to... well, Windows.

He's got an eMachines T6410, and since I'm only home for another week or so I want to make sure I'm not spending a full day figuring out how to make Ubuntu work.

So my question is, can you give me a little bit more in the way of details on how you made it work? Is 6.06 the same as Edgy, or does 7.10 work?

Thanks in advance!

---

### Post by soundcyst on 2007-12-27
bump.

maybe even someone who doesn't have a T6410 but knows enough to know if it will work based on the [specs on cnet]("http://reviews.cnet.com/desktops/emachines-t6410-media-center/4507-3118_7-31466283.html")?

---

