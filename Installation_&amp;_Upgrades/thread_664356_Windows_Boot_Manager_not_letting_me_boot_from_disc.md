---
title: "Windows Boot Manager not letting me boot from disc"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by mofmog on 2008-01-11
So I had my Dell Inspiron 1420 running with Ubuntu 7.10 and Windows Vista working pretty dang well all things considered. However, after I installed the Vista updates, my Vista install pretty much died. So I booted up into Linux and wiped the Vista partition so I could reuse the space. This was an absolutely stupid choice on my part because every time I boot up now, the "Windows Boot Manager" comes up and says:

"Windows failed to start. A recent hardware or software change might be the cause. To fix the problem: blahlbhalbh"

"OK" I tell myself. I'll just reinstall Ubuntu. It's a pain, but hey, I deserve it for being such an idiot. Well for some reason, my laptop won't boot from CD. I know the CD works because it boots from the computer I'm currently writing this post from and I've set CDs to be booted from first in the BIOS settings, and I've even tried explicitly telling the Dell to boot from disc. No dice. I keep getting the friggin' Windows Boot Manager screen. I can't use my Vista CDs because it's in my dorm room back at college and I don't get back up there until a week. Of course- if I can't even boot from the Ubuntu CD, how should I expect the Vista to boot?

So is there any way to boot from a CD? Or at least wipe Windows Boot Manager so I can somehow install GRUB over it?

---

### Post by Amstell on 2008-01-11
this has saved me a bunch of times.  Now that I don't dual boot i don't need it but its good

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by mofmog on 2008-01-11
I bet it's good but I still can't boot from CD due to Windows Boot Manager somehow overriding any other sort of booting. This is seriously distressing :(

I tried disabling booting from the HD in the bios settings but for some reason now it says that there's nothing to boot from.

---

