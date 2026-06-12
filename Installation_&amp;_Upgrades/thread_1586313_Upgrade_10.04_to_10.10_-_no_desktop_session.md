---
title: "Upgrade 10.04 to 10.10 - no desktop session"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by thewer on 2010-10-01
Hi there,

it's probably just me behaving very dump (Linux beginner), but I cannot start the desktop session:

After upgrading from 10.04 to 10.10 (dual-boot system) via Alt+F2 as suggested on [https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)
Grub loads fine after reboot (booting Windows works, Upgrade without errors).

If I boot Ubuntu (no matter which Kernel, etc.), I end up in shell (black screen + prompt, stating the new Ubuntu version) and being asked to log in.

Entering my name and pw results in the shell prompt changing to my name, but nothing else. So how do I start the desktop session ?
Repairing packages had no effect...

Do I miss a step here?

Thanks a lot for your help! :)

---

### Post by mörgæs on 2010-10-02
Hi, welcome to the forum.

Using a development release is dangerous, and upgrading rather than installing from scratch is even more. Since you are a beginner, I would recommend that you stick to 10.04 until after Christmas.

Anyway, what happens if you write **startx** at the prompt?

---

### Post by sveterv on 2010-10-02
Are you using NVIDIA graphics card?
We need to see what logs are saying, so please attach to your next post that file:
/var/log/Xorg.0.log

---

### Post by thewer on 2010-10-06
Hi there - 

Thanks for your answers, it helped me solve the problem... :)

Yes it's an Nvidia graphic card and it caused the problems (with the release candidate of 10.10). I just didn't think it was responsible as looking through this forum gave me the impression that Nvidia problems would cause graphical glitches, not prevent the desktop session from starting.

Startx will produce an error message regarding the driver.

Solution:
Start Ubuntu in the recovery mode with minimal graphic requirements, it now should start the desktop session, in the menu under system settings select the driver settings, choose the recommended driver (update), restart, done...

Thanks a lot for your help! :)

---

### Post by mörgæs on 2010-10-06
Good, please mark the thread 'solved'.

---

### Post by Ragnar! on 2010-11-11
I had the same problem today. But the update manager did the upgrade so I assumed that it was an official release and went ahead with it. Thank you for the help. I guess I now need to find the thread about what I have to do in 10.10 to get everything up to snuff...lol.

---

