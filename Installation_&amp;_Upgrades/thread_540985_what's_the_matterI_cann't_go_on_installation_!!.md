---
title: "what's the matter?I cann't go on installation !!"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by nanture on 2007-09-02
when i click on the install icon, my monitor looks like that pic showed below
[IMG]http://i52.photobucket.com/albums/g28/nanture/1.jpg[/IMG]

PS: I have installed XP
what's wrong? How can deal with it?

---

### Post by Pumalite on 2007-09-02
Bad CD or incompatible hardware. Post your specs. Did you do md5sum on your iso?

---

### Post by PatrickE on 2007-09-02
I'm maybe guessing wrong, but seems that Ubuntu tells you anyway what's wrong and how to deal with it. If I interpret the message on your screenshot right, your BIOS version is too old so you have to activate ACPI "manually" by giving Ubuntu the "acpi=force" argument in the bootup menu.

So when your Ubuntu cd is about too boot, press Escape to enter the boot menu. There select the kernel you want to boot and press "e" to edit the command line by adding

```
 acpi=force
```

Maybe that's the reason. If it doesn't help, then maybe run a memtest before booting up the cd. Or check the cd itself.

Good luck
Patrick

---

### Post by nanture on 2007-09-02
let me try, thanks first

---

### Post by Midwest-Linux on 2007-09-02
As far as the ACPI "problem" it isn't limited to just Ubuntu. All it means is that you have to shut down the computer manually after shutting down Ubuntu. It happens on older computers with older motherboards. 

 If you are trying to a partition, I belive it would be better to use the text installer...also called "ALTERNATE" installer. it will install around your XP. When burning a ISO use the lowest speed you can and use the best CD you can find like a Tayo Yuden. I have Windows 2000 and Ubuntu 7.04 on one machine. 

 Do you have enough hard drive space left to do a partition? If you are trying to a install from a Live install CD that may be the problem too. As a live CD install will require 256 MB or better on its own. So that means even if you have 256 MB, that would not be enough as the system and the video on its own will take away from the 256 MB. The ALTERNATE text based installer will solve that problem and save you a lot of time and  will guide your installation, it recognizes installed operating systems and will install around it...and it asks you as you go along.

---

### Post by Pumalite on 2007-09-02
I believe the same. That's why I asked for specs.

---

### Post by nanture on 2007-09-02
My notebook was manufactured in 2002&#65292;maybe it is too old

---

### Post by Pumalite on 2007-09-02
We need memory and graphics at least to advise you.
My guess is Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

