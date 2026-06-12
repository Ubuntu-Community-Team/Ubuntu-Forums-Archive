---
title: "ubuntu pre install display errors"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by damd79 on 2008-04-11
writing assuming knowledge of ubuntu install  

When I choose "Start or install" the Ubuntu logo comes up and the bar starts to move. As soon as the bar finishes the monitor cuts out. The monitor itself gives the error "Signal out of range". The program finishes loading but i cant see anything.

So I boot in safe grafics mode.

Get the error "Failed to start xserver". Go through the next couple questions and get to  a comand prompt, type in the following "sudo dpkg-reconfigure xserver-xorg". Answer all the following questions to the best of my ability. Get to the question about color depth. Every option in that menu gives me an error and boots me the to the prompt. The error in question is:

    xserver-xorg postinst warning overwriting possibly-custum config file; back up in /ect/xll/xorg.config

---

### Post by Partyboi2 on 2008-04-12
When you are at the ubuntu main menu screen press F4 and adjust the resolution.

---

