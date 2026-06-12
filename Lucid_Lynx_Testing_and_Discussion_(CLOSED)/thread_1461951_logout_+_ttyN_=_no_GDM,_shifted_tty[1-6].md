---
title: "logout + ttyN = no GDM, shifted tty[1-6]"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by quiritius on 2010-04-24
I noticed a quite unpleasant bug when logging out of Gnome session. Not sure it is reported. Please check whether it is present on your systems.

Just log in the Gnome and do whatever you usually do, then log out. When GDM window with user list is loaded, switch to one of the tty's. When you see the console login prompt, press ctrl+alt+F7 to get back to the GDM screen. Here I consistently see a black screen with text messages left from last boot-up, and a cursor blinking. GDM seem to have crashed. I can switch back to tty1-6 though.

I have proprietary nVidia drivers from the reps installed. My console is set to 1440x900x24 in grub. No "splash" or "quiet" in grub.

Also, probably an irrelevant bug: my console (tty1-6) is intermittently shifted down and right (2 lines from bottom). One time you boot OK (even then the tty1 is always shifted halfway down), the next you have the shift. I tried to boot several times in a row without changing anything and sometime you get the shifted tty, sometimes not. During boot-up text messages are always printed normally, the shift occurs only in ttyN consoles. Usually it helps for a couple of boots in a row to issue sudo update-initramfs -u && sudo update-grub.

Could it be plymouth&#8230; again?

---

### Post by Aearenda on 2010-04-24
After logout, try tty8 (ctrl+alt+F8) to get back to GDM. I don't know why it moves.

---

### Post by quiritius on 2010-04-24
Yes, switching to tty8 did get me to the GDM login screen. Is it normal, I remember it always was tty7…

After re-login I have about about 40 MB more memory consumption then from "clean login" and network manager is missing in the notification area (working OK though). Some more rough edges, I guess.

---

