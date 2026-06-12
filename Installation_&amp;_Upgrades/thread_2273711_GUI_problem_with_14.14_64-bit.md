---
title: "GUI problem with 14.14 64-bit"
date: 2015-04-15
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2015-04-15
Thanks to help from this forum, I have installed Ubuntu 14.10 64-bit alongside a 14.04 32-bit on my Packard Bell EasyNote TS laptop. I have used 32-bit Ubuntu on this machine for over five years without any GUI issues. I use Bumblebee to switch to Nvidia GeForce GPU when watching videos etc but otherwise use the Intel GPU to save power and extend battery life. 

After installing the 14.10 64-bit OS I find that the GUI is stuttering. By this I mean that the mouse icon jumps about on the screen and sometimes replicates with several arrow icons on the screen and cycling between them. Selecting a program from the dash leaves copies of the loading circle all over the screen as the mouse is moved. This only happens with the 14.10 64-bit version of Ubuntu. The 14.04 32-bit OS runs perfectly.

---

### Post by grahammechanical on 2015-04-15
Open About this Computer from the power/cog menu or open System Settings>Details. What information do you see under Graphics. If it says llvmpipe then you are running a fallback open source video driver that can give the effects that you describe.

In System Settings>Software & Updates>Additional Drivers tab what is the video driver that is activated?

Regards.

---

### Post by stepheny on 2015-04-16
After updates the problem seems to have corrected itself and the Intel driver is activated. 

There is a problem with switching to the nVidia driver though, with Bumblebee installed "optirun glxgears" speed doesn't improve over "glxgears". I am trying to fix this. I will ask in another thread if I need help fixing it.

---

