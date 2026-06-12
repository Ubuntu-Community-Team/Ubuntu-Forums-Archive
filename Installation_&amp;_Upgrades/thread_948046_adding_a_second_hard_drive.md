---
title: "adding a second hard drive"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by cowboyup8606 on 2008-10-14
i just re did my computer and put ubuntu on it and i wanna add a second hard drive and be able to use them both .. can i do this ?? if so how ?? can someone plz help me

---

### Post by Partyboi2 on 2008-10-14
Yes you can add another hard drive. Make sure that you have set the jumper(s) on the hard drive as slave before connecting it. Once you have connected it make sure that it is been shown in your bios. Then boot ubuntu and see if ubuntu mounts the hard drive if not then you will need to probably add it to your fstab file.

---

### Post by cowboyup8606 on 2008-10-14
how do i set it as slave ??

---

### Post by Partyboi2 on 2008-10-14
Have a look on the face of the hard drive for jumper setting information, different hard drives have different settings.
Are you trying to install a sata drive or a ide one?

---

### Post by cowboyup8606 on 2008-10-14
sata its just a little 160 giger

---

### Post by Partyboi2 on 2008-10-14
I haven't connected a sata drive before, so I don't think I will be much use, maybe someone else will be able to help you.

---

### Post by cowboyup8606 on 2008-10-14
alright well ty man :) im goin to try to tinker with it tomorrow and if i cant figure it out im just goin to leave it and have just the one HD for now

---

### Post by alphaniner on 2008-10-17
SATA is a piece of cake, no jumpers required.  In the BIOS, make sure your SATA controller is enabled.  Make sure your SATA controller is set to 'Native' or 'IDE' mode or some such, not RAID (check your mobo docs).  Finally, make sure the HDD you were originally booting from is in the boot order, not your new drive.

---

