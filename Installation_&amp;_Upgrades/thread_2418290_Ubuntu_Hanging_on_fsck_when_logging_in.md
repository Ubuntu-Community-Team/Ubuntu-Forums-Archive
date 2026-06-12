---
title: "Ubuntu Hanging on fsck when logging in"
date: 2019-05-04
forum: Installation &amp; Upgrades
---

### Post by Keilan on 2019-05-04
Hey all,

I've recently installed Ubuntu on a part of a second hard drive (dual booting with Windows 10). I set it up with 3 partitions, /boot, root, and /home. After install when I first logged in it got stuck with the following message:

[ATTACH=CONFIG]283189[/ATTACH]

After waiting about 8 hours with no change, I powered off the computer and restarted, at which point it worked. However when I restart again, I'm back at the same point. Any help would be appreciated! I did check the hard drive's SMART info from my bootable USB and everything seemed to be fine.

Thanks!

---

### Post by Bashing-om on 2019-05-04
Keilan; Hey - hey ....


What results do you get when running the file system check (fsck) from a liveDVD(USB) ?

[INDENT][INDENT]can't hurt to look
[/INDENT][/INDENT]

---

### Post by Keilan on 2019-05-04
Hey Bashing-om, thanks for the help! It looks fine as far as I can tell:

```

root@ubuntu:/home/ubuntu# fsck /dev/sda2
fsck from util-linux 2.33.1
e2fsck 1.44.6 (5-Mar-2019)
/dev/sda2: clean, 309/61056 files, 23732/243968 blocks
root@ubuntu:/home/ubuntu# fsck /dev/sda3
fsck from util-linux 2.33.1
e2fsck 1.44.6 (5-Mar-2019)
/dev/sda3: clean, 153856/3055616 files, 2227028/12207104 blocks
root@ubuntu:/home/ubuntu# fsck /dev/sda4
fsck from util-linux 2.33.1
e2fsck 1.44.6 (5-Mar-2019)
/dev/sda4: clean, 1082/17408000 files, 1386980/69628160 blocks

```

I did get an error mentioning my GPU when booting into the live CD - it didn't stay on my screen long enough to get a good look at it. I'm using a GTX 1660 TI if that's possibly related.

---

### Post by Bashing-om on 2019-05-04
Keilan; Yup -

System now looks clean.
What now when you boot the installed system?

[INDENT][INDENT]maybe yes
[INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Keilan on 2019-05-04
The same problem unfortunately, or at least a very similar one. There were 3 new messages because the fsckd-cancel message:
[OK] Started Modem Manager.
[OK] Started Accounts Service.
[OK] Dispatcher daemon for systemd-networkd

Then the same issue - fsckd cancel followed by PPM init failed (-110).

---

### Post by Bashing-om on 2019-05-04
Keilan

A fresh install here!  As I have not a clue how Perl Package Manager  (PPM) could play into this;
Did you verify the .iso file ?
Did you verify the copy to the install medium ?

My ignorance might show as I have no other idea presently on how to proceed,


[INDENT]but
[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT][/INDENT]

---

### Post by Keilan on 2019-05-05
I didn't verify the ISO file after download, maybe there is an issue there. I'm going to try to download again (maybe Ubuntu 18.04 this time and then upgrade once installed) and I'll remember to verify this time. Thank you so much for your help.

---

### Post by Bashing-om on 2019-05-05
Keilan; Well -
sounds reasonable:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by ya-paulle on 2019-05-05
> **Keilan said:**
> Hey all,

I've recently installed Ubuntu on a part of a second hard drive (dual booting with Windows 10). I set it up with 3 partitions, /boot, root, and /home. After install when I first logged in it got stuck with the following message:

[ATTACH=CONFIG]283189[/ATTACH]

After waiting about 8 hours with no change, I powered off the computer and restarted, at which point it worked. However when I restart again, I'm back at the same point. Any help would be appreciated! I did check the hard drive's SMART info from my bootable USB and everything seemed to be fine.

Thanks!

I have the same problem, did 3 fresh installations (with new iso downloaded), but nothing changed. Checked the HDs too with SMART. They are ok. It's a ubuntu 19.04 / win10 dual boot installation.  Ryzen 7 1700, msi motherboard, 16 GB RAM.
With Ubuntu 18.10 never had this problem.

---

### Post by Keilan on 2019-05-05
Just an update in case anyone finds this - I installed Ubuntu 18.04 which initially had a lot of trouble with finding a graphics driver. I was able to install it using the nvidia PPA. After that was working, I updated to Ubuntu 18.10, at which point this exact same problem started up again. It seems like it might be related to my graphics driver and using such a new GPU but that's just a hunch. No real solution except for sticking with 18.04.

---

### Post by ya-paulle on 2019-05-06
@keilan, I don't believe the issue has something to do with using such a new gpu. My gpu is older (nvidia gtx960) and I have the same problem.

---

### Post by ya-paulle on 2019-05-06
I otherwise made a fresh installation and i didn't check the use of proprietary software. So no nvidia drivers were installed, instead nouveau driver is installed. Now everything runs fine. The nvidia drivers caused the issue.

---

