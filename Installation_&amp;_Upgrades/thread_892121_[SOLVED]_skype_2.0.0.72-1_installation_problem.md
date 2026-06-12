---
title: "[SOLVED] skype 2.0.0.72-1 installation problem"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by tgklohn on 2008-08-16
Hi,

I need a hand to install skype version 2.0.972-1 in my kubuntu 7.10. The GDebi Package Installer should do the hard work for me, I know, but it isn't working. The installer just makes the computer slower and then closes itself. Is there a command I can give through the terminal to install the downloaded program?

thnxs

---

### Post by Partyboi2 on 2008-08-16
open a terminal and change directory to where the deb file is. So if its on your Desktop type
```
cd ~/Desktop
```then to install type
```
sudo dpkg -i package
```change "package" to actually name of package.

---

### Post by tgklohn on 2008-08-17
Partyboi2,

Thanks a lot! Actually, the skype had already been installed in my first attempt. I found it installed after following your instructions and getting to the same "problem" as before. Then I tried to search for the skype and found it ready to be used.

T G Klohn

---

