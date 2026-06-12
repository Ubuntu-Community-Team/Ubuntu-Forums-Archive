---
title: "Dual boot problem/question"
date: 2017-02-03
forum: Installation &amp; Upgrades
---

### Post by ra7411 on 2017-02-03
I had a 500gb HD that had Ub14.04 installed on it, using the whole HD; I did not create a separate partition for Home on that install.

I decided to shift an oem win8.1 install to it (hoping to get a dual boot situation) which had been on a different HD.

I decreased the Ub14.04 by 100 gbs for the Win8.1 install - that went fine, and I verified that I could still bootup the Ub14.04.

I installed the win8.1 to the 100gb partition - that went ok, it boots up fine.

However, when I boot the computer up, it goes right into the win8.1 partition without giving me a choice of Ub or win (I was hoping I might stumble into a viable dual boot choice).

So, is there a method to keep the existing Ub14.04 install and create a dual boot choice on startup, or do I have to do a new Ub install, or what?

Thanks

---

### Post by oldfred on 2017-02-03
Are both UEFI or both BIOS installs?

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

With BIOS Windows normally puts its boot loader in the MBR. You just need to reinstall grub to MBR.
With UEFI Windows makes it first in boot order. You may just need to change order, or one time boot from UEFI boot menu, often f10 or f12.
But with UEFI some brands make it a bit more difficult.
What brand/model system?

---

### Post by ra7411 on 2017-02-03
> **oldfred said:**
> Are both UEFI or both BIOS installs?


BIOS.


May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)


Maybe easier to just do a UB16.04 install to replace the Ub14.04. Will that guide me into a dual boot situation?


With BIOS Windows normally puts its boot loader in the MBR. You just need to reinstall grub to MBR.
With UEFI Windows makes it first in boot order. You may just need to change order, or one time boot from UEFI boot menu, often f10 or f12.
But with UEFI some brands make it a bit more difficult.
What brand/model system?


It's a desktop, mobo =  Asus M5A78L-M LX+  .

---

### Post by oldfred on 2017-02-03
If BIOS then just reinstall grub to MBR.

 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

