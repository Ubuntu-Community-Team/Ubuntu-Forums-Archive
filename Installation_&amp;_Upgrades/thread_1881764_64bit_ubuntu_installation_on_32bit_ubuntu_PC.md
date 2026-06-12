---
title: "64bit ubuntu installation on 32bit ubuntu PC"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by vinayakahegde on 2011-11-16
I would like to install 64bit 11.04 ubuntu on a PC which is having 32bit 11.04 ubuntu. Is this possible? If yes, where can I get the documentation for the same?

---

### Post by raja.genupula on 2011-11-16
> **vinayakahegde said:**
> I would like to install 64bit 11.04 ubuntu on a PC which is having 32bit 11.04 ubuntu. Is this possible? If yes, where can I get the documentation for the same?

 I think its not possible  man , this is what i think . But even though its installed , i think performance issues will rise .

I suggest you to go with 32-bit os.

---

### Post by tartalo on 2011-11-16
I don't think it's possible to "upgrade" from one to the other, but as long as the CPU is supported I don't see why you could not replace your OS with a fresh install. If you have a separate /home partition it's a non-issue.

---

### Post by vinayakahegde on 2011-11-17
Thanks a lot for your  inputs.
 
-Vinayaka

---

### Post by fantab on 2011-11-17
> **vinayakahegde said:**
> I would like to install 64bit 11.04 ubuntu on a PC which is having 32bit 11.04 ubuntu. Is this possible? If yes, where can I get the documentation for the same?

If your CPU or Processor supports 64bit then YES you can CLEAN install and use Ubuntu_64bit, however you CANNOT upgrade form Ubuntu_32bit to Ubuntu_64bit. It has to be a Fresh and Clean Installation.

---

### Post by Tickeldi on 2011-11-17
It needs to be a fresh install but you don't have to have /home in another partition.

It is not going to be deleted if you tell the installer to use that partition in its same role with the same filesystem as before and not to format it. That way the installer will delete system related folders (/var /usr /etc...) but not /home.

---

### Post by sammiev on 2011-11-17
I would think your system is a 64 bit or your install would have been a mess. You can install 32 bit on a 64 bit system but not the other way.

---

