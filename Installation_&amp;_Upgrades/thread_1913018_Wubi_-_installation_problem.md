---
title: "Wubi - installation problem"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by spili on 2012-01-21
Hello,

first of all , sorry for my english :)

problem : I tried to install Ubuntu to my Windows XP ... i followed this instructions : [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer) .... but at the end of this installation after rebooting my computer i dont get this [http://www.ubuntu.com/sites/default/files/active/maverick/U2.2.2_07_medium.jpg](http://www.ubuntu.com/sites/default/files/active/maverick/U2.2.2_07_medium.jpg) .... just me windows start normally like nothing happens ...

Thank you a lot :)

---

### Post by bcbc on 2012-01-21
If the installation completed normally, check your boot.ini. It should have an entry in it for Ubuntu. Also check the 'time to display OS':
Right click My Computer, Properties, Advanced tab, Startup & Recovery settings. 

If the timeout is 0, set it to 30. If there is no Ubuntu entry in the drop down box (warning don't set it as default if it's there), then click to edit/view the boot.ini and copy and paste the contents back here.

---

