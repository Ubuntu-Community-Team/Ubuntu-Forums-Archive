---
title: "removing a preinstalled but unconfigured windows"
date: 2006-05-20
forum: Installation &amp; Upgrades
---

### Post by prismatic7 on 2006-05-20
i hope this is a stupid question. i really do.

i helped a friend of mine purchase a computer a couple of days ago - sternly informing the bloke at the computer shop that an operating system was not required and my friend would be doing it himself. we picked up the PC yesterday,  and fired it up with his windowsXP pro install cd in the drive - we're going to dual-boot with Ubuntu.

The PC ignored the install disk, claiming the system could not boot from CD (error 4), and went into an unconfigured WindowsXP Home - asking for the install key. Which we don't have. The XP Pro key won't work. ](*,) 

The PC won't boot to anything except the XP installer, so clearly a flag is set somewhere to cause that. 

The HDD is SATA, so I don't actually have another PC that can format it (after loading it as a secondary hard drive...

Any ideas?

---

### Post by Gannin on 2006-05-20
You could try getting the latest version of the Dapper Drake live CD, or a copy of the gParted live CD, and use the partitioning tools in either to delete and then recreate the main partition on the drive.

---

### Post by aysiu on 2006-05-20
So... is there any way to get into the BIOS?

Pressing one of these keys during start-up, maybe...?

Delete
F1
F2
F12
Escape

---

### Post by Gannin on 2006-05-20
If I understand correctly, I think his BIOS is already set to boot from a CD, as it specifically gave an error message about not being able to boot from his Windows CD.

---

### Post by prismatic7 on 2006-05-20
[quote=Gannin]If I understand correctly, I think his BIOS is already set to boot from a CD, as it specifically gave an error message about not being able to boot from his Windows CD.[/quote]

That's correct. Even setting the BIOS not to boot from HDD at all ends up in the Windows setup.

Could the Windows CD be flaking out because of the SATA drive? It's SP2, though.

[quote=Gannin]You could try getting the latest version of the Dapper Drake live CD, or a copy of the gParted live CD, and use the partitioning tools in either to delete and then recreate the main partition on the drive.[/quote]

I didn't try Dapper - my friend's a self-described computer nuffy, so i didn't think to bring a testing distro... I'll give it a shot tomorrow. 

Would booting from an external drive - a USB key or something - be an idea?

Any other suggestions gratefully recieved!

---

### Post by bigken on 2006-05-20
is the xp disc ok it could be damaged try another boot disc anything will do just to try it yes u can setup usb sticks to boot from ;) google it

---

### Post by Gannin on 2006-05-22
While it would be possible to boot from a USB flash drive or a USB hard drive, it would be more simple and straight-forward to try booting from another bootable CD.

---

