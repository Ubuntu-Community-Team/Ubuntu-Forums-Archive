---
title: "[SOLVED] Installing Ubuntu along XP Media Center"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Goop on 2007-12-02
Hey all,

After trying (and failing) to install Ubuntu 7.10 beside Windows XP Media Center Edition (I think x86 version), I've been thinking about trying it again, but I'm a little less willing to try it now. Last time, I couldn't get into XP no matter what I did, although my files on the XP partition were all still there. I don't want the same thing to happen again, because re-installing everything now would take quite a bit. The exact error I got was, after selecting XP from GRUB: "Disk read error, press Control+Alt+Delete to restart."

The x64 version of Ubuntu worked (almost) perfectly, apart from my USB network adapter failing after I found out I couldn't boot into Windows. I would use Ubuntu, but I'm not yet ready to completely switch from MS; some things I'm doing at home and for school require it.

So, is there a way I can install Ubuntu and still at least have a surefire way (be it floppy disk, CD or even USB pen drive) to get back to Windows if something goes wrong?

My specs:
AMD Athlon 64 Processor, 1.76GHz
Windows XP Media Center Edition
1GB of RAM
nVidia GeForce 7500 LE (which worked perfectly before)

---

### Post by Pumalite on 2007-12-02
You can install Ubuntu, and if things go wrong you can fix your MBR with your Install CD.

---

### Post by Goop on 2007-12-02
> **Pumalite said:**
> You can fix your MBR with your Install CD.

That's the only problem, I didn't get an XP Media Center CD with it. There is, however, a restore utility by HP on a second partition, which is what I used to restore my XP install before, after deleting all but the Windows and recovery partitions. The "restore" CD that is produced by the software that comes with the install only points the computer to that recovery partition, not anything on the disc.

Can I get a CD (apart from the official XP one) which can at least get me into recovery mode so I can run 'fixmbr'?

---

### Post by Pumalite on 2007-12-02
If you don't have an Installation CD, you can use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It also fixes your MBR.

---

