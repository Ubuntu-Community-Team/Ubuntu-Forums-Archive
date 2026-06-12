---
title: "No package for acroread in the Synaptic Package Manager..."
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by scho on 2007-02-09
I couldn't find the acroread package in the Synaptic Package Manager. Should I add some
repository ? I'm using Edgy.

By the way, I installed acroread manually using tar files from Adobe website and I could make
it working but after upgrading something, yesterday, it hasn't been working. It gives the following
message when I run it in the terminal and doesn't show any acroread program backgroud,

(acroread:23230): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

Any idea ?

---

### Post by Stemp on 2007-02-09
acroread is part of the multiverse repositories.
Read [Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu") to add them ;)

---

### Post by scho on 2007-02-13
Thanks for reply. Currently, I am using Edgy and using every repository checked in the Synaptic
Package Manager.

But I can't find acroread from repositories.

---

### Post by confused57 on 2007-02-13
> **scho said:**
> Thanks for reply. Currently, I am using Edgy and using every repository checked in the Synaptic
Package Manager.

But I can't find acroread from repositories.

I had the same problem on an Ubuntu Lite install with a Dapper server base...couldn't find acroread or mozilla-acroread in Synaptic...I ended up downloading from Adobe & installing that way.

You might want to use automatix2, it will automatically install it for you:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Add:  I've used automatix on 10-15 installations, including Breezy, Dapper, Edgy, Xubuntu(Dapper & Ubuntu), SimplyMepis, and haven't had any problems...I have read of some having issues with using it.

---

### Post by Stemp on 2007-02-13
BTW the acroread package is only available for the i386 architecture.

---

