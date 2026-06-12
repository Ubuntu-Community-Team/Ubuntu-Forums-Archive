---
title: "How to disable Skype on startup."
date: 2021-04-08
forum: Installation &amp; Upgrades
---

### Post by gardenair on 2021-04-08
Hi,
       I have installed Skype in my Ubuntu 20 box.It is working perfect.The issue is every time when Ubuntu boots it also loaded by default.I cancel it all time then move ahead. I want that every time Skype should not loaded, it  just  consume the memory .
_Is there any way on command line by which I may disable Skype on startup ?_
I does 't want GUI method the command line will be easier.

Thanks in advance

---

### Post by CelticWarrior on 2021-04-08
Skype may have settings for that. It should be the first place to look. I don't use it so I don't know.
If it has no such setting then you can open Startup apps and remove it there.

PS - It doesn't "[COLOR=#000000]just consume the memory". What Skype uses when in standby should be negligible. If you're worrying about such thing you have much deeper problems than Skype.[/COLOR]

---

### Post by cybrsaylr on 2021-04-08
Click on, Show applications.
Select All.
Scroll down to and click on, Startup applications.
Skype for Linux should be shown with a check-mark. Uncheck Skype for Linux and problem solved.

---

### Post by ajgreeny on 2021-04-08
Have a look at ***.config/autostart/Skype.desktop*** and you can either remove it or edit the file by commenting out the Exec= line.

But as CelticWarrior said, there is a GUI button in the Settings->General tab to do this.  See screenshot.

---

### Post by gardenair on 2021-04-09
Thanks for guiding me. :)

---

