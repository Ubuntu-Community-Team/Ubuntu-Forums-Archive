---
title: "Unable to login after fresh install"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by wasko7 on 2020-04-24
Hi,

I bought a second hand desktop with Win 10 pre-installed several months ago.  I did a dual boot Ubuntu 19.10 installation as I have many times before but I have not been able to log in consistently to my Ubuntu install.  Most times I get stuck in a loop at the log in page.  I put in my password (even though I checked login automatically) and I just keep going round in a loop back to the same login page. I thought it might have something to do with my partition setup so I erased all my disks, re-installed Win 10 then re-installed Ubuntu 19.10 but the problem persists.  I've tried numerous "fixes " found on-line but none have been successful.  So I over wrote my Ubuntu install and tried Ubuntu DDE Beta for a few weeks and it performed flawlessly.  Feeling that my last tweaks may have fixed it.  So tonight I down loaded Ubuntu 20.04 installed it and now I'm back to the loop at the log in screen again.  Can anyone please help me I'm fresh out of ideas. Below are pictures of my partition setup.  But the fact that it works fine with Deepin as a desktop environment makes me think that it could be a Gnome issue.

---

### Post by iekanat on 2020-04-27
I too have this problem...

---

### Post by CelticWarrior on 2020-04-27
There's a bug still being worked on with autologin and some graphics cards.
Considering autolgin shouldn't be used, just don't.

---

### Post by wasko7 on 2020-04-27
> **CelticWarrior said:**
> There's a bug still being worked on with autologin and some graphics cards.
Considering autolgin shouldn't be used, just don't.

Thanks for the info.  Since I've got nothing invested in this install I'll do a quick re-install and untick auto login and see how it goes.

---

### Post by CelticWarrior on 2020-04-27
Yes, that makes sense.

If you have a Nvidia Graphics don't forget to tick the option to install drivers and also disable Secure Boot in UEFI.

---

### Post by rbmorse on 2020-04-27
Switching from GDM3 to lightdm will unstick it, too.

---

### Post by wasko7 on 2020-04-28
Thanks Celtic Warrior and rbmorse.  Before I saw your latest posts I did a fresh install ticked install driver as I have an Nvidia Graphics card,  unchecked Automatic login but I left secure boot enabled in UEFI and on install.  So far after 48 hours no issues.  I'm hoping that this has solved the problem. If it re-occurs I will do a re-install without secure boot and change from GDM3 to lightdm .  Thanks for both of your advice.

---

