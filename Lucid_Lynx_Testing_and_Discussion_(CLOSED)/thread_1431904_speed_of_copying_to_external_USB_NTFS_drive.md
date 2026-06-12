---
title: "speed of copying to external USB NTFS drive"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Myxb on 2010-03-17
First of all, I still have Karmic install and would not at the moment install Lucid. I hope some of you with 64-bit installs could test whether Lucid have a bug I experience with Karmic. Sorry, that I write this without actually installing Lucid and trying it myself.

Under Karmic I have a nasty bug with 2.6.31-20 kernel. When I copy a large file to an external USB NTFS drive I have a really low average speed of about 6-8 M/s. I usually copy a 50G file to and from an external drive so this speed is painful indeed. The iotop shows instant read/write speeds of 4-12 M/s, but mostly in the range of 6-8 Mb/s.

On the other hand, under the mainline kernel 2.6.32-9, the average speed stays at about 25-27 M/s, the instant speeds iotop shows is between 12 and 41 M/s, but mostly stay between 24 and 33 M/s.

I am running a 64-bit system and have seen a similar behavior on at least one other 64-bit system I've installed. However, the 32-bit systems seem to behave OK with the standard kernels.

So I am really interested whether problem is _fixed_ in the 2.6.32 kernel OR the Ubuntu standard kernels are _broken_ after applying Ubuntu-specific patches? It would be a pity to have the issue in the next release...

---

### Post by Seventh Reign on 2010-03-17
30-32 mb/s average transfer speed with the .32-16 kernel.

---

### Post by Myxb on 2010-03-17
Thanks for the input! Hope I will get similar results after upgrade :)

---

### Post by psyke83 on 2010-03-17
Another factor is NTFS-3g itself. The version used in Karmic/Lucid has performance issues.

See [bug #392204]("https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/392204") and [bug #513197]("https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/513197").

---

### Post by forcecore on 2010-03-17
They will fix it at least in final if not sooner, i have too 3 NTFS usb drives (i have not encountered with that problem because i have 32bit).

---

