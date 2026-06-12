---
title: "New installation in Pentium R 2 Gb RAM"
date: 2015-11-01
forum: Installation &amp; Upgrades
---

### Post by Jaime_Carcel_Trull on 2015-11-01
I have been trying to install Ubuntu 14.04.3 LTS in my old machine, I did not encounter any problem with the installation but  I must have missed some point because once installed the only message that comes up in the black screen after asking for the login and password is 
jaime@ubuntuNAME:~$

I am a total newbie. I cannot understand why the OS does not fully load and the usual desktop comes up.

I would really appreciate your help with this matter.
Thanks in advance.

---

### Post by grahammechanical on 2015-11-01
When you installed did you tick the box "install third party software?" If you ticked that box you got more than some proprietary audio and video codecs, you also got a proprietary video driver. Newer versions of Ubuntu come with newer versions of proprietary video drivers. These newer video drivers do not support older video adapters. I know this to be true because the newest Nvidia drivers do not support my Nvidia GT220 card.

At the Grub boot menu select Advanced options for Ubuntu and then select recovery mode and at the recovery mode select Resume. If that gets you to a working desktop go to System Settings>Software & Updates>Additional drivers tab and select the open source video driver. If a restart is successful then go to Additional Drivers again and see if you are offered a legacy driver. And compare the open source with the proprietary.

You might have to consider if your video adapter can run Ubuntu's Unity 3D user interface. You might need to install Lubuntu or Xubuntu or Ubuntu mate.

Regards.

---

### Post by Jaime_Carcel_Trull on 2015-11-01
I don't remember if I checked install third party software.
I tried the recovery mode and then recovery. I ended up in the same place like before, 
[COLOR=#000000]jaime@ubuntuNAME:~$

But nothing else happened.[/COLOR]

---

### Post by mörgæs on 2015-11-02
Welcome to the fora.
I have never heard of a Pentium R. Are you sure about this?

Anyway, if the hardware is old I recommend that you abandon the present install and do a fresh one of Lubuntu 15.10. Whether or not you add closed-source drivers during installation is unlikely to make a difference.

---

