---
title: "Openoffice menu text corrupted plus freezes"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by durzagott on 2010-06-09
I have recently done a clean install of Ubuntu 10.04. Since then I have had no end of trouble with Openoffice 3.2.

When I open any office app, the text on the menus is corrupted and has lines going through it. I've included some screenshot to show what I mean.

Also, sometimes when I open an Excel spreadsheet my entire system crawls to a standstill and it can take anything up to 10 minutes for it to respond again. Not even the mouse cursor will move. If I reboot the PC and open the same document it will sometimes be just fine. It is very random.

So far I have tried uninstalling and reinstalling openoffice.org from apt-get, but this hasn't fixed the problem. 

My system:
OS: Ubuntu 10.04
CPU: Core 2 Duo
GPU: nForce 610i/nVidia 7050 (onboard VGA)
RAM: 2GB

Can someone please help me look into this? I frequently have to deal with office documents at work and this is having a serious impact on me. Please help!

---

### Post by Hagar Delest on 2010-06-09
See that one, several fixes (read until the end): [[Solved] No text in OpenOffice menus](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183).

---

### Post by durzagott on 2010-06-10
> **Hagar de l'Est said:**
> See that one, several fixes (read until the end): [[Solved] No text in OpenOffice menus]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183").

Thank you. I think I've solved the problem now. I updated my JRE by typing

```
sudo apt-get install default-jre
```It seems to be working much better now.

---

### Post by novicee on 2010-07-11
deleted post.

(realised where I could find the answer to my question)

---

