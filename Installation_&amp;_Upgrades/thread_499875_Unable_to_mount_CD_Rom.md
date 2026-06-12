---
title: "Unable to mount CD Rom"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by Reneagde222 on 2007-07-13
In the Ubuntu Feisty Fawn installation, I fail the step "Mount CD Rom"


Strangely enough, in VMWare, I pass this step...

Please help, I am new to Linux and have no idea what's wrong.

---

### Post by Reneagde222 on 2007-07-13
Bump :(

---

### Post by wpshooter on 2007-07-13
Check to see if your CD-Rom drive is jumped as master.

---

### Post by Reneagde222 on 2007-07-15
My drive is jumped as master. I am using CD-R and I have tried DVD-R and DVD-RW.

Same error every time 

Please help.

---

### Post by Reneagde222 on 2007-07-15
> **Reneagde222 said:**
> My drive is jumped as master. I am using CD-R and I have tried DVD-R and DVD-RW.

Same error every time 

Please help.


Bump


:popcorn:

---

### Post by Pumalite on 2007-07-15
Do you have something like this in your fstab?:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Layman's terms on 2007-07-15
Reneagde222: I have a similar problem with my CD-ROM drive (e.g. I get the "Unable to mount media" message as well).

I know that my drive still works because I'm able to access CD content on my XP partition.

After some research online, I came across a confirmed launchpad bug that mentions mounting problems with the 2.6.20 kernel. I can't speak specifically to your problem, but there's a good chance that you are suffering from a kernel bug like I am.

Here is the link to the bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119)

Maybe this situation doesn't apply to you, but I wanted to let you know that it is a possibility.

---

### Post by Reneagde222 on 2007-07-25
Actually, I haven't even got past installation yet. This error comes up in installation. I fail the step "Mount CDROM"

It gives no error other than that. I am clueless and have asked on several forums to no avail.

Please help!

---

### Post by Pumalite on 2007-07-25
There are some motherboards in which the only solution for Feisty is to go to BIOS>IDE Configuration>Advanced Support>Set it to 'Advanced Support for PATA+SATA'

---

### Post by Reneagde222 on 2007-07-27
Problem solved. Anyone watching this thread waiting for an answer, boot with the irqpoll option.

---

### Post by minhtrietle on 2007-08-01
it didn't work for me... 

SAD!!!!!

---

### Post by minhtrietle on 2007-08-02
I've tried so hard to work on this problem but this is what I end up with.

:confused::confused:

:mad::mad::mad:

I understand that I'm using FREE software, but I still hope that Ubuntu will do something about this supposed-to-work-out-of-the-box bug soon.

---

