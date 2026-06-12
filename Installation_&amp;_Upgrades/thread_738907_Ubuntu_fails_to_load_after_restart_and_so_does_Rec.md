---
title: "Ubuntu fails to load after restart and so does Recovery mode"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by DjFlush on 2008-03-29
Ok I installed Ubuntu 7.10 and it was working fine

Installed packages and everything and it was still working cool and fine. Then I logged in to Windows to do some of my work and then rebooted.

Now on Reboot when I choose to load Ubuntu, it shows the Ubuntu Loading screen which is instantly replaced by a blank screen with a black background and blinking white cursor on top left.

Then nothing happens for ages

My specs are

NVidia 7600GT
Intel Pentium D 3.00 Ghz
1GB Ram

and the worst part is that when I choose to boot into Recovery mode, even this doesn't load too. It takes like ages to load.

what could be the problem. Please help me Ubuntu'ers

---

### Post by ridgeland on 2008-03-31
Your LiveCD may be able to help you repair the boot process.
Can you still boot the LiveCD OK?

Boot the LiveCD - check out the files that GRUB is trying to load.

Do you want detailed step by steps?

---

### Post by starsphereaz on 2008-03-31
I have a blank screen when boot ubuntu from grub screen and nothing happens. I do not have a live CD, I have 7.04 64-bit CD.  I tried to boot from CD and all I can get is the install a new version screen.  I assume that the upgrade from 7.04 to 7.10 changed the video VGA resolution below what my Nivida video card and my LCD monitor can display. So far I have no idea as to how to change that with in the boot sequence. Has any one got a handle om this?

:mad:This is just one more thing that needs to be fixed with in the Linux OS that will make it more user friendly.  I hope one day that someone much smarter than me will figure out how to make Linux OS superior to Windows in everything that I would like to do with my computer..  I have two masters degrees in acoustic engineering and have to do most of my CAD drafting from windows because frankly CAD in Linux is bad. :mad:

---

### Post by ridgeland on 2008-03-31
Cut and Paste from another post:

> On booting the Ubuntu 7.10 LiveCD using a Dell monitor I click the first option on the menu "Start or Install" after a while I get to the "Cannnot Display This Video Mode". Then [Alt]+[Ctrl]+[F1]. at the $ prompt:
$ sudo su
# nano /etc/X11/xorg.conf
page down to Section "Monitor" change HorizSynch from 30-70 to 30-50, change VertRefresh from 50-160 to 50-100. [Ctrl]+O to "writeout" to same name then [Ctrl]+X to exit nano. Now
# ps -C Xorg
shows the process number to kill like 8441 USE YOUR NUMBER IN THE NEXT LINE
# kill 8441
Then it starts the GUI with a login (10 seconds and it goes away) then I'm at the GUI

Let it boot fully to the black screen, all stable then try [Alt]+[Ctrl]+[F1]  do you get a text window?

---

### Post by ridgeland on 2008-03-31
Hi starsphereaz,
Off the subject of the thread but a suggestion.

I use a very simple 2D CAD package qcad for projects around the house.  It's by RibbonSoft which sells more advanced CAD but being a casual user I cannot comment on their quality.

Four years ago I bought a Windows package to edit WAV files, to remove Click and Hiss from LPs I recorded to CDs (EasyTools).  Linux's Audacity is not as good.  I run it in Linux with VirtualBox with WinXP.  You might be able to run your Windows CAD package in VirtualBox.  I like it because it lets me have Linux for the web and blocks Windows from the web (Virus etc).  Also WinXP is just another window on my Linux system.  I give my WinXP virtual box about 1GB of RAM and it runs EasyTools just as fast in Linux/Windows as it does in Windows.  Your mileage may vary.

---

