---
title: "Ubuntu can not be installed on empty hard drive?"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by Basketball on 2008-05-13
Hi, I have server and desktop versions, I deleted my hard drive of Windows to install Ubuntu but the CD does not boot... why can I only install Ubuntu desktop from Windows???  Please give me a link to download and install Ubuntu on an empty HD thx.

---

### Post by Basketball on 2008-05-14
ttt

---

### Post by iaculallad on 2008-05-14
If those CD that you mention came from valid sources, surely, it will boot to continue with the installation.
Check your CMOS settings and set your first boot device to be your CD/DVD ROM.

---

### Post by Aearenda on 2008-05-14
One hour is a bit soon for a bump - this isn't a paid service. You might get more response if you tell us what you see.

When you say 'the CD does not boot' what happens? 

Common issues:
Not booting at all -> Operating System not found
Booting into Grub but no further
Failing into the boot with a busybox prompt

Have you done the CD integrity check?
Did you burn the CD slowly?
Maybe your computer needs a boot-time parameter for the kernel - especially if you have a mixed PATA/SATA system.

---

### Post by Basketball on 2008-05-14
Hi, well there is no OS and instead of booting from the CD the screen says something like "error loading os".  The win XP cd boots and the Ubuntu Desktop CD can be installed from the win XP desktop, I thought maybe there's another download I don't have...

I don't want a dual boot though, just Ubuntu!

---

### Post by Basketball on 2008-05-14
> **iaculallad said:**
> If those CD that you mention came from valid sources, surely, it will boot to continue with the installation.
Check your CMOS settings and set your first boot device to be your CD/DVD ROM.

I clicked that option but the CD isn't read, I'll re-download it since it's supposed to work thx. I thought that maybe Ubuntu is only a dual boot OS...

---

### Post by iaculallad on 2008-05-14
> **Basketball said:**
> I clicked that option but the CD isn't read, I'll re-download it since it's supposed to work thx. I thought that maybe Ubuntu is only a dual boot OS...

Ubuntu can be both a dual boot (if paired with any other OS) and a standalone OS.
Just be sure that after your successful download, check the ISO image for errors.

---

