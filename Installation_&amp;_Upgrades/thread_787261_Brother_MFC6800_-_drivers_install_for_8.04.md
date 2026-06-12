---
title: "Brother MFC6800 - drivers install for 8.04"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by zeiz on 2008-05-08
If someone has Brother MFC6800 then it's a trick in Hardy:

BEFORE installing of Brother's drivers please create a directory:

$ sudo mkdir /usr/share/cups/model

Brother's cupswrapper installs .ppd files to the directory otherwise you'll get error similar to "unable to install .ppd..." and your printer then won't work and you have to uninstall cupswrapper and then install it again after creating of the directory.

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143)

---

### Post by avtolle on 2008-05-08
> **zeiz said:**
> If someone has Brother MFC6800 then it's a trick in Hardy:

BEFORE installing of Brother's drivers please create a directory:

$ sudo mkdir /usr/share/cups/model

Brother's cupswrapper installs .ppd files to the directory otherwise you'll get error similar to "unable to install .ppd..." and your printer then won't work and you have to uninstall cupswrapper and then install it again after creating of the directory.

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143)

Actually, this needs to be done in Hardy for any Brother printers. I found this out when installing a Brother MFC240C a few weeks ago. 

Good catch, there, and good to call it to our attention.

---

### Post by zeiz on 2008-05-09
Indeed. Not only Brother printers. I have also color Xerox and it also requires "model" directory under /usr/share/cups .
It looks like not a big deal for developers to restore this directory in Hardy :)

---

### Post by KD6TZF on 2008-05-19
> **zeiz said:**
> If someone has Brother MFC6800 then it's a trick in Hardy:

BEFORE installing of Brother's drivers please create a directory:

$ sudo mkdir /usr/share/cups/model

Brother's cupswrapper installs .ppd files to the directory otherwise you'll get error similar to "unable to install .ppd..." and your printer then won't work and you have to uninstall cupswrapper and then install it again after creating of the directory.

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143)

I did this then downloaded the MFC6800 driver from Brother and installed it, but the printer still doesn't print.  As for the computer, I submit a test print.  The notice comes up that the job has been submitted, but nothing prints.  I have not been able to locate any error messages and don't know where to go from here.  Help Please.

Thanks,

---

### Post by avtolle on 2008-05-19
Take a look at this:
[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)
Used it to install Brother MFC240C under Hardy (8.04) with success.

---

