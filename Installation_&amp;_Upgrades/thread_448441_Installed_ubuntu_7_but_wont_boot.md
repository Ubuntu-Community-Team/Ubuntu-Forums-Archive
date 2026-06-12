---
title: "Installed ubuntu 7 but wont boot"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by Sir P on 2007-05-19
Hi all,

Need some assistance here, if anyone can help it would be much apperciated.


I downloaded the latest ubuntu 7 release and installed it onto a hdd of mine, all went fine. Came to boot it up and frooze on the very first little onranage sqaure of the boot progress bar on the splash/loading screen. Rebooted few times, same thing. So I assumed my harddrive was damaged.

Installed on an entirely new harddrive, exactly the same thing. So this time went into the recovery mode from grub, it falls over on
> uniform cd-rom driver loaded
And some stuff about SCSI, but the scsi stuff was before that. I dont have scsi that im aware of? so i thought its odd. Anyway ...

so switched off, unplugged CD-ROM and rebooted. Still dies in same place. Went back into recovery off the grub menu, this time it dies on 
> attach scsi generic sg0 type0

Anyway assistance would be cool, cant wait to get my new unbuntu system going :)
Cheers all,

Sir P:D

---

### Post by lw5 on 2007-05-19
Does your failsave login work? If so, it might be helpful if you take a look at your logs (and perhaps post them here).

---

### Post by Sir P on 2007-05-19
hi

thanks for replying

by failsafe i assume you mean the 'recovery' option in grub?

as I said, that doesnt work but shows me where it fails :)

Or is there another failsafe i can type?

It dioes not get as far as 'login' i assume you mean boot option?

cheers again
Sir P

---

### Post by lw5 on 2007-05-20
I'm sorry. Yes, I meant what you already did.

Are you able to boot the live CD? Does that complete the boot proces? Otherwise it sounds fairly difficult to modify a system that wont boot.

Perhaps you could also look into grub and its supported boot options. Perhaps you can try turning everything off at boot, see if that works, and if so, turning things on one at the time to see what is causing the problem.
The boot line can be adjusted in Grub on the fly by pressing 'e' (I believe, it says so below the boot menu) when in the boot menu.

---

