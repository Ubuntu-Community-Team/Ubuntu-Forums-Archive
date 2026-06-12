---
title: "Ghosted Ubuntu constantly reboot"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by sagouain on 2012-04-23
Hello,

I have to deploy several Ubuntu 11.10 clients and i'm using Acronis True Image to get a .tib image.

It worked fine on every signle OS I used ( Win XP, Ubuntu 10, Win 7 etc... ).

But on 11.10, something is preventing the ghosted computer to boot, and it cycles through the bios screen.

I checked the hardware with the original HDD, and it is booting without a problem.

Is there some sort "execution prevention" enabled on the basic installtion of Ubuntu 11 that checks the S/N of the HDD?

Kind Regards,
Sagouain.

---

### Post by Aldrak on 2012-04-25
I have the same issue actually and I can’t find the solution…

---

### Post by zeljkojagust on 2012-04-25
Do you get GRUB menu at least, or not even that?

---

### Post by sagouain on 2012-04-25
No, the BIOS screen appears every 10 seconds, and it won't stop restarting.

I tried with the original drive and it works perfectly.

I used a Live CD to check if the ghosting process was sucessfull, and the filesystem was correctly cloned.

I tried to repair the boot with this live CD [http://forum.ubuntu-fr.org/viewtopic.php?pid=5745281#p5745281](http://forum.ubuntu-fr.org/viewtopic.php?pid=5745281#p5745281) without sucess...

---

### Post by sagouain on 2012-04-25
Anyway my goal is to use thoses internet kiosks with a single OS.

---

### Post by sagouain on 2012-04-25
I found a workaround, but its kinda long and boring.

I installed a fresh Ubuntu, then i restored all the partitions excepted the MBR...

I must have missed something with the Boot-repair CD....

---

### Post by YannBuntu on 2012-04-25
@Sagouin: salut, next time you use Boot-Repair, please indicate the BootInfo URL that appears, this will help us to help you ;)

---

