---
title: "Help with prepare partition is blank"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by stepbystep on 2008-09-30
Hi there,
New to ubuntu and love it. My problem is, when it comes to prepare partition this shows up blank.

I don't have any other operating system on my hardrive, just want unbuntu.

I use sata is that means anything. Compaq presario sr1520an.

can anyone help to correct this.

I see the install on desktop and can even use the internet, but I need to figure out what's going on and why I get blank:o):confused:

---

### Post by davidryder on 2008-09-30
I don't fully understand your query. What are you using to prepare your partitions?

---

### Post by stepbystep on 2008-09-30
Nothing I think. I just put the disk in the and it runs and installs. I don't know if I am suppose to load something else in?

Really new to ubuntu, and have some knowledge of computers

---

### Post by stepbystep on 2008-09-30
How do you prepare a partition?

---

### Post by stepbystep on 2008-09-30
Cd is fine. Another friend just used it on there computer. Ubuntu 7.04

---

### Post by Victormd on 2008-09-30
I'm not sure I understand what's going on, but this is what I think is happening:

You're using 7.04 (may I suggest downloading and installing the latest version instead, Ubuntu 8.04). This means that when you insert the CD and boot, you're in the Live CD mode (which doesn't mean that it's installed). You need to click the Install Ubuntu icon on your desktop. Then the actual install will begin. You'll be given the opportunity to setup your HD during the install...

Let me know if I'm way off base or not... :)

---

### Post by stepbystep on 2008-09-30
cool, I will try that. Thanks. I read another blog and someone said something about bios and sata, and I know I have a sata cable. I will download the new version and try.

---

### Post by Victormd on 2008-09-30
SATA (Serial ATA) is simply a communication protocol for the HD that allows higher speed transfer than the traditional ATA (Advanced Technology Attachment) or PATA (Parallel ATA)... you don't need to worry about that, it simply means that you have a faster HD... :)

---

### Post by mikewhatever on 2008-09-30
It looks like Feisty couldn't detect any HDDs, Which explains why the partitioning screen was blank. I'd also recommend trying Hardy. Feisty is reaching its end of life on Oct 19, and hopefully, Hardy does better.

---

### Post by lemming465 on 2008-09-30
> **stepbystep said:**
> ,
... when it comes to prepare partition this shows up blank.
If I interpret your situation correctly, you are running a live CD, boot Linux, click on the install icon, step through some dialogs, get to the disk partitioning step, and don't see any disks.

This is typically because you have a version of Linux too old to support your SATA disk controller chipset.  A newer version might do better.  In the meantime you'd half to limp along using the live CD, perhaps supplemented by files stored on a USB drive or SD memory card.

---

### Post by stepbystep on 2008-09-30
cheers

---

### Post by stepbystep on 2008-10-01
Excellent, up and running. Had to download nero for the iso image thingy when I downloaded the latest version. Thanks.

---

