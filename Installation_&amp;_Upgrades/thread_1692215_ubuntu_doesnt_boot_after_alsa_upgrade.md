---
title: "ubuntu doesnt boot after alsa upgrade"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by skarosg3 on 2011-02-21
Hi all,
I had some problems with my sound recently so i decided to upgrade my alsa driver using this guide
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

Now the machine will boot, but stuck on the "welcome" screen, where it says ubuntu and has some dots that change collor from white to red.

I left it there working ( i thought maybe it was doing some upgrading or something) but almost an hour later nothing changed!!!

any ideas pls?!

thanks, ilias

---

### Post by skarosg3 on 2011-02-21
after pressing F4 while loading i am getting this:

> 1 package can be updated
89:124002]BUG: soft lockup - cpu#0 stuck for 61s![modprobe:582]

broadcast message gfrom root@"mycomputername"
(unknown) at cc

and when i press the off button i am getting this:

> the system is going down for halt NOW!
Power button pressed
acpid :exiting
in ti: cron main process(846) kille3d by term signal
tty1 (1176)
alsa-mixer-save (1374)
*stopping TiMidity++ ALSA midi emu;atyiopn...
Stopping Jetty servlet engine n(was reachable on [http://computer:8080/](http://computer:8080/))
*not running
*stopping VirtualBox kernel module

[xxxxxxxx]BUG: soft lockup - cpu#0 stuck for 61s![modprobe:582]
[xxxxxxxx]BUG: soft lockup - cpu#1 stuck for 61s![kstop/1:1441]

now, i see that i havent copied them properly, sorry, but i was in a hurry, i thought that it might switch off at any time.

anyone that could help?

i have a 10.10 cd that i am using now in live mode. is there a way to upgrade to 10.10 without loosing everything?

I could copy everything to my external HD but i would rather keep it as it is.

thanks

---

