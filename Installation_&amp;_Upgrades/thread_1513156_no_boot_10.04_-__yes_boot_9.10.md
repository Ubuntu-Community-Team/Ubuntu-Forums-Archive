---
title: "no boot 10.04 -  yes boot 9.10"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by renegade600 on 2010-06-19
I am unable to boot to the 10.04 cd desktop.  the cd is good because I  used it to install  10.04 on my laptop.

symptoms - get a couple of icons at the boot of the screen one looks  like an old keypunch card with a dash (possible arrow) to another icon  with stick figure inside of a circle as soon as it starts to boot.  Then  (dual monitors)  one monitor turns black and the other one white.  What  is funny is, every time I try,  the montors takes turns being white and  black.   Finally the only way I can restart the computer is to pull the  cord.  

I had absolutely no problems booting and installing 9.1 but I am wanting  to start with a clean install, otherwise I would install 9.1 and  upgrade it through the software center to 10.04.   I know that will work with no problems since that is what I have done for the time being.  

One other thing to note, I get the very same issue when trying to boot  to the latest version of fedora, ubuntu 64bit, kubuntu, and Xubuntu.   And it does not matter whether I install it within windows or outside.

I want to dual boot with win7 (need itunes for my iphone -what can I say) and I am installing it in a second partition on a second physical drive.  

System specs

Win7 pro
4 gigs ram
64 bit x2 dual core 4600
vtech radeon x1300

I appreciate any help

---

### Post by ronparent on 2010-06-19
10.04 seems to have more hardware incompatibilities than 9.10. More so with the more recent changes in graphics chips. You will probably have to experiment with the f6 boot options to find which one or more are needed to boot your equipment - most likely nomodeset. Also, with an ati card I was unable to boot with two monitors plugged in. You will probably have to start out by unplugging one or the other to see if that make any boot differences.

You get to the boot menu by hitting any key when the 1st screen appears - that is what the keyboard/stick figure indicates (I have no idea how you are supposed to figgure that out). I would suggest booting to try 1st, until you find the condition(n) that allows you to boot. In my case I was able to replug the second monitor after installing the restricted drivers for my chipset. Good luck. Post if you need more help.

---

