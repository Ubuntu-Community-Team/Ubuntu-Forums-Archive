---
title: "Ubuntu 10.10 hangs..."
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by umfolozi on 2010-12-15
I just installed Ubuntu 10.10 after using Vista to reduce it's partition size and then allocating an Ubuntu partition and a swap partition. All this on a Dell Inspiron 1721 laptop.
I then downloaded Ubuntu 10.10, burned it onto a DVD, and installed it into the Ubuntu partition.
It installed OK and booted up.
But I couldn't get at Vista anymore (it only listed embedded XP as an option, and that returned an 0xc0000098 error).
Downloaded EasyBCD on another machine and managed to fix the booting issue.
Both Vista and Ubuntu now boot.
Ubuntu works somewhat. The Chrome browser works and downloads data just fine. But Ubuntu hangs unexpectedly. It always hangs when the screensaver kicks in (after typing in the requested password). It always hangs if I attempt a System Administration function such as Synoptic? packages.
I tried (suggestion found by browsing):
sudo apt-get updates
sudo apt-get upgrade
sudo reboot
but that didn't fix things.
Any suggestions much appreciated.

---

### Post by sikander3786 on 2010-12-15
Welcome to the forums :-)

What do you mean by hanging? It goes blank screen or it just hangs in whatever state it is? Even the pointer gets stuck?

Which graphics card is there?

```
lspci | grep VGA
```

There might be proprietary drivers available under System > Administration > Additional Drivers. If available, install the recommended version and see if things get better.

Here is a troubleshooter for X freezes.

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by umfolozi on 2010-12-15
I can now consistently cause the screen to BLANK and the system to hang:
Using Nautilus, step through this path:
/sys/kernel/debug/dri
until two folders show: '0' and '64':
now click the '0' folder, and the screen blanks and the system hangs.

---

### Post by umfolozi on 2010-12-15
Sorry: just missed your reply.
Yes, it usually just hangs in whatever state it is in; the pointer can move but I get no response when clicking.
But I found that I can also make the screen blank before hanging (no pointer) as explained above.
It is an ATI Radeon.
I've also looked at the link you sent me - I'll read it some more.
Thanks!

---

### Post by umfolozi on 2010-12-15
ATI RS690M [Radeon X1200 Series]

---

### Post by sikander3786 on 2010-12-15
I can't say much on that. A quick Google revealed a bug here.

[http://www.gossamer-threads.com/lists/linux/kernel/1156556](http://www.gossamer-threads.com/lists/linux/kernel/1156556)

---

### Post by umfolozi on 2010-12-16
That link you sent me directs one here:
[https://bugzilla.kernel.org/show_bug.cgi?id=14485]("https://bugzilla.kernel.org/show_bug.cgi?id=14485")
It sounds as if it is my exact bug. It says it is resolved, but I have no idea how to interpret the resolution stated or how to apply the patch, if any.
I'd greatly appreciate some guidance.

---

### Post by sikander3786 on 2010-12-16
That states that a patch for that problem has been released. Make sure you have installed all the updates and that issue might go away ;-)

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by umfolozi on 2010-12-16
Thanks for responding so quickly.
Unfortunately I've already tried the update.
The search goes on...(I still can't believe I got though a day without google twenty years ago)...

---

