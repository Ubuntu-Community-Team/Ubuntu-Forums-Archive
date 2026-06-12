---
title: "PC without graphic card"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by fgking on 2011-02-14
I installed ubuntu but when I first tried to login with my correct passwords it goes in a loop and prompt me to log in again. I went to recovery mode and selected safe mode then I was able to log in without any further prompts. As a result of what happened, I unlocked the login screen and changed the setup to allow me to log in automatically and in safe mode only. I am now stuck to login in safe mode only. I tried to unlock the login screen to change to default but no chance. If there is no graphic card in the PC would that have an effect on memory or login? Is there anyone who can guide me to unlock the login screen please.

---

### Post by pricetech on 2011-02-14
If there's no graphics card in the computer, it shouldn't boot.

---

### Post by Harpette on 2011-02-14
Perhaps you could be more specific :
When you say "it goes in a loop", what does this mean exactly? That it logs you in and then out, or that it simply refuses your logging in? If the latter, do you get any error message at all, such as "invalid user or password"?
Then, "I unlocked the login screen" : how did you manage that?
"and changed the setup to allow me to log in automatically": that too, how?
"If there is no graphic card in the PC": is that a headless computer? A server? In  which case, how do you log into it? Remotely via ssh?

---

### Post by fgking on 2011-02-15
Thanks my password seems to be accepted but after a while the screen goes black with mouse pointer showing and then it comes back with normal color and prompts me to login again. How I unlocked the login screen, I think I accessed GDM init  safe mode via recovery. I have tried to do the same and reset to the default but no chance. This is an old PC which has XP running fine using some sort of graphics emulator. I think UBUNTU is also using similar technic.  I have also installed ubuntu on newer pc for my son and did not encounter any problems.

---

### Post by Harpette on 2011-02-27
Log in via a text-only console and examine the X server log file:
ls -o /var/log/Xorg.*
No, wait : if you got the GDM login prompt then X is working
Still, first things first : are you able to log in with a text console?

---

