---
title: "I can't install anything"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by [zerophase] on 2006-10-03
Hey! I'm completely new to ubuntu and linux but I like it a lot more than windows haha. Anyways, I just installed it onto my laptop and now I'm trying to add more apps through the add/remove programs under applications but everytime I select a program and try to apply it this error messgae comes up: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." Help me please! and thanks in advance.

---

### Post by wieman01 on 2006-10-03
Try the most obvious and open at terminal window (command line)... Then type this and press enter:
> dpkg --configure -a
That done, try to add programs once again.

---

### Post by [zerophase] on 2006-10-03
i typed that in and it told me i needed superuser privileges so i typed su in and it asked for my password. i entered my pass for my account and it says auth. failed.. but when i installed ubuntu it only asked for one password and this is the only password i have set up... i don't know what the su pass could be besides this one password i have. what should i do?

---

### Post by wieman01 on 2006-10-03
Sorry... My fault... Try this and key in your password when prompted:
> sudo dpkg --configure -a

---

### Post by [zerophase] on 2006-10-03
it keeps saying i have broken packages and to use a broken filter to find them... how do i do that?

---

### Post by unisol on 2006-10-03
go to system adminstrator and click on synaptic package manager when it opens click on fix broken  packages (i think its under the edit menu ) then click apply to fix broken packages

---

