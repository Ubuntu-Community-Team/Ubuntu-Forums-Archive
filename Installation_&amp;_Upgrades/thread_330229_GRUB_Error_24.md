---
title: "GRUB Error 24"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by falsedust on 2007-01-02
I was just on the phone to my sister and she was telling me her computer (6.06 LTS 32-bit) is doing strange things and now she can't boot. While GRUB is booting she gets the error 24 message. From a GRUB error message website it tells me this "Cannot boot without kernel loaded".
This is strange because I was running and testing her computer for a week and had no probs what so ever. It is a new clean install of 6.06 LTS so no dual booting or anything.
Any suggestions?

---

### Post by goodfella on 2007-01-02
You might want to post your sisters menu.lst file to help solve this problem.  It is located in the /boot/grub directory.

---

### Post by falsedust on 2007-01-03
Yeah I thought of that, but as she can't boot up her Ubuntu she can't go look at it. If she reboots her computer and lets it go though it's normal processes when GRUB starts it gets to stage 1.5 then spits out the error message 24, according to the grub manual this is what error 24 corresponds to -
24 : Attempt to access block outside partition.
 This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt file system on the disk or a bug in the code handling it in GRUB (it's a great debugging tool). 

So does this mean that her hard drive has a problem or GRUB has a problem?
If you boot from the live CD how do you mount the hard drive so you can check it's grub menu.lst.
Also how do you check the hard drive for errors under the live CD?

---

### Post by falsedust on 2007-01-17
Anyway it ended up being that my sister's HD was faulty so I swapped it for an other one and it works fines now.
I had so much trouble trying to reinstall 6.06 and after checking something in the BIOS I noticed that the HD comes and goes meaning that for some reason it will show up on one boot but not the next.

So at least now I know what the implications of the GRUB error 24 are.

---

