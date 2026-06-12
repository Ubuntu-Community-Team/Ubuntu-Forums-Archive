---
title: "Blank Screen on Booting"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by philip360 on 2007-02-26
Hi all, 
Did a fresh install of **6.10 Kubuntu**.
Everything seemed to go smoothly on text install.

When the install finished and I rebooted I got the grub boot loader
I selected 2.6.17.10-generic

The nice Kubuntu logo displayed and progress bar went to 100%

Then...The black screen....nothing

I rebooted and selected recovery mode and got the root command prompt so I think the system is basically OK.

XP boots OK

I read in my book a command "startx"
It ended up at the black screen

So I think: either kde did not install correctly OR X server is not starting or ATI card problem. (6.06 ubuntu worked OK for video)

I'm not sure what to search on the forum for solution

I have learned a little but not a lot about ubuntu linux so:

Can someone point me in the right direction?? Please and Thanks

Philip

---

### Post by haricharan on 2007-02-27
do u get the text screens by pressing ctrl+alt+F1 - ctrl+alt+F6. if you get the screens the kde installation is good...only thing is the driver for ur ATI card...login in on any of the screens and try ```
/etc/init.d/kdm restart
``` i am guessing its kdm, bcoz its called gdm in ubuntu....any try if it works...

---

