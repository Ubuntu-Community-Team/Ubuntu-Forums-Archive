---
title: "Ubuntu 10.04 Graphics Messed up"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by EienTatsu on 2010-05-09
When I use the live cd or installed 10.04 there are a bunch of horizontal lines and the screen is jagged and parts of windows are shoved to different parts of the screen. I tried butting up in low graphics mode but the same problem existed.

---

### Post by Catharsis on 2010-05-09
What graphics card do you have?
```
lspci | grep VGA
```

Try adding "nomodeset" to your kernel parameters:
1) Hold down Shift as you boot to enter the grub menu.
2) Press 'e'. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.

---

### Post by EienTatsu on 2010-05-09
the nomodeset fixed it. May I ask if that means I have to do anything else?

---

### Post by Catharsis on 2010-05-09
To make it permanent:
```
gksudo gedit /etc/default/grub
```
Replace
```
GRUB_CMDLINE_LINUX=""
```
with
```
GRUB_CMDLINE_LINUX="nomodeset"
```
Save and exit. Then run
```
sudo update-grub
```

---

### Post by EienTatsu on 2010-05-09
WIll that have an effect on other OS on the machine? The graphics card is "VGA compatible controller: nVidia Corporation C67 [GeForce 7150M /nForce 630M] (rev a2)"

---

### Post by Catharsis on 2010-05-09
Hmm, never thought of that. It should only affect other Linux OSes. I never thought of that though. Do you have other linux OSes on your machine?

---

### Post by EienTatsu on 2010-05-09
I'm going to install Fedora and Mint

---

### Post by Catharsis on 2010-05-09
Yeah, I really don't know enough about GRUB to give you a definitive answer. You can check here through for some more Grub2 info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by EienTatsu on 2010-05-09
It's fine thanks for the help.

---

