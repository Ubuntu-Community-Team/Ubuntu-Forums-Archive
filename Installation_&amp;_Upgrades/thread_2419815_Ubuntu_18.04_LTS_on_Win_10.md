---
title: "Ubuntu 18.04 LTS on Win 10"
date: 2019-05-25
forum: Installation &amp; Upgrades
---

### Post by BigYellowDog on 2019-05-25
After I run apt update & apt upgrade in the Linux subsystem on Windows 10, I can not restart the Ubuntu shell.  The shell opens up but it is just a blank terminal, no prompt.

I tried uninstalling Ubuntu & reinstalling with no success.  The only fix is to remove %USERPROFILE%\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu18.04onWindows_79rhkp1fndgsc folder and
reinstall the Ubuntu subsystem from the Microsoft store.  I have been able to replicate this.

I'm not sure if this is the correct place to post this, if not please recommend a more appropriate place.

---

### Post by yancek on 2019-05-26
> I'm not sure if this is the correct place to post this, if not please recommend a more appropriate place.

This is windows software and the link below is to the microsoft site with an explanation on installing it.  Doing an online search for " linux subsystem for windows" will give you a number of resultls.

[https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

---

### Post by BigYellowDog on 2019-05-28
My question was not about how to install linux subsystem for windows, I've been running it for over a year.  My question is once it is installed apt update & apt upgrade breaks the program.

---

### Post by yetimon_64 on 2019-05-28
> This is windows software and the link below is to the microsoft site...

@ OP, that link also has troubleshooting and FAQs sections you should utilize.

At the bottom of the troubleshooting section is a product feedback link that you should use for this situation, see next screenshot.
[ATTACH=CONFIG]283332[/ATTACH]

> apt update & apt upgrade breaks the program.         The Microsoft WSL application does not support all linux features, don't assume it is apt that is breaking your WSL program. Running apt on an installation that does not support all linux features is likely to cause problems like this, report the problem to Microsoft being that the problem is just as likely to be with one of their products. They are more likely to be able to fix this for you. 

Regards, yeti.

---

