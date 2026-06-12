---
title: "Laptop Logs Out When I Put It To Sleep"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by suprman2020 on 2010-03-17
I'm not sure if this is a bug or a new "feature," but when I put my computer to sleep, it's always logged out when I resume. Is it a setting I could have possibly changed? Whatever it is, is there a way to stop it from logging out?

---

### Post by StanleyEnn on 2010-03-17
Hi! I had the same problem after installing and enabling the newest nvidia driver in Lucid Lynx alpha 3. After reverting to the previous one (v. 173) the problem disappeared.

---

### Post by ildfroe on 2010-03-17
> **suprman2020 said:**
> I'm not sure if this is a bug or a new "feature," but when I put my computer to sleep, it's always logged out when I resume. Is it a setting I could have possibly changed? Whatever it is, is there a way to stop it from logging out?

Press alt-f2 and enter: gconf-editor
Go to apps/gnome-power-manager/lock and uncheck the boxes.

---

### Post by StanleyEnn on 2010-03-17
Hi, ildfroe! Aren't you by chance confusing screen locking with logging out? I suppose that suprman2020 talks about having closed all running applications by the system when putting the laptop to sleep.

---

### Post by nhasian on 2010-03-17
go to System->Preferences->Screen Saver and untick the box labeled "Lock screen when screensaver is active"

---

### Post by joske on 2010-03-17
I've noticed this too.

He is not mistaking screen lock, you are logged out after resume from suspend/hibernate. I'm on 195.36.08.

---

### Post by alexmurray on 2010-03-17
X crashes when you resume which hence causes all your apps to die - gdm then restarts and so you're left looking at the login screen - its a known bug [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/534754](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/534754) which should be fixed by the recently released 195.36.15 Nvidia driver which as yet is not packaged in Ubuntu.

---

### Post by suprman2020 on 2010-03-17
Thanks for the answer about the lock screen. Does that bug also affect Intel Integrated graphics because I don't have Nvidia?

---

