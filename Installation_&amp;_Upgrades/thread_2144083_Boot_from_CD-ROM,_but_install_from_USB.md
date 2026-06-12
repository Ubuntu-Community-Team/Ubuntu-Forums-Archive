---
title: "Boot from CD-ROM, but install from USB?"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by gdea73 on 2013-05-11
I intend to install Ubuntu 12.04.2 LTS Server on an old laptop, a Sony Vaio PCG-SR33K. This laptop has 64MB RAM and can only boot to its internal hard disk or a PCMCIA-attached CD-ROM drive. Said CD-ROM drive is impossible to use after booting to a live system, i.e. from within a live system it is unusable. (I have tried the kernel arguments ide2=0x180,0x360 and ide2=0x180,0x386, to no avail.)

Granted, I already know a basic solution, I just need assistance in formulating the procedure. I intend to boot to the Ubuntu Server CD with the attached CD-ROM drive, and then run the installer from a USB flash drive (or, rather, when the installer attempts to locate the CD-ROM drive, somehow point it manually to a mounted USB disk.)

In order to accomplish this, there are two things I must do, of which my understanding is limited:
[LIST=1]
[*]Copy the contents of the CD-ROM-based installation media to the USB flash drive.
[LIST]
[*]What I mean is I am not sure precisely which files to copy. I suppose I could write the ISO to the USB drive with the *dd *command?
[/LIST]

[*]Force the installer to use an arbitrary directory for its sources, rather than search for a CD-ROM drive.
[LIST]
[*]This is mainly where I would appreciate some assistance. I am familiar with the Ubuntu installer, but not necessarily how it works in a technical sense. I have tried to attach a USB CD-ROM drive with the installation media, but the installer still did not find that drive in its search. Must I install the entire operating system manually in order to accomplish this (and is that remotely practical / possible from a normal Server CD?)
[/LIST]
[/LIST]

Thanks in advance.
— gdea73

---

### Post by 2F4U on 2013-05-11
I don't know if the intended way works, but there are quite some alternatives available:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

But reading through your post I found that the machine has just 64 MB of RAM, which may not need the minimum requirements:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by grahammechanical on 2013-05-11
Is the CD drive faulty? Is the CD-Rom faulty? Or is the live session unusable because the machine has too low a specification. May be there is not enough RAM or the video adapter is not powerful enough or the CPU is not powerful enough or all three together? If this is so, then even if you get Ubuntu installed then performance will be of poor quality and disappointing.

Does the 12.04 server edition have a live session? Does it install using a GUI or just text mode?

Regards.

---

### Post by gdea73 on 2013-05-11
The specifications are definitely low, but it's the RAM that's the bottleneck. Using most text-based Linux live systems actually isn't intolerably slow, however. The CD-ROM itself and the drive both function correctly: I can verify the disk's integrity sucessfully.

Essentially, I know that this is a rather low-spec laptop, but the installation by all means should work as long as there is some way I can tell the installer to use, for example, /dev/sda1 to find the packages. Also I would need to copy the packages to /dev/sda1...

---

