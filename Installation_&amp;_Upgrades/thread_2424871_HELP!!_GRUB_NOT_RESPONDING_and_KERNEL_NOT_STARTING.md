---
title: "HELP!! GRUB NOT RESPONDING and KERNEL NOT STARTING"
date: 2019-08-16
forum: Installation &amp; Upgrades
---

### Post by jeremyimmanuel on 2019-08-16
Hello,

So I dual booted my desktop with windows 10 and ubuntu 18.04. So at first my grub (boot selection menu) didn't work with my keyboard so it always boots up to ubuntu, and I cannot get into UEFI settings because the computer was to fast. So I researched some solution, and I stumbled upon this person's solution: [https://forums.gentoo.org/viewtopic-t-1068792-start-0.html](https://forums.gentoo.org/viewtopic-t-1068792-start-0.html) which said


So I did that, but it didn't fix the problem, and worse, now it doesn't detect linux.
[IMG]https://mail.google.com/mail/u/0?ui=2&ik=441ee2b4c1&attid=0.1&permmsgid=msg-f:1642000662538447339&th=16c98ee7238f69eb&view=fimg&sz=s0-l75-ft&attbid=ANGjdJ-E0Wgo7O1rVWLLOR_hXFy23S2rE3bLpg1AZErcnZ-PVczAeD3DKNsqRT31hccIf1cuae5lrtgZpV80SbfPO3sQPzszq0FBlx-6SzyAYm8alilWaJ-PrLx1URo&disp=emb[/IMG]

Can someone know the solution? Like how to force the computer to UEFI setting through the power button? Or maybe is there a way to wipe my ssd and start from fresh (not preferable but if it does go to this then i'm ok with it).

Thank you so muchhhh.

---

### Post by ubfan1 on 2019-08-16
When shutting down Windows, hold down the shift button, and select restart.  You'll get some menu choices which I don;'t totally remember, but "Troubleshooting" is one of them, then Settings, and from there you can get into the UEFI settings/BIOS.  Change the "fast boot" to off, or give a time like 10 seconds to allow you to type the function keys to get into UEFI setup again.

---

### Post by Rubi1200 on 2019-08-17
Didn't see it mentioned in that link but you probably should have run ```
sudo update-grub
``` when done with the config file for all changes to take hold.

If you are able to get back in I recommend running the summary report (first link in my signature) so we can see what is going on.

Please note, do not repair just run the report and post here.

Thanks.

---

