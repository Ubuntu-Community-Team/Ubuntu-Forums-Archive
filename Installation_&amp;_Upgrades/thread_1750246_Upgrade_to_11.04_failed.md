---
title: "Upgrade to 11.04 failed"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by mpve on 2011-05-05
Dear all,

Last week I upgraded from 10.10 to 11.04. After the reboot following the upgrade I came into the usual login screen. My mouse and keyboard were not working however so I could do nothing with the computer.

I solved this problem by doing the following:
---Reboot the PC
---When the BIOS messages appear press the SHIFT key and keep it pressed until the GRUB menu appears
---Choose for recovery mode
---Choose DPKG and (re)run it until all software is installed and all dependencies are satisfied. The problem, in my case, was that some software failed to install during the upgrade and that kept X-window from recognizing my keyboard and mouse

Hope this helps you too.

mpve

P.S.: I was able to find this out looking at the logs in system. I could login because I pulled the mouse USB plug from the USB socket and inserted it again. The system then recognized the mouse and I could activate the on screen keyboard to type in my password. Then I could approach the logs via the admin menu :-).

---

