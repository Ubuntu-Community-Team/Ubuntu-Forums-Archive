---
title: "Problem with starting linux after installing updates"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by Constantinus_Spin on 2015-07-16
Hello, after i installed my ubuntu updates, i switched off and then started my laptop, and although ubuntu was loaded, i had blank screen. What could be the problem?

---

### Post by howefield on 2015-07-16
With that description, one of a thousand things maybe :)

Can you get to a command prompt with Ctrl + Alt + F1 ?

---

### Post by Constantinus_Spin on 2015-07-16
Yes i can.

---

### Post by Constantinus_Spin on 2015-07-16
I tried to start ubuntu using previous ubuntu kernels (the latest is 3.13.0-57-generic) and i got into it using 3.13.0-55-generic. But i noticed that instead of using the NVIDIA drivers, it used the Intel graphics drivers. And when i started nvidia-settings to change from intel to nvidia, i got a message window with no words but the sign of forbiding the change.

---

### Post by howefield on 2015-07-16
I'd remove the nvidia drivers, boot into the new kernel which should then be using the nouveau drivers for your card - then re-enable the proprietary driver.

---

### Post by Constantinus_Spin on 2015-07-20
Interestingly, when i press Ctrl+Alt+F1, i get into terminal mode. But when i execute startx, loading start but then freezes and when i press again Ctrl+Alt+F1, i see the loading process(Initializing ...., Loadgin ........, etc)  and in the end i get the same message three times:

Warning:       Symbol map for key <KPDL> redifined
                   Using last definition for conflicting fields

Errors from xkbcomp are not fatal to the X server.

At the end of the second repetition of that message, the process freezes.

---

### Post by sudodus on 2015-07-20
Did you remove the proprietary drivers? In that case, did anything change in the boot sequence?

Have you tried some [boot options](https://help.ubuntu.com/community/BootOptions), for example **nomodeset**?

Scroll down to 'Changing boot options Temporarily for an Existing Installation'

---

