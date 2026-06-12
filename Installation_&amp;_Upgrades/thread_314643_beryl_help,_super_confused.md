---
title: "beryl help, super confused"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by madhatter434343 on 2006-12-07
Im running edgy and ive read a few other threads and goggled it but i cant find a good guide to install beryl, the wiki for their website says"As of october 2006, AIGLX should work out of the box in edgy, provided your graphics card supports it." but i have no idea what that means, i just installed ubuntu for the first time this week so i am fairly new to it.

---

### Post by divague on 2006-12-07
Which graphic card do you have?

---

### Post by madhatter434343 on 2006-12-07
i don't know how to check

---

### Post by divague on 2006-12-07
open a terminal application->accesories->termianl
and type

more /etc/X11/xorg.conf

and look into the section "device"

---

### Post by madhatter434343 on 2006-12-07
it gives me a message saying permission denied and "sudo /etc/X11/xorg.conf" plus my password tells me "command not found"

---

### Post by gtsmith on 2006-12-07
remember to type in teh "more" command between sudo and the path: "sudo more /etc/X11/xorg.conf"

---

### Post by gtsmith on 2006-12-07
> **madhatter434343 said:**
> i don't know how to check

Just as a heads up...you ought to know more about your PC before diving into the Linux world. I suggest a full inventory of all your hardware, version numbers, etc. Going in blind as you are will most likely lead to a very frustrating linux experience.

---

### Post by madhatter434343 on 2006-12-07
i have "Intel Corporation 82915G/GV/910GL Express Chipset Famil
y Graphics Controller"

---

### Post by gtsmith on 2006-12-07
> **madhatter434343 said:**
> i have "Intel Corporation 82915G/GV/910GL Express Chipset Famil
y Graphics Controller"
 Now do a search on this forum for beryl Intel 915Gm and you should find the guide you're looking for.

---

### Post by gtsmith on 2006-12-07
Good place to start:
[http://wiki.beryl-project.org/wiki/Install/Ubuntu]("http://wiki.beryl-project.org/wiki/Install/Ubuntu")

---

### Post by madhatter434343 on 2006-12-07
im trying to do what one of the guides is saying

---

### Post by madhatter434343 on 2006-12-07
which do i click on from their? "aiglx"?

---

### Post by gtsmith on 2006-12-07
> **madhatter434343 said:**
> im trying to do what one of the guides is saying

The Intel card should be pretty easy to set up, I did it on my Toshiba laptop. Be glad you dont have the ATI card, that one is a bear to get configured. Try the Beryl forums at [http://forum.beryl-project.org/]("http://forum.beryl-project.org/")
they have some really good howtos. For now I wouldn't worry about whether you run XGL or AIXGL...just find a howto guide for the Intel card.

---

### Post by gtsmith on 2006-12-07
Here ya go...it has a section about the Intel card:
[https://help.ubuntu.com/community/BerylOnEdgy]("https://help.ubuntu.com/community/BerylOnEdgy")

---

### Post by madhatter434343 on 2006-12-07
thank you ill try it ight now

---

### Post by madhatter434343 on 2006-12-07
when i try to run "/etc/apt/sources.list" in the terminal like it says in the first step of [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) it tells me that command not found

---

