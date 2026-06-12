---
title: "Huge problem with Windows 'Fixmbr' and Grub"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by SmiteMeister on 2008-03-06
Sorry for the length, but this is actually summarized.  This has been a LONG ordeal, and I don't want to leave an important detail out.

I've had my laptop dual booted with ubuntu and windows with no problems for quite a while.  Though, I've had ubuntu for a while, I've still yet to really use it.  The problem came a few days ago when I (stupidly) took 20 GB of unpartitioned space and made a partition out of it (yes, I'm lazy and it took me that long to get around to making the partition).

Anywho, as your gringes I can feel as I'm typing this indicate, it messed things up.  Neither windows or linux would boot.  After a while of searching forums, I was able to reinstall grub.  Windows still would not boot.  As per another site, i used ms-sys to try to fix the MBR on windows.  I was prepared for linux to be knocked out, but at the same time, I thought windows would be back.  This once again knocked them both out of commission.

Next, i used the windows boot disk to do a fixboot and fixmbr.  Neither worked, and the fixmbr, made linux unrecoverable.  I have 2 friends who are (in my eyes) linux masters, and after a while of looking at it, they had to reinstall ubuntu.  This got my linux back, but my windows still wont work.  In fact, the boot cd will not even work.  It freezes after "Setup is inspecting your hardware configuration screen".  The hard drive light stays lit the entire time.

I've researched this, and the only solution I could find involved disconnecting the hard drive to get it past this point, reconnecting it, then doing Fixmbr.  I have no problem with this, but does anyone know from what is described here if this will just put me into an infinite loop?  If so....HEEEEELP!!!

Thanks in advance for putting up with my newbie-ness :)

---

### Post by syg00 on 2008-03-06
From a (Linux) terminal enter this and post the results```
sudo fdisk -l
```

---

### Post by SmiteMeister on 2008-03-06
No problem.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06ec06eb

     Device    Boot       Start                   End             Blocks     Id   System
/dev/sda1      *                1                 5099      40957686       7   HPFS/NTFS
/dev/sda2                  5100                 7842      22033147+    7   HPFS/NTFS
/dev/sda3                  7843                 9729      15157327+    5   Extended
/dev/sda5                  7843                 7904          497983+   82  Linux swap / Solaris
/dev/sda6                  7905                 9729      14659281      83  Linux

---

### Post by syg00 on 2008-03-06
mmmm ... that looks sane. No ideas at the moment - sorry.

---

### Post by SmiteMeister on 2008-03-06
Yeah.  This is kind of a difficult one.  If worse comes to worst, then I'm going to use my Ubuntu disk to erase my windows partition, and if need be, the entire HD, and start from scratch.  I'm HOPING someone has an answer though:confused:

---

### Post by syg00 on 2008-03-07
Just re-read your initial post. I had thought you couldn't get the fixmbr to run at all. The fact it did run (even only once) precludes what I was suspecting when I asked for that listing.
Wonder if you have filesystem corruption - does Ubuntu mount it o.k. ???. What about running chkdsk from recovery console on the 'doze CD.

---

### Post by jimv on 2008-03-07
Here's what I would do.

Boot up from your Ubuntu CD.  Use the partition manager to wipe out all of the partitions (back up anything that you want to keep) and just leave your drive unpartitioned.  Boot up from your XP disk and partition your disk with the XP installer.  Leave room for Ubuntu if you intend on installing it again.  Once you have XP installed, then go ahead and install Ubuntu.

I just noticed that was what you said already...oops.

---

