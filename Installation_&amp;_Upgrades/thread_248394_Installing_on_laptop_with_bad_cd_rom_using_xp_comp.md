---
title: "Installing on laptop with bad cd rom using xp computer"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by y50a7XpWRH66IV on 2006-09-01
Hi guys,

I am trying to install Ubuntu 6.06 on an old laptop with a broken cdrom drive.

I have the ubuntu cds so what I want to do is:
Use a floppy to boot the laptop.
Point it to a copy of ubuntu on my xp machine.

I have looked through the help pages etc, but can't find anything that can help me what this.

Any ideas?

Cheers!

---

### Post by Jussi Kukkonen on 2006-09-01
Three choices:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
Two problems: It's not trivial. You'll need services running on the other machine that might be hard to find for Windows.

[http://instlux.sourceforge.net/](http://instlux.sourceforge.net/) 
A windows program that'll install a linux distro from the net.

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
Same thing "by hand"

I'd try instlux.

---

### Post by y50a7XpWRH66IV on 2006-09-01
Cheers mate.

Can instlux *stream in* the files or cd image from a local computer instead of via the internet?

I have the ubuntu cds already.

Cheers!

---

### Post by Jussi Kukkonen on 2006-09-01
What does "stream in" mean? 

I'm not too familiar with instlux (there's suspiciously little documentation), but generally speaking the computer that is serving the files needs to have some kind of a server running, whether it's in a local network or not is not important  -- e.g. the netBoot installation needs a tftp server.

Is there a working Windows on the laptop already? In that case you could copy the needed files for netboot to the laptop (over the network), and then do the netboot-from-windows-procedure. In any case I don't think you can use the CDs you have...

---

