---
title: "Kubuntu Jaunty fglrx dualhead (big desktop) problems"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by shappie on 2009-04-19
Hello,

i'm using kubuntu 9.04 fully up to date. I installed the 9.4 ATi drivers from the site using this tutorial: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

Now fglrx is running. I can use desktop effects and glxgears in terminal. But i have 2 screens plugged into my system so i would like to have one big desktop on both screens. So not cloned like now. When i start the Catalyst Control Center i could normally (with ubuntu 8.10) just go to the Manage Screen section and then just choose for Big Desktop. Which worked great for me but now i cant choose anything. I even cant choose cloned. It just says in grey unknown. But it does recognize my screens because it got 2 screens in the list and good resolutions and names.

How can i enable the Big Desktop feature now?

Thanks in advance, Shappie
(ps. i have a R600 chipset, HD3850 card)

edit: I think the problem is caused by RandR 1.2. RandR doesnt cooperate with fglrx and i think thats the problem. I found it out by trying to setup the dualhead setup using the aticonfig tool in terminal. This command gave this:
```
mart@mart-kde:~$ sudo aticonfig --dtop=horizontal --overlay-on=1
[sudo] password for mart:
Error: Options, e.g. --dtop and --desktop-setup, are not supported when RandR 1.2 is enabled!
Warning: Failed to set hardware overlay to head 1 immediately.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-6
mart@mart-kde:~$

```
I googled on it but cant find out how to fix it. Can i disable RandR1.2? Or can i solve this conflict another way?

edit2: I found a guy with same problem but no solution: [http://forums.amd.com/forum/messageview.cfm?catid=310&threadid=110989](http://forums.amd.com/forum/messageview.cfm?catid=310&threadid=110989)
edit3: Same prob: [http://bbs.archlinux.org/viewtopic.php?id=68124](http://bbs.archlinux.org/viewtopic.php?id=68124)
edit4: I fixed the problem with some help of the phoronix irc channel.
This is the solution: I had to put XRandR off and here i will show you how (if you use fgrlx driver...):
Reboot your pc into recovery mode and choose for the root option (just terminal without network acces). Type: sudo nano /etc/ati/amdpcsdb
Than you have to add this: EnableRandR12=SFALSE below: [AMDPCSROOT/SYSTEM/DDX]
Save the file (control+o) and exit nano (control+x).
(optional: Reset xorg.conf to default ati settings: sudo aticonfig --initial)
Reboot pc. Start Catalyst Control Center (amdcccle) and configure your multiple screens the way you like it ;).

---

