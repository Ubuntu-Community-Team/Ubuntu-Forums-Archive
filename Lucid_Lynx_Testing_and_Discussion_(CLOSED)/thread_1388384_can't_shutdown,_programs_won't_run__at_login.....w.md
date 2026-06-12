---
title: "can't shutdown, programs won't run  at login.....what the hell?"
date: 2010-01-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by setherd on 2010-01-23
I have a few problems. I have searched the forums and googled every term I can think of.....
I can't shut down. when I try to shutdown I get the plymouth screen and that's it. if I hit ctrl-alt-del it will reboot about a minute later.

programs don't want to run at login. I have set a program called thinkpad buttons to run at startup using the startup applications function.
I notice that update manager also doesn't run although both are listed in startup applications.

I can't be the only experiencing this...or am I?????

---

### Post by VMC on 2010-01-23
> **setherd said:**
> I have a few problems. I have searched the forums and googled every term I can think of.....
I can't shut down. when I try to shutdown I get the plymouth screen and that's it. if I hit ctrl-alt-del it will reboot about a minute later.

programs don't want to run at login. I have set a program called thinkpad buttons to run at startup using the startup applications function.
I notice that update manager also doesn't run although both are listed in startup applications.

I can't be the only experiencing this...or am I?????

Need more hardware specs. Also have you checked your "/var/log/*" files, dmesg errors, Xsession error log in your home directory?

---

### Post by setherd on 2010-01-23
checked logs, haven't seen anything that jumps out at me.
I have seen an error message at shutdown if I do the following:
when shutdown freezes I ctrl-alt-f1 to another terminal. then do ctrl-alt-del.
I get a message about alsa sound then a message about plytmouth and then it says the system will reboot.
I have a thinkpad T43 with ati X300 video card.

---

### Post by sirkeith on 2010-01-24
I wasw having a similar problem but I could shut down using command line with a -P to power off and then spotted a different shutdown button app in the stuff that pops up for add to panel. I tried it and the machine now powers off. 


keith

---

### Post by thezood on 2010-01-26
I have this problem too. I've also filed a bug report: [https://bugs.launchpad.net/bugs/511436](https://bugs.launchpad.net/bugs/511436)

Not sure if anyone can work with it though since there's so little to go on. Perhaps the problem is related to something else and will be fixed.

---

### Post by setherd on 2010-01-27
thanks, I've posted my info there.

---

### Post by thezood on 2010-02-02
I have also noticed that some startup doesn't run on my machine. For example, I have to run Empathy and nm-applet afterwards. There is also a program called "Install RELEASE" on my System -> Administration menu, like on a live CD. It seems this isn't a proper installation. Weird!
There was a weird thing when I installed my system, I had to make my user administrator manually. Anyone had these problems?

---

### Post by jabastija on 2010-02-02
I have a similar problem. Some programs won't run, when I try to shut down the taskbar disappears and the computer freezes. I have a usb modem and my dialer now says it cant find the modem.
This all started after I installed the latest updates. One other time after installing updates it started acting up also.
Worked fine before update.

---

### Post by setherd on 2010-02-03
OK at least I'm not alone!

---

### Post by setherd on 2010-02-08
I filed a bug report about programs not running at startup here:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/518740](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/518740)

---

### Post by gspat on 2010-02-10
For those of you whose startup programs will not run...

double check you log in under "gnome" and not "failsafe gnome"

I did this and had to manually start all the goodies for weeks until I figured it out!

---

### Post by zika on 2010-02-10
My machine doesn't shutdown properly for a week or so. It doesn't shutdown wit either 2.6.32-12-generic or 2.6.33-999-generic... Just a power switch... Reboot is OK...

---

