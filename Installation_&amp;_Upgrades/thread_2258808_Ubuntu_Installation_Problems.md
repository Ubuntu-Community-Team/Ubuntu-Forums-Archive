---
title: "Ubuntu Installation Problems"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by alireza378 on 2014-12-30
Hi guys
I tried to install ubuntu 14.04 and 14.10
But everytime i confront with many errors. such as ( The system is running in low-graphics mode , Low install speed , crashing when install , etc )
While i tried to install xubuntu it installed without any problem and it works good !

My System Performence is :
Nvidia G-Force GT-240 video card
AMD Phenom X2 II 555 Proccessor
1 TB hard disk

You can see that i don't have any tangible weakness in my hardwares... ( Even my system has hardware requirements for installing Kubuntu !! )

**So Why Ubuntu has these problems with my computer ?**

These crash liken ubuntu to a unstable linux distribution :|

---

### Post by Dreamer Fithp Apprentice on 2014-12-30
Some things to try:
The standard installer has a self check option. For a while now I've only used the mini.iso when installing from scratch, so I'm not sure how you get to it. At one point it was available as an explicit choice on the early menu as an alternative to "try ubunt" and "install ubuntu". Later you had to press a key to see hidden menu options. Look for some message referring to additional options as you boot the installation disk. It may tell you what key to press when to get them. If not you might try Esc, del, and various F keys, starting with F1. Or spend a little time with a search engine. Or somebody may post it here. If the installation-media fails the self-check you can try it on another machine to see if perchance it is the cd drive or usb port rather than the media itself or you can go ahead and burn another installer from an iso you've verified the hash of. It is possible you might be able to install from a usb stick installer and not a cd or vice versa. If none of that does it, get pen and paper and try the installation process again but this time write down EXACTLY what error message you get EXACTLY when in the process and post back with as many details as possible.

---

### Post by alireza378 on 2014-12-30
> **Dreamer Fithp Apprentice said:**
> Some things to try:
The standard installer has a self check option. For a while now I've only used the mini.iso when installing from scratch, so I'm not sure how you get to it. At one point it was available as an explicit choice on the early menu as an alternative to "try ubunt" and "install ubuntu". Later you had to press a key to see hidden menu options. Look for some message referring to additional options as you boot the installation disk. It may tell you what key to press when to get them. If not you might try Esc, del, and various F keys, starting with F1. Or spend a little time with a search engine. Or somebody may post it here. If the installation-media fails the self-check you can try it on another machine to see if perchance it is the cd drive or usb port rather than the media itself or you can go ahead and burn another installer from an iso you've verified the hash of. It is possible you might be able to install from a usb stick installer and not a cd or vice versa. If none of that does it, get pen and paper and try the installation process again but this time write down EXACTLY what error message you get EXACTLY when in the process and post back with as many details as possible.

Thank you very much dude :)


**Does anyone has any other idea ?**

---

### Post by Bucky Ball on 2014-12-30
When booting the installer, you will get to the Try Ubuntu and Install Ubuntu screen. Once there, press F6 and choose 'nomodeset'. Proceed. Any different?

Taking a punt, but worth a try. Could be having issues with the Nvidia graphics which can be rectified once installed. The 'nomodeset' option can also be made permanent after install, if that is what is required (and sometimes it is).

---

### Post by alireza378 on 2014-12-30
> **Bucky Ball said:**
> When booting the installer, you will get to the Try Ubuntu and Install Ubuntu screen. Once there, press F6 and choose 'nomodeset'. Proceed. Any different?

Taking a punt, but worth a try. Could be having issues with the Nvidia graphics which can be rectified once installed. The 'nomodeset' option can also be made permanent after install, if that is what is required (and sometimes it is).

Thank you very much my friend

I hope to solve this problem. Otherwise i have to emigrate to other linux distributions 

But i'm sure that this site and its users will help me to solve this :)

I will do your statements and will report the result ;)

ta ta for now

---

