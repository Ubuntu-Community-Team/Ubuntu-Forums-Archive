---
title: "I can't shutdown normaly my computer after installing ubuntu 14.04"
date: 2016-04-08
forum: Installation &amp; Upgrades
---

### Post by law2016 on 2016-04-08
Hello,
After installing Ubuntu 14.04 in dual boot with Windows 10 pro on my computer Thinkpad X1 Carbon Yoga , it is normally impossible to shutdown or to hibernate the computer.
I tried most of the solutions on the French forum ( intel_pstate no_hwp = ... ) ; nothning work.
Im new user of ubuntu and french. sorry for my english

Could you please help me ?

Thank you

---

### Post by Bucky Ball on 2016-04-08
Welcome. You might like to give us some details about what happens when you try to shutdown. You haven't given a lot for us to go on. 

To hibernate your /swap partition should be as large or larger than your installed RAM.

---

### Post by law2016 on 2016-04-08
/ = 30 Go
/swap = 16 Go
/boot = 3 Go
/home = 300 Go


I installed ubuntu in dual boot with windows 10.
To install this, i needed to put on grub "acpi=off" because in the first install, there is black screen and i saw that to resolve this, its to put on grub "acpi=off";
after i can install.
After i installed, all work  and i can't only not able to shutdow the computer. when i click of shutdown, the logo of ubuntu appear and nothing happen later..its look like block. I need to force by shutdow with the power button.
I cant hibernate because the computer still working even if i closed it and no click button appear to hybernate

---

### Post by Bucky Ball on 2016-04-08
Hmm. Well, rather than using the power button to shutdown, which isn't good for the hardware, when the screen locks, if you hit control+alt+F1 do you get to something that looks like a large terminal with a cursor? If you do, in there, type:

> sudo reboot -h now

... or swap 'reboot' for 'shutdown' if you want to shutdown. You may need to login to the CLI before typing this command.

That's all I can think of for the moment but have bumped your thread.

---

### Post by law2016 on 2016-04-10
Hello,

not working.
Still have the same problem.
who can help me shutdown normaly my computer please?

thank

---

### Post by law2016 on 2016-04-12
Help ...nobody to help resolve this problem please?
 I cant shutdown my computer and i tried all advices i received and the problem is still there.... :-(

---

