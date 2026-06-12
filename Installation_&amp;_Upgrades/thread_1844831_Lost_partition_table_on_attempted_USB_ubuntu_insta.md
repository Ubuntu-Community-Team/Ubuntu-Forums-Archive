---
title: "Lost partition table on attempted USB ubuntu install. What table do I use?"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by Swashy on 2011-09-15
I've searched with about 10 different variations of this question on these forums and google but apparently this isn't an issue for anyone but me.

So gparted gives me these options for the partition tables:
> msdos
aix
amiga
bsd
dvh
gpt
mac
pc98
sun
loop

So my question is whether anyone has a resource explaining partition tables (wikipedia isn't much help), and which one is best to use for ubuntu/linux/windows installations, or if there are different best ones for each.

And of course I greatly apopreciate any help you cool dudes can give me.

---

### Post by haqking on 2011-09-15
> **Swashy said:**
> I've searched with about 10 different variations of this question on these forums and google but apparently this isn't an issue for anyone but me.

So gparted gives me these options for the partition tables:


So my question is whether anyone has a resource explaining partition tables (wikipedia isn't much help), and which one is best to use for ubuntu/linux/windows installations, or if there are different best ones for each.

And of course I greatly apopreciate any help you cool dudes can give me.


If you are dual booting with windows choose MSDOS (or MBR as it is also known) if only Linux choose MSDOS or GPT (which is known as GUID) MBR limit is 2TB so might be better to go for GUID depending on your HDD sizes etc

---

### Post by Swashy on 2011-09-15
> **haqking said:**
> If you are daul booting with windows choose MSDOS (or MBR as it is also known) if only Linux choose MSDOS or GPT (which is known as GUID) MBR limit is 2TB so might be better to go for GUID depending on your HDD sizes etc

Sorry I meant to say that its on the usb drive itself. I'm trying to install lubuntu onto it with unebootin. What do I use for the usb drive?

Thanks for the response!

edit: the lost partition table is on the usb drive.

---

### Post by haqking on 2011-09-15
**msdos** (windows and linux or windows only it is also known as MBR)
**aix** (IBM proprietary UNIX system)
**amiga** (commodore)
**bsd** (BSD is also a UNIX variant)
**dvh** (For MIPS based architectures i believe)
**gpt** (GUID helps extend beyond 2TB limit of MSDOS and can be used by Linux)
**mac** (Apple)
**pc98** (old MS and Intel thing i thnk)
**sun** (as in sun microsystems such as Solaris)
**loop** (as in looback also i believe)

---

### Post by haqking on 2011-09-15
> **Swashy said:**
> Sorry I meant to say that its on the usb drive itself. I'm trying to install lubuntu onto it with unebootin. What do I use for the usb drive?

Thanks for the response!


MSDOS, if using persistance then there will be a 4GB limit due to FAT32 limitations, but that can be worked around if needed

---

### Post by Swashy on 2011-09-15
Thanks!!

---

### Post by haqking on 2011-09-15
> **Swashy said:**
> Thanks!!

no worries, you are welcome.  Please mark the thread as solved using thread tools if you feel your question was answered.

Cheers

---

