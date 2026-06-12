---
title: "Problem detecting CD on Ubuntu Live"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by pcbodger on 2006-12-13
Hi

I got back an old PC that had been on long term loan to a friend who has not got an XP laptop. It is a 10 (?) year old Mitsubishi Apricot P200 (blimey, I hear you say) with a 1G HD and less RAM than my watch. It is definitely the AK47 of the PC world, old, ugly, outdated but d*mn robust and effective! I got it back as my friend now has a laptop.

I want to use it as my "under the telly" music / video PC, which it should handle with Ubuntu on.

I've set the BIOS startup sequence to FD, CD, HD but when I pop in the Breezy CD and reboot, it totally ignores the CD and goes straight to Windows 95. Grr!

I can see the CD and the files on it once in Windows.

I need help!

Q: What am I likely to be missing / doing wrong / doing stupid?
Q: Is there another way to force a Breezy install without going through the Live CD detect?
Q: Is it just too old?

TIA

pcb

---

### Post by taurus on 2006-12-13
Do you see a bunch of files and directories/folders on the CD when you view it in Windows?  See if you can boot the same CD on another machine?

---

### Post by pcbodger on 2006-12-13
> **taurus said:**
> Do you see a bunch of files and directories/folders on the CD when you view it in Windows?  See if you can boot the same CD on another machine?

Sure can - that is what is doing my head in. I can see the contents of the CD perfectly in Windows explorer once WIN 95 loads up. It just won't auto detect the CD drive on boot up, even though the BIOS sequence is set to FD, CD, HD.

---

### Post by pcbodger on 2006-12-14
Had a thought - doesn't Linux provide the ability to boot and install the CD via FD?

Does anyone know if Ubuntu provides this?

---

### Post by taurus on 2006-12-14
Do you have another computer that you can test out to see if that CD is bootable?  If you can boot from that CD with another machine, then it means your old machine is having a problem booting the CD...

---

### Post by pcbodger on 2006-12-14
Yup - tried on two other boxes. Wil try again to be sure :)

It must be something to do with how the old machine's BIOS treats a non Windows bootable CD.

---

### Post by Sef on 2006-12-14
> I've set the BIOS startup sequence to FD, CD, HD

Have you tried changing the BIOS start up sequence to CD, FD, HD to see if that works?

---

