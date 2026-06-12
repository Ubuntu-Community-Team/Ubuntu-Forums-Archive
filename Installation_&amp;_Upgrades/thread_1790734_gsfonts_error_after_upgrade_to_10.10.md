---
title: "gsfonts error after upgrade to 10.10"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by harr986 on 2011-06-25
Recently upgraded to 10.10 via Update Manager. After upgrade my Epson Stylus R340 printer wouldn't work. In main menu I went to System->Administration->Printing. Nothing was listed under printers any longer. Clicked Help->Troubleshooting. It suggested to go to System->Administration->Services. No Services menu was listed under System->Administration. In Terminal I ran [sudo lshw], no printer was listed. I then went to the Synaptic Package Manager and searched Epson and checked reinstall on all packages which were installed. The reinstall returned this error "E: gsfonts: subprocess installed post-installation script returned error exit status 1" followed by several package dependency problems. I then followed the same steps after a search for cups in Synaptic Package Manager. After those packages were reinstalled got the same error, "E: gsfonts: subprocess installed post-installation script returned error exit status 1". That error was also followed by a list of broken package dependencies. Again I followed the same steps for all gsfonts installed packages. The reinstall produced the same results again.

Suggestions on what to try next.

---

### Post by harr986 on 2011-06-29
I have upgraded again. This time to 11.04. Problems fixed. However, I'm not sure if I like "unity".

---

