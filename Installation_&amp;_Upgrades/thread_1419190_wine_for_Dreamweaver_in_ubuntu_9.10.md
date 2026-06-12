---
title: "wine for Dreamweaver in ubuntu 9.10"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by ljupcho on 2010-03-01
Hi,
I am trying to install wine in order to install Dreamweaver under Ubuntu 9.10.
I installed wine and then there are some folders that i need to copy from my windows, but i am having problems with these:

3- copy  C:\Documents and Settings\your-windows-user-name\Application Data  to /home/username/.wine/drive_c/windows/**profiles/All Users/Application Data/**
-- i am not having the "profiles" folder under .wine/drive_c/windows/ , how come?

6-copy   Winsxs  from   C:\windows    to /home/username/.wine/drive_c/windows/  (this folder is  verry  important)
-- here i am not having the "Winsxs" file from Windows, that is strange! Instead i already have that folder in ubuntu partion like "winsxs" and in it contains: manifests/x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef.manifest

I though i had wine installed incorrectlly, so i did:
sudo aptitude remove wine && sudo apt-get autoclean && sudo apt-get autoremove

but i can see that didn't quite remove the wine! It was still under Applications/Wine/...

So, is wine installed correctly? Do i need to configure it somehow?

Thanks,
Ljupcho

---

### Post by joek71 on 2010-05-05
Here follow the instructions on this link

[http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html](http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html)

---

