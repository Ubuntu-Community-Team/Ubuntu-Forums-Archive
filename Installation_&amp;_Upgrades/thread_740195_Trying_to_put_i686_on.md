---
title: "Trying to put i686 on"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by koresho on 2008-03-30
Hi everyone, I am using a Core 2 Duo so I'd like to use the i686 kernel. Problem is, when I search Synaptic for "linux-image" it pulls up a list with generic (what I'm using), i386, rt, virtual, server, and xen. No 686 kernel is available, apparently... I am using Ubuntu Hardy, any help is appreciated.

---

### Post by Pumalite on 2008-03-30
I got this through updates:

Linux pumalite-desktop 2.6.24-12-generic #1 SMP Wed Mar 12 23:01:54 UTC 2008 i686 GNU/Linux

---

### Post by koresho on 2008-03-30
Alright, how can I tell if I got that as well? 
Or, how could I tell if my kernel is using SMP?

---

### Post by Pumalite on 2008-03-30
Post:
uname -a

---

### Post by koresho on 2008-03-30
oh, ah ha. I apparently got the same update you did... thanks!

---

### Post by Pumalite on 2008-03-30
Glad we got it sorted out.

---

### Post by jman82s on 2008-04-28
Actually, I'm not 100% sure on this, but I think that 'uname -r' just tells you your computer's actual physical architecture (i386, i686, etc.), and not the architecture your current kernel is designed for. I just installed the linux-686 packages, but they are tiny (less than 1MB), so I'm not really sure what they do.

I'll update if I find something. Has anyone compiled a custom kernel on Ubuntu? I gave it a shot, but it didn't seem to go too smooth...:(

---

