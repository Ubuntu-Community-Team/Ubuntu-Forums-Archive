---
title: "newly installed 18.04.1 on new laptop has no wifi and crashes on opening settings"
date: 2018-08-25
forum: Installation &amp; Upgrades
---

### Post by janw-oostendorp on 2018-08-25
I got a new laptop ([this one]("https://www.paradigit.nl/hp-power-pavilion-15-cx0670nd-qwerty/80051158/product")). I've made fresh new live-USB and installed Ubuntu.
Wifi was not available during this install.

Most of the time the system freezes when I login, I can move the mouse but it does not do anything.

Only way to get into the system is via recovery.

And still no Wifi. Pluging in a cable works.
But when I open system settings the windows doesn't show up and the system freezes.

**Where do I start looking?**

The laptop is a pretty new model, are there drivers incomplete?

I also installed updates with the cable plugged-in, no difference.

---

### Post by oldfred on 2018-08-25
Have you installed the nVidia proprietary driver? Do not install from nVidia directly, but from Ubuntu repository or add ppa for very newest drivers.
If you use nomodesest does it boot ok? Nomodeset should then not be required once nVidia driver installed.

[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

Start a new thread in the Wireless sub-forum and see sticky thread at top on running the wireless script. Then those that know wireless issues may be able to help.
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by janw-oostendorp on 2018-08-25
Okay, I figured it out.

I got wifi working when I turned off secure boot.
The freezes where a lack of graphic drivers, [solution here]("https://askubuntu.com/a/1030490")

---

### Post by ajgreeny on 2018-08-25
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

