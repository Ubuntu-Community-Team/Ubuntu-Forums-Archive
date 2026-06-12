---
title: "NumLock won't work on Dell 7720 running Ubuntu Unity 22.04"
date: 2022-09-02
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-09-02
My Dell 7720 laptop is dual-boot: Ubuntu Unity 22.04 and Win 11 Pro Insider Build.  BIOS is set for NumLock key to work.  It works fine in Win 11.  It does not work in Ubuntu Unity.  Indeed, the entire keypad is dead.  What do I need to change to get NumLock and keypad working?

Thank you,

John

---

### Post by Claus7 on 2022-09-03
Hello,

I would try to install numlockx from synaptic and add it as a startup application and see what happens. Normally it should work without you needing to do this. Just a proposal.

Regards!

---

### Post by cigtoxdoc on 2022-09-03
Thank you for your suggestion.  Unfortunately, it did not work.  I did find at [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock) a section about adding greeter-setup-script=/usr/bin/numlockx on to /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf .  The instructions mentioned Ubuntu 14.04.  Are they still valid.

John

---

### Post by cigtoxdoc on 2022-09-03
Also, the suggestion I posted earlier did not work.  If the KEYBOARD section of SYSTEM SETTINGS is supposed to have a section on the keypad as reported for previous version of Ubuntu, it is not there now.

John

---

### Post by cigtoxdoc on 2022-09-19
SOLVED.  Just needed to set Mouse Keys -- Control the ponter using the keypad to OFF.

---

