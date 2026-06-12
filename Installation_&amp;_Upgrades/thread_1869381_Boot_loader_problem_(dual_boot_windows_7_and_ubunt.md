---
title: "Boot loader problem (dual boot windows 7 and ubuntu)"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by yliu90 on 2011-10-25
I recently upgraded to Ubuntu 11.10, and in the process, it seemed something with the boot loading was messed up (it went automatically to Ubuntu and never even showed the selection screen that I had set up to let me choose between Windows 7 and Ubuntu).

I installed Grub Customizer in Ubuntu and changed the settings so that I set Windows 7 boot loader as default and then set the time-out to 0. However, this caused the problem that that Windows 7 bootloader comes up (letting me choose between windows 7 and Ubuntu), but when I choose Ubuntu, it just loops back to the Windows 7 bootloader again. In effect, I can not actually go to my Ubuntu installation anymore.

Is there a way to reset the default for Grub2 so that I can access ubuntu? Furthermore, can I get it so that I can choose Ubuntu or Windows 7 on the Windows bootloader (only have the Windows bootloader come up and not the Grub2 boot loading screen?)

Thanks!

---

### Post by critin on 2011-10-25
Install and run this on a live 11.10 CD or flash; (since you can't get to ubuntu)  it always worked for me.  Boot-Repair

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Oh, and give customizer more time to let you choose.  O seconds lets it do the first choice only.  Give 5 or 10 seconds--you can click enter without waiting.

*<<I installed Grub Customizer in Ubuntu and changed the settings so that I set Windows 7 boot loader as default*>>

I suggest letting the customizer, and now Boot-Repair,  put boot loader where it wants to.  I think this is the problem. I may be wrong.
You can make Windows default in the customizer--it has the option.

---

### Post by aliboy on 2011-10-26
Thanks!

---

