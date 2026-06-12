---
title: "Unable to install ubuntu 10.04"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by sojukrishna on 2010-07-31
hi all

 i am unable to install ubuntu 10.04, the problem in between the installation is like this:

the screen blinks for many time and after changing two of my monitors it shows lik this:

Ubuntu is running in low graphics mode
The following error was encountered. you may need to update your configuration to solve this.
(EE)intel(0):No valid modes
(EE)screens(s) found, but none have a usable configuration.

After that many options given..i tried all..but screen becomes completely black...wat to do..i love working with ubuntu, pls help me out.

---

### Post by Rubi1200 on 2010-07-31
You could try the workaround mentioned here:
 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
 
The error message you see indicates that you have an Intel chipset; use the i915.modeset=1 option and see if that helps.

---

