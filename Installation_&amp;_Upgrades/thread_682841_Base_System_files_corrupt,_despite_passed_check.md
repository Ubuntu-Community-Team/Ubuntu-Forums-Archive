---
title: "Base System files corrupt, despite passed check"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by Vudusu on 2008-01-30
I'm using the alternative text-based installer (graphic install kicked out I/O errors) on my laptop. I ran a CD integrity check on my desktop system, and it passed. The alternative CD got me past the I/O errors, through hardware detection and partitioning, but now every file in the base system is kicking out > Debootstrap Warning, file:xxx was corrupt I can't even back out of the install.

History: the laptop presently has aborted installs of Windows and Ubuntu, so no working OS and probably lots of clutter. Could the hard drive clutter be the source of this problem?

All I can think to do now is a zero-fill format, for which I'll have to figure out who made my hard drive to get the right software. The only way I can think to do that is cracking open the laptop and hoping I can find it (the most I've done w/ a laptop is replacing the keyboard).

Is zero-fill likely to help? 
Is there any other reason for the corruption errors? 
Any ideas on getting the make of the hard drive short of brute force (remember, no OS)?

---

### Post by Vudusu on 2008-01-30
I managed to wipe the drive with PC Inspector EMAXX, but it was no help. The laptop will start the text-based installer, but still reports the system files as corrupt, both from installer and integrity check. The CD still passes integrity check on my desktop PC.

All I can think at this point is download another ISO and burn another disk (I'm collecting quite a stack) but I'm not optimistic.

---

### Post by Vudusu on 2008-01-30
I'm thinking now the issue is the DVD-R/W drive on the laptop, which has been reading disks inconsistently at boot (often takes half a dozen boots with the same settings before it reads the disk). If it's being similarly inconsistent reading the disk during integrity check and installation, could that be the problem? 

If so, might it be the drivers? Would I be able to put new drivers on a bootable disk?

I don't have another drive to swap out.

---

### Post by Partyboi2 on 2008-01-30
If you believe its the dvd drive causing the problem you could try installing via usb
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Vudusu on 2008-02-03
No, the machine won't boot from USB and the only flash device I have with enough memory is my phone, which I doubt would work even on a newer laptop. It's looking like I'll have to track down another drive to make this work, if the drive really is the problem.

---

