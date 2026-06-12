---
title: "multiple buggy issues with 14.04.1 new install: 1. GLib-CRITICAL **"
date: 2015-11-02
forum: Installation &amp; Upgrades
---

### Post by michael2009 on 2015-11-02
I will list all the issues with separate posts just to keep things clean here. All are concerned with the same computer: a Dell Optiplex 755 desktop system running a recently installed Ubuntu Gnome 14.04.3 (64-bit)

So, the first issue: after an initial software update (using Software Updater), I installed Synaptic Package Manager. Using Synaptic, I downloaded some additional packages i.e. Leafpad, Bleachbit and a few others from the official repositories. However, when the packages are being installed, I always get a line at the beginning of the install details window: 

(synaptic:3350): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed

I have no idea what it means. I am not a techy type who understands lots of codes and scripts, sorry but I am too old and still too busy! However I have done loads of successful installations of Debian, Ubuntu, Linux Mint etc over the last six years. I have also had this problem with nearly all the Linux installations I have done over the past two years, including a new install of Linux Mint on two laptops at home. 

I would much appreciate it if anyone out there can explain and/or help me to resolve this issue.

---

### Post by mörgæs on 2015-11-03
Is this the bug?

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1282542](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1282542)

---

### Post by michael2009 on 2015-11-03
Yes, all the reports in your link suggest something similar or identical with my experience. 

I noticed one post in the link: [Bug #1282542]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1282542")   Comment #10. It is about a possible cause due to the settings in /home, after reinstalling but keeping an existing /home partition. I initially suspected the same, and re-installed a completely new system including fresh /home partition, but the bug reappeared again after using Synaptic.

i have not noticed any loss of functionality, but it is annoying all the same, especially as, like another user noted, I never had this problem with Ubuntu 12.04. It may be minor, but it should be fixed don't you think?

---

### Post by mörgæs on 2015-11-03
Maybe it's fixed already. Have you tried 15.10?

---

### Post by michael2009 on 2015-11-03
Almost, but I gave up on the 2+ hours download/upgrade process! If you are using 15.04, perhaps you could confirm whether it has the same issue or not? It would be nice to know.

---

### Post by michael2009 on 2015-11-03
Btw, I prefer the LTS versions. I am afraid of more bugs, because I have more than enough already.

---

### Post by mörgæs on 2015-11-03
If you want to avoid bugs then it's better to move on to 15.10. Bugs in old software like 14.04 is unlikely to get fixed except for security ones. Since the bug in question is not related to security I don't think there is much hope. 

Only if you want closed-source ATI drivers I see a reason not to try 15.10.


Your other question: I don't think I have seen the bug in 15.04 but I install most programs using the command line and use seldom Synaptic.

---

### Post by michael2009 on 2015-11-20
I am sticking with 14.04 LTS because it is a perfectly good system that has worked on other computers with few problems/issues. 

So now for the second issue. Every time I boot up my computer, after the first manufacturers window, and before the Ubuntu logo appears, I am getting a black screen with a notification in the top left corner of the screen. It looks like this:

[1.01951395] ACPI PCC Probe failed

The number between the [] brackets changes each time I boot the computer. Some other examples: [1.0114579]  [0.947355]

The only loss of functionality with the ACPI that I have noticed is that there is no slider in the Brightness and Lock Settings window
I have also tried reinstalling the ACPI package, but it doesn't solve the problem. Anyone got any ideas on a possible solution?

---

### Post by Geoffrey_Arndt on 2015-11-20
How about testing Wily Werewolf on a usbstick install (not a live install - but a full install to a 16 or 32 gb stick.)   Wonder if that would exhibit the same behaviors?   BTW, 15.04 and 15.10 were both flawless installs and no bugs on a System76 Galago Pro Laptop.   Nothing beats getting a system designed to run Linux versus only WIndows.

---

