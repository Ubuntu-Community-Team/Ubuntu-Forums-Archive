---
title: "Grub error 17 upon installing new HDD"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by mocka on 2011-02-14
I have just bought a new HDD and installed it in my Ubuntu server. The problem is that when I try to boot, I only receive the message "Grub error 17" and at that point the computer freezes.

In my troubleshooting I found that without the new drive, the computer starts and the hard drives are listed in BIOS as follows:
1. DVD-rom (ide) - Master
2. 80gb disk (with OS installed) (ide) - Master
3. 1tb disk (sata) - Master

In the new setup the disks are listed like this:
1. DVD-rom (ide) - Master
2. 80gb disk (with OS installed) (ide) - Slave
3. 1tb disk (sata) - Master
4. 2tb disk (sata) - Master

May this different listing in BIOS lead to the Grub error? What can I do to solve the problem?

---

### Post by presence1960 on 2011-02-14
You need to keep the 80 GB as #1 master- whether through IDE cables or BIOS. That is the disk that must boot first to boot your machine.

---

### Post by mocka on 2011-02-14
Thanks that did it. After playing around with the jumper settings for a while, I managed to make the IDE drive master - and voila, the server is yet again up and running.

---

### Post by presence1960 on 2011-02-14
> **mocka said:**
> Thanks that did it. After playing around with the jumper settings for a while, I managed to make the IDE drive master - and voila, the server is yet again up and running.

Glad you got it working, enjoy.

---

### Post by glene77is on 2011-02-14
> **presence1960 said:**
> You need to keep the 80 GB as #1 master- whether through IDE cables or BIOS. That is the disk that must boot first to boot your machine.

Presence:
Why is this a solution ? 
I mean, I know it will work, 
but WHY is this a solution ?
Did the OP forget to install an MBR pointing into a new HD ?

---

### Post by presence1960 on 2011-02-15
> **glene77is said:**
> Presence:
Why is this a solution ? 
I mean, I know it will work, 
but WHY is this a solution ?
Did the OP forget to install an MBR pointing into a new HD ?

The OS is on the old hard disk as well as GRUB which is on the MBR of the old disk. OP has a perfectly good MBR and OS on the IDE disk (80 GB)- no need to install GRUB to another MBR. However that could have worked also.

---

