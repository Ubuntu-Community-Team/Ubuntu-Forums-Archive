---
title: "unity desktop and 22.04"
date: 2022-04-27
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-04-27
I still cannot get Unity desktop to work under 22.04.  I am still getting "sad face" and must log out and log in again using Ubuntu as the choice and not Unity. I have removed and then resinstalled ubuntu-unity-desktop.  Unity worked on this PC before upgrading from 21.10 to 22.04.

Apparently, I have missed an important step.

John

---

### Post by ActionParsnip on 2022-04-27
If you make a new user then log in as that, is it OK?

---

### Post by cigtoxdoc on 2022-04-27
Thank you for your suggestion.  Adding a new user as an admin does not fix the problem.

---

### Post by deadflowr on 2022-04-27
What's the graphics card situation?

---

### Post by cigtoxdoc on 2022-04-27
&#8220;lspci | grep VGA.&#8221;
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)

---

### Post by cigtoxdoc on 2022-04-28
I just had another PC fail to run unity.  I had to do fresh install of 22.04.  For video, this one has 01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [GeForce 310M] (rev a2).  Ubuntu-unity-desktop is installed.

I hope that someone can help me get the unity desktops installed.

Thank you,

John

---

### Post by cigtoxdoc on 2022-04-29
I just had another PC fail to run unity.  I had to do fresh install of 22.04.  For video, this one has 01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [GeForce 310M] (rev a2).  Ubuntu-unity-desktop is installed.

I hope that someone can help me get the unity desktops installed.

Thank you,

John

---

### Post by ronsking on 2022-04-30
[https://ubuntuunity.org/]("https://ubuntuunity.org/")

Maybe this would work for you.

---

### Post by cigtoxdoc on 2022-04-30
Thank you.  Perhaps some other can clarify.  Does use of the ubuntu unity iso require in essence, reinstallation of 22.04?  John

---

### Post by cigtoxdoc on 2022-05-02
The ubuntu-unity ISO did work on one PC of have tried so far.  However, I have lines in GRUB that don't work.  How do i get Grub Customizer for 22.04?  Doesn't show in synaptic and sudo apt install shows program not available.

John

---

### Post by Frogs Hair on 2022-05-02
The linked bug has lead to the removal of the grub-customizer  for the 22.04 release. 

 [https://bugs.launchpad.net/ubuntu/+source/grub-customizer/+bug/1969353](https://bugs.launchpad.net/ubuntu/+source/grub-customizer/+bug/1969353)

There is a PPA.

[https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer)

---

### Post by cigtoxdoc on 2022-05-02
Thank you very much for the ppa

---

