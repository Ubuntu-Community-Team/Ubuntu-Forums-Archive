---
title: "USB mouse and keyboard unresponsive after update with Kernel 4.2.0-17"
date: 2015-11-06
forum: Installation &amp; Upgrades
---

### Post by digital-daniel on 2015-11-06
I had an update this morning with kernel 4.2.0-17. At boot up it goes to a very large login screen (sometimes) and the keyboard and mouse are responsive so it is impossible to log in. 
If I try to run in safemode, the keyboard is unresponsive so it's impossible to choose safe mode.

Works fine if I run advanced options and use kernel 4.2.0-16 


I don't think I'm alone with this problem, but can't actually find any solutions (other than manually selecting the kernel I want at start up).

Any suggestions are warmly welcomed.

Thanks

Daniel

---

### Post by noah29 on 2015-11-06
Hi Daniel,
I am also having this issue. Booting into the older kernel works fine. 
In addition to the keyboard and mouse, touch screen does not work either. Like you said, the resolution appears to be small causing everything to look big. The other monitors I had connected to the system don't have any signal.

-Noah

---

### Post by digital-daniel on 2015-11-06
Hi Noah,

I've edited my grub to give me the option to chose the version I want at boot up. But I hope there's a better solution out there. I'll follow up here if I find out anything helpful.  

command for grub: 
sudo gedit /etc/default/grub

in the line: 
GRUB_HIDDEN_TIMEOUT=0  - I added # so that line is ignored. It now reads

#GRUB_HIDDEN_TIMEOUT=0

then saved, closed and did
sudo update-grub

---

### Post by noah29 on 2015-11-07
I had to reinstall Ubuntu this morning due to unrelated reasons, but after the reinstall, I did the update and was expecting the same outcome. To my surprise, everything booted normally. Not sure if there was additional update that fixed the issue or what. Hmm.

---

### Post by prise2 on 2015-11-08
I had the same problem. This morning I updated Ubuntu. The update installad a new kernel-4.2.0-17-generic-extras. After reboot everything works fine now. 

Prise

---

### Post by digital-daniel on 2015-11-08
Update solved it for me too. 

Yeah!

---

