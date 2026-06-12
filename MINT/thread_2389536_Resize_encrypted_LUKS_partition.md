---
title: "Resize encrypted LUKS partition"
date: 2018-04-18
forum: MINT
---

### Post by crizz2k on 2018-04-18
Hello community!

I would like to to decrease my encrypted Linux Mint partition to get space for a Windows partition (150 GB).

So far I followed this instruction "https://medium.com/@tbeach/resize-an-encrypted-partition-without-breaking-your-linux-system-6ef475619745", because it seemed easy to execute (I don't know any terminal commands!).
I managed to install Manjaro at my USB stick and followed the instructions.

[URL="https://i.imgur.com/FmqaKhQ.png"]
  [IMG]https://imgur.com/FmqaKhQl.png[/IMG]
[/URL]

The Problem is, that i still cannot decrease my partition.

GParted Screenshots:
[URL="https://i.imgur.com/eg0rQLO.png"]
  [IMG]https://imgur.com/eg0rQLOl.png[/IMG]
[/URL]

[URL="https://i.imgur.com/SyxEGP3.png"]
  [IMG]https://imgur.com/SyxEGP3l.png[/IMG]
[/URL]

File Manager Screenshot:
[URL="https://i.imgur.com/BdwpxcN.png"]
  [IMG]https://imgur.com/BdwpxcNl.png[/IMG]
[/URL]

Please can someone guide me through this complicated process.

I really appreciate it. Thank you!

---

### Post by howefield on 2018-04-18
Thread moved to the "MINT" forum.

---

### Post by yancek on 2018-04-18
Did you notice on the GParted screens the lock symbol to the left of the filesystem?  That means it is mounted and cannot be changed.  If you are using the Manjaro usb to do this, you will first need to unmount sda then the Extended partition sda2.  I don't use LVM so I'm not sure what commands you would use but they are definitely not the same as a standard partition.  You might be able to do this in GParted, not sure.

---

### Post by crizz2k on 2018-04-18
thx for the answer. Ok I tried to unmount it:

[url=https://i.imgur.com/Xj2lX2a.png]
  [img]https://imgur.com/Xj2lX2al.png[/img]
[/url]

Also I found the command: umount /run/media/manjaro/e696db63-f929-40f2-8bda-7a099b21119c/
Nothing happen

---

