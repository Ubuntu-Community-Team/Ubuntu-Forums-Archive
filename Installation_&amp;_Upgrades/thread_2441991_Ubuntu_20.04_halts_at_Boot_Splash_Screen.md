---
title: "Ubuntu 20.04 halts at Boot Splash Screen"
date: 2020-04-28
forum: Installation &amp; Upgrades
---

### Post by sotires on 2020-04-28
I have exactly the same problem: used Ubuntu successfully for years, now a fresh install of Ubuntu 20.04 I get stuck on the splash screen if I ever log out. 
However, I can't try the various solutions suggested because, as I said, I'm stuck on the splash screen (I'm posting this from another machine). 
Do I really have to re-install (i've already done that twice) just so I can enter the commands to disable splash screen?
Like the OP, i'm using an elderly Lenovo Thinkpad, which ran Ubuntu 19.10 and all the earlier versions since 12.10 with no problem.

---

### Post by QIII on 2020-04-28
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2441821").

Please do not hijack the threads of other users.  Although symptoms may be similar, root causes may be entirely different.  In such cases, threads can become confusing very quickly as people try to solve several problems.

The OP of the other thread, like you, deserves exclusive help on issues.

---

### Post by mrdc76 on 2020-04-28
> **sotires said:**
> I have exactly the same problem: used Ubuntu successfully for years, now a fresh install of Ubuntu 20.04 I get stuck on the splash screen if I ever log out. 
However, I can't try the various solutions suggested because, as I said, I'm stuck on the splash screen (I'm posting this from another machine). 
Do I really have to re-install (i've already done that twice) just so I can enter the commands to disable splash screen?
Like the OP, i'm using an elderly Lenovo Thinkpad, which ran Ubuntu 19.10 and all the earlier versions since 12.10 with no problem.

You don't have to reinstall: reboot (force shutdown or Alt+REISUB) and press Esc when the splash screen appears with the spinner. It should show the boot messages and reach the login screen. Now you can edit grub's config files to enter the commands.

---

### Post by sotires on 2020-04-29
Sorry about that. It was not my intention to "hijack the thread". it was supposed to be a "me too" response, just to show that it really is a bug that affects more than just one person.

---

### Post by sotires on 2020-04-29
What changes do I need to make to the grub file?

---

### Post by oldfred on 2020-04-29
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mrdc76 on 2020-04-30
[https://askubuntu.com/questions/33416/how-do-i-disable-the-boot-splash-screen-and-only-show-kernel-and-boot-text-inst]("https://askubuntu.com/questions/33416/how-do-i-disable-the-boot-splash-screen-and-only-show-kernel-and-boot-text-inst")

---

