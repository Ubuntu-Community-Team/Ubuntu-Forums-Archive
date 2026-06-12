---
title: "install on old windows 98se computer"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by BooTooK on 2007-01-09
Before I finally decided to install Ubuntu on my old probmatic Windows 98se computer I thought I'd try reinstalling Windows 98SE just to see if the problem would be solved. The procedure of reformatting didn't work and now the computer is stuck on the C prompt and no commands work. Commands from the floppy didn't work either. It wouldn't boot from the floppy. The Ubuntu CD is in the D drive. It isn't reconized. Both lights next to the Off/On swith are steady green. Keyboard and mouse are working. It has been a long day:) Can anyone help? Thanks for reading.

---

### Post by meng on 2007-01-09
Sounds like a real lemon you have there :p
Check:
1. CD-ROM drive is listed in BIOS as the first boot-up device.
2. CD is burned correctly (possible problems: a) copying the iso file to CD rather than creating a filesystem on the CD using the ISO, b) corrupted download - use md5sum to check, c) burning at high speed.

[www.psychocats.net/ubuntu/iso](www.psychocats.net/ubuntu/iso)

---

### Post by Josey on 2007-01-09
You need to enter bios and "boot from cd-rom" needs to be an option I believe.  Usually you get into bios with the 'delete' 'F1' or "F2' keys right away.

---

### Post by BooTooK on 2007-01-09
That's another problem I forgot to mention. I can't get into the BIOS. When hitting F2, it says "keyboard error" and then "F1 Boot". Hitting F8 brings up the standard normal,safe mode etc. choices but still goes to the C prompt. Trying the Delete key does nothing either.

---

### Post by meng on 2007-01-09
Different BIOS have different keys - esc, f1-f12, del are some options.

---

### Post by BooTooK on 2007-01-09
None of the keys work. Is there anything physical I can do like removing the hard drive and then re-install it?

---

### Post by meng on 2007-01-09
I guess you could. Is it worth your while? Sounds as if this is going to be very tricky!

---

### Post by BooTooK on 2007-01-09
It's like a dog with a bone now! It will keep me busy for awhile but I'll be learning at the same time.

---

### Post by meng on 2007-01-09
> **BooTooK said:**
> None of the keys work. Is there anything physical I can do like removing the hard drive and then re-install it?
If you're determined, then this might work. Could require a LOT of post-install configuration.

---

### Post by mickeyf on 2007-01-09
Simply disconnecting and reconnecting the existing hard drive won't help, since it won't in any way change the boot record, etc, on that hard drive.  You should be able to get into the bios even if there is no operating system of any sort installed, or even no hard drive. Temporarily installing a hard drive with a known bootable operating system on it, setting the original drive to be a slave, then formatting it, is a viable option, but ultimately, you need to be able to set the bios so that the machine will boot from the floppy, CD, or try various devices in some order. If you can't do this everything else you do may be futile.

I would suggest holding down the delete key while you power the PC up, and keep it down until either the bios setup screen comes up or windows shows a prompt. If you get any message that is clearly from Windows, then you have already gotten past the point of being able to access the bios. Either the delete key is not the right one, or the keyboard is flakey, or there are deeper hardware problems (time to pitch this PC!). I believe I recall some PCs (Compaqs?) many years ago that required something like 'control-enter' to access the bios.

If you get a Windows message, but the the PC halts at the C prompt, I would say that Windows itself is broken. It may be running at the DOS level, but not able to bring up the GUI. Try typing in some DOS command ('DIR') and see if it is alive.  In this case you may be able to reformat the HD from a floppy, but you still might need to boot from a floppy for it to allow you to do that - back to the bios issue.

Good luck.

mickeyf

---

### Post by djheadley on 2007-01-09
Just a thought, but because of where my cpu sits I sometimes inadvertantly dislodge the mouse or keyboard cables.  It usually drives me nuts until I take a deep breath and start checking cable connections.  If cables are not the problem then I'd get the UBCD (Ultimate Boot CD) and check the system.

---

### Post by Papillonrus on 2007-01-29
Remove the cmos battery or use the jumper to clear the cmos to default,  There also might be a security password jumper depending on system.

---

### Post by digitalrao on 2007-08-19
Same problem with my Dell XPS dimension T500 with Win98SE ( orginal install) IE is so buggy. F1,F2 or delete won't allow me into BIOS just only Safe mode

---

