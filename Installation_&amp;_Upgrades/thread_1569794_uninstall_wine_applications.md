---
title: "uninstall wine applications"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by stijnblommerde on 2010-09-07
ubuntu 10.04

i installed a program in wine, but it did not work well, therefore i wanted to uninstall it again

the default procedure did not work (applications - wine - uninstall wine software)

therefore i removed the content of the program on the virtual disk c:

now i also want to remove the application launcher in the applications menu and clean up the registry

how do i do this?

thanks in advance

---

### Post by ottosykora on 2010-09-07
....>clean up the registry
<....

registry? on Linux? or did I missunderstand you somehow?

---

### Post by stijnblommerde on 2010-09-07
o.k., so i understand that a registry does not exist in linux. (i guess also no virtual registry in wine) i did not know that (newbee).

still, i would like to remove the 'application launchers' in the applications menu. 

i removed the complete .wine folder, shut down and restarted the laptop, but the launchers are still around.

launchers/menu items:
applications - wine - programs - itunes 
applications - wine - programs - quicktime

how to remove these launchers?

---

### Post by Fifthmarch on 2010-09-17
I had the same problem, and solved it using this thread:
[http://ubuntuforums.org/archive/index.php/t-815333.html](http://ubuntuforums.org/archive/index.php/t-815333.html)

What you have to do is delete all the files in  ~/.local/share/applications/wine

---

### Post by stijnblommerde on 2010-09-17
thank fifthmarch. your answer solved my problem.

---

### Post by Fifthmarch on 2010-09-17
Yay! 

First time I solved a problem on ubuntu forums!

---

