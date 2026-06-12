---
title: "Botched Windows boot after installing Ubuntu"
date: 2018-03-29
forum: Installation &amp; Upgrades
---

### Post by foxy123 on 2018-03-29
I've installed Ubuntu on my new ASUS laptop and it seemed to botch my Windows boot. I have Windows entries in the GRUB menu but they don't work. It goes into trying to repair Windows and then gives me options to repair the start-up, do the recovery, bi=ut nothing works. I can see all Windows partitions in GParted (see the image attached) but cannot carry out the recovery. Unfortunately I did not make a recovery image before installing Ubuntu (silly me, I know) but I hope if the recovery partition is available I still can do something.

 [ATTACH=CONFIG]279126[/ATTACH]

Could anyone help, please?

---

### Post by yancek on 2018-03-29
It appears you have overwritten your windows install.  You have the standard EFI partition but the only windows partition is only 800MB.  The home partition for Ubuntu takes up most of the drive.  I doubt you will be able to use a recovery cd even if you had one.  Probably need to use an install disk if you have one or you may need to contact the manufacturer or microsoft.

---

### Post by foxy123 on 2018-03-29
> **yancek said:**
> It appears you have overwritten your windows install.  You have the standard EFI partition but the only windows partition is only 800MB.  The home partition for Ubuntu takes up most of the drive.  I doubt you will be able to use a recovery cd even if you had one.  Probably need to use an install disk if you have one or you may need to contact the manufacturer or microsoft.

Yeah, I have realised in now :(

---

### Post by sdansmith on 2018-03-29
I did that once a few years ago, you have my sympathy.

---

### Post by foxy123 on 2018-04-01
I have downloaded the Win10 ISO from Microsoft and reinstalled both Windows and Ubuntu. Seems fine now.

---

