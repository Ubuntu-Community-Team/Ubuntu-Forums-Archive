---
title: "Install win xp with existing ubuntu install"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by Ampsonic on 2007-07-05
Hello!

I've got ubuntu 7.04 running on my laptop, and unfortunatley need to put Win XP back on my machine. (Just got an iPhone and can't sync anything yet...)  I would like to dual boot but I know that windows installer will not play nice with grub. 



How do I create a partition for windows to use?

What do I need to do to ensure my ability to dual boot after the installation? 

Thanks,
Nick

---

### Post by Vajra Vrtti on 2007-07-05
Do you still have the XP partition available?

---

### Post by Ampsonic on 2007-07-06
I did not, but I booted into the ubuntu live cd and created a partion for xp. I now have xp installed fine, I just don't know how to set up grub again. (presently the laptop boots straight into xp)

---

### Post by Vajra Vrtti on 2007-07-06
Just follow [these instructions]("http://ubuntuforums.org/showthread.php?t=224351") and you will have grub back.

---

### Post by Ampsonic on 2007-07-07
Thanks, Grub is back and working, but boots straight to ubuntu. How do I add the option at boot for ubuntu OR windows?

Thanks,
Nick

---

### Post by logos34 on 2007-07-07
**gksudo gedit /boot/grub/menu.lst**

Just use the example Windows entry near the top of menu.lst and paste it to the bottom, changing the 'root' line to point to your windows partition

---

### Post by Ampsonic on 2007-07-07
How do I determine what partion my windows install is on?

---

### Post by Vajra Vrtti on 2007-07-07
Most probably it is (hd0,0). If not, find out in *System -> Administartion -> System Monitor*, in the*File Systems *tab, but note that the numbering there is +1 in relation to grub, that is, */dev/sda2* is (hd0,1) and not (hd0,2)!

---

