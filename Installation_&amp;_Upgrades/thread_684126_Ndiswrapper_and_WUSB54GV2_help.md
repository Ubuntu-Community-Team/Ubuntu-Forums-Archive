---
title: "Ndiswrapper and WUSB54GV2 help"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by dmbruley on 2008-01-31
> root@david-desktop:/home/david# '/home/david/Desktop/WUSB54gv2
> ndiswrapper -i wusb54gv2.inf
> '/home/david/Desktop/WUSB54gv2
bash: /home/david/Desktop/WUSB54gv2
ndiswrapper -i wusb54gv2.inf
/home/david/Desktop/WUSB54gv2: No such file or directory

Can someone tell me what this means? I feel like I'm so close to getting this figured out, I can taste it! Why do I get the ">"? What do I need to do to make my pc wireless?

---

### Post by phidia on 2008-01-31
You have to be in the directory that has the .inf file you want ndiswrapper to load when you issue the ndiswrapper -i command. I also think you need to be prefacing that command with "sudo".

For specific issues and troubleshooting I recommend the [Networking & Wireless forums]("http://ubuntuforums.org/forumdisplay.php?f=136").

---

