---
title: "Where Did Ubunto Go ?????"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by mrkstapleton on 2007-03-11
I am a convert from SUSE. I love the platform! Here's a curve ball ... I downloded and installed *UBUNTU* only. I spet a few hours setting it up and getting my Lap running great. Woke up this morning, turned on my lap and *EDUBUNTU* loaded. I tried every os option on the boot loader (except win) and they all lead to edubuntu. Any help in getting back to ubuntu would be greatly appreciated. 


M

---

### Post by pradeepadapa on 2007-03-11
first of all which flavour of UBUNTU did u download from the site, plse describe in detail............

---

### Post by garybrlow on 2007-03-11
Hmm, are you sure you installed Ubuntu not Edubuntu? When you download the ISO each derivative is labeled as such so to avoid confusion. If it was really Ubuntu, did you by any chance install the edubuntu-desktop meta package which will install all files relating to Edubuntu. Perhaps you could clarify how you installed Ubuntu. The meta packages: Ubuntu, Xubuntu, Kubuntu, and Edubuntu do not automatically install themselves unless of course the installation CD/DVD made from the downloaded ISO is specifically that particular derivative default i.e. Ubuntu, Xubuntu, Kubuntu, and Edubuntu.

If you do not want Edubuntu just remove the edubuntu-desktop meta package and install ubuntu-desktop. You can not have to two desktop meta package, you have to choose one else dual boot which is actually impractical since they are the same OS with a difference of only a few programs. You can install any number  programs from other desktop meta packages/Ubuntu derivative since they use the same repositories.

You can either use synaptic or apt via terminal  to install or remove any software and/or meta package.

ex. $  sudo apt-get remove edubuntu-desktop
      $  sudo apt-get install ubuntu-desktop

Welcome to Ubuntu!!!

Cheers!!! :)


GaryBrlow :biggrin:

---

### Post by louieb on 2007-03-11
In the lower left hand corner of the logon screen there is a session button. Click on it and play around a see what types of desktop sessions are listed.

---

