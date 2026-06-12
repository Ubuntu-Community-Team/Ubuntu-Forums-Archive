---
title: "installing on Pentium D problem"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by DeThPhase on 2006-10-20
Hi there.

I have used linux before with no problem. I built a computer this summer and now that I want to put linux on it I cant (oh the horror!).

Specs:

Pentium D 805 2.66
Foxconn 945G7MA-8KS2 mobo
1.8 gigs of ram DDRII 533
Raptor 74 gig sata hd
maxtor 250 gig pata hd
samsung 16x dvdr
soundblaster audigy 4
ati radeon x550 256mb pci-e

I have been running win xp pro x-64 with no problem. I can install ubuntu i386 with no problem but when I try to install 686, 686smp or amd64 it freezes right after it says uncompressing the kernel and everything locks up.

A forum that I visited said something about taking out all your memory except for 1 chip.....so I did that but it then would lock up immediatly after loading X. My keyboard and mouse would become unresponsive. Oh and they are plugged into the ps/2 ports.

I could use some help.

---

### Post by taurus on 2006-10-20
You mean your Ubuntu won't boot when you upgrade your kernel from i386 (default) to i686!

---

### Post by DeThPhase on 2006-10-20
Yes but it also wont install from the amd64 disc as well......its like anything newer than 386 won't work.

---

### Post by deadgobby on 2006-10-20
I have a Celeron D and you'll need to use the 386 CD. 686 is still buggy and besides. You have a intel chip and not AMD. 386 works just fins and runs swell on this Intel Celeron D chip. 
Gobby

---

### Post by DeThPhase on 2006-10-20
Well thats fantastic......the whole point of getting a dual core processor is to well.....use 2 cpus......and it is amd64 compat.

---

### Post by deadgobby on 2006-10-20
> **DeThPhase said:**
> Hi there.

I have used linux before with no problem. I built a computer this summer and now that I want to put linux on it I cant (oh the horror!).

Specs:

Pentium D 805 2.66
Foxconn 945G7MA-8KS2 mobo
1.8 gigs of ram DDRII 533
Raptor 74 gig sata hd
maxtor 250 gig pata hd
samsung 16x dvdr
soundblaster audigy 4
ati radeon x550 256mb pci-e

I have been running win xp pro x-64 with no problem. I can install ubuntu i386 with no problem but when I try to install 686, 686smp or amd64 it freezes right after it says uncompressing the kernel and everything locks up.

A forum that I visited said something about taking out all your memory except for 1 chip.....so I did that but it then would lock up immediatly after loading X. My keyboard and mouse would become unresponsive. Oh and they are plugged into the ps/2 ports.

I could use some help.
 I notice your vid card, you may need to config or install the driver for it.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 If you used Linux before, you may want to try Suse too. Suse has excellent HW detection. The bummer side of things is that it is a 5 cd install or a 2 DVD install. Not as easy as Ubie. I run both suse and ubie and different pc's. Oh Mepis bost to have gread HW detection too. 
Gobby

---

### Post by DeThPhase on 2006-10-20
Yeah I might try another distro. First I'm going to try the alt. ubuntu cd.....then I might go with suse or fedora.

---

