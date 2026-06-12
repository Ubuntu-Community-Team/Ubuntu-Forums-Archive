---
title: "Gnome-do working with Koala?"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-07-09
Is Gnome-do from the repos working in Karmic? I just installed it yesterday and it wont open for me??

---

### Post by zekopeko on 2009-07-09
try running it from the terminal with --debug

I'm running it in a virtual up to date karmic and it's working.

---

### Post by budluva04 on 2009-07-09
works good here, ive removed my bottom panel, and started using the "docky" skin, wonderful dock imo

---

### Post by ghindo on 2009-07-09
Working fine for me.

---

### Post by tawmas on 2009-07-09
Last week I hit a bug where it was actually running but not showing up. It happens mostly on my (Jaunty) netbook, but at times also on my (Karmic) desktop. Have you tried restarting gnome-do?

---

### Post by soapytheclown on 2009-07-09
using the latest ppa version on a 64bit is resulting in a seg fault for me:-

[PHP]
gnome-do --debug
Stack overflow in unmanaged: IP: 0x7f038ceefebc, fault addr: 0x7fff3a2cfff8
Stack overflow in unmanaged: IP: 0x498b34, fault addr: 0x7fff3a2cde60
Stack overflow in unmanaged: IP: 0x544de3, fault addr: 0x7fff3a2cee18
Stack overflow in unmanaged: IP: 0x498b34, fault addr: 0x7fff3a2cd6a0
Stack overflow in unmanaged: IP: 0x544de3, fault addr: 0x7fff3a2cde78
Stack overflow in unmanaged: IP: 0x544de3, fault addr: 0x7fff3a2cced8
Stack overflow in unmanaged: IP: 0x585c54, fault addr: 0x7fff3a2cba60
Stack overflow in unmanaged: IP: 0x585c54, fault addr: 0x7fff3a2cacc0
Stack overflow in unmanaged: IP: 0x585c54, fault addr: 0x7fff3a2c9f20
Stack overflow in unmanaged: IP: 0x585c54, fault addr: 0x7fff3a2c8ab0
Stack overflow: IP: 0x585c54, fault addr: 0x7fff3a2c7d10
At Unmanaged

[/PHP]

---

