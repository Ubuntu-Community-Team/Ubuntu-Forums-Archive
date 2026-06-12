---
title: "Only mousepointer after login"
date: 2005-08-17
forum: Installation &amp; Upgrades
---

### Post by pawwen on 2005-08-17
Hello! I have a IBM Thinkpad 600X on witch i have installd Ubuntu 5.04. Everything installd without problems.

The problem is: After the graphical login there is only a black screen with only the mousepointer visable. I've tried the "Failsafe login-mode" but without sucess.

Can anyone help me or atleast give me a hint?

//Pawwen

---

### Post by heimo on 2005-08-17
We probably need some more information. Could you try to go to virtual console (hit ctrl+alt+F1), login, stop gdm (type: *sudo /etc/init.d/gdm stop*) and try to start X (type: *startx*). If that doesn't work, post any errors you get on screen. If you get the black screen, exit by hitting ctrl+alt+backspace. Make notes of the messages on screen. Scroll up with shift+Page Up. You can restart gdm with [i]sudo /etc/init.d/gdm start


[/i]

---

### Post by Thulemanden on 2005-09-12
Have you tried with different video drivers?

---

### Post by pawwen on 2005-09-21
I found out, after searching the forums that using the kernel option "irqpoll" could perhaps work. And it did! Everything works like wonder now! =)

---

### Post by burevestnik on 2005-09-29
How did you use this irqpoll option? I am very new to LINUX, and not really sure how to change options in the kernel...

Thanks a lot!

---

