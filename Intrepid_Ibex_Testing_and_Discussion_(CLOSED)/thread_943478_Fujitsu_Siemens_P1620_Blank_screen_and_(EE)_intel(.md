---
title: "Fujitsu Siemens P1620: Blank screen and (EE) intel(0): overrun on pipe B! on Intrepid"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by JD82 on 2008-10-10
The LiveCD of Intrepid Ibex Beta get a blank (black) screen once it has entered into graphics mode. The same happens with the LiveCD of Hardy and Gutsy.

The computer still works, I can hear the start sound of GDM, and I can log in from GDM, but I just can't see anything on the screen.

With the Feisty's LiveCD the problem does not occur. By viewing the xorg.conf I noticed Feisty uses the i810 driver.

Changing the xorg.conf in Hardy and forcing the use of "i810" driver the problem does not occur. Using the drivers "intel" the problem reoccurs.

In Intrepid Ibex **does not work** even with the i810 driver.

[IMG]https://bugs.launchpad.net/@@/bug-high[/IMG] [Bug #221119]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221119")

Take a look at the logs, in particular the xorg.log and the gdm.log showing the following error:
```
(EE) intel(0): overrun on pipe B!

```

I do not know what to do, any suggestions?

---

### Post by Piraja on 2008-10-18
I have a problem that might be related. At the moment, I can log on to my Gnome session without problems, but after logging out, most of the time all I see is a black screen. I can hear the log-on prompt sound, but no GDM screen, so I have thought it's better to just drop into a virtual console with Ctrl+Alt+F1 and reboot — then I can log in again. 

This problem has appeared (with an apparently related problem with Compiz, which I had to remove from my installation) after upgrading from Hardy to Intrepid Ibex. The relevant log files show an error: "(EE) Intel(0): overrun on pipe A!"

I added a comment to your bug report. I hope our reports will help the developers to fix these issues soon.

---

### Post by Piraja on 2008-10-18
PFA my corresponding log files.

---

### Post by JD82 on 2008-10-19
Thank you for your reply.
Today I tried the LiveCD of Fedora Core 9 and OpenSUSE 11.1 Beta2 but also these distributions are unable to start the graphical environment.

---

### Post by timjohn7 on 2008-10-22
I have the same problem on a Fujitsu Siemans Amilo with 82845 Intel graphics.
Everything worked fine in Hardy but II remains broken.  I have tried disabling compiz (which worked for a while) but the new kernel 27-7 broke everything again.
I am currently running Kubuntu which appears to be OK and I still have Hardy on another partition while I check things out.

---

