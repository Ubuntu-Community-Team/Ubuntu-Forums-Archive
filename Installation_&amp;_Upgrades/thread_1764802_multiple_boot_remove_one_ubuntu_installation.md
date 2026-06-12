---
title: "multiple boot: remove one ubuntu installation"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by cremersstijn on 2011-05-22
I have currently a triple boot with windows, ubuntu 11.4 32bit and ubunt 11.4 64bit. 

I want to remove the ubuntu 32 bit installation. How can i remove this and be sure that the other system keep working?

Widows was default installad on my laptop, then i installed ubuntu 10.4 32 bit and upgraded it to 11.4 and now i have installed ubuntu 11.4 64 bit.

Thanks!

---

### Post by cremersstijn on 2011-06-02
Anybody any suggestions?

---

### Post by mörgæs on 2011-06-02
If you boot a live CD, you can run Gparted and delete the partition(s) where the 32 bit Ubuntu sits. 

After you have confirmed that everything works, you can expand the 64 bit partition into the free space.

---

### Post by YesWeCan on 2011-06-02
One thing you have to be careful about is which linux partition contains the active Grub files, if you are using Grub to boot. They will be in one of the two linux /boot directories. If Grub is using the ones in the OS partition that you delete then Grub won't be able to boot anything and you'll get a rescue prompt.

To make sure Grub uses the Grub files in the linux OS you are keeping, boot into that OS and run
sudo grub-install /dev/sdn (where n=drive where you want the Grub MBR.) and
sudo update-grub

---

