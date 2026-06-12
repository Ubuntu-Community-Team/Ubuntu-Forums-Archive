---
title: "Installation failed. Ubuntu 14.04 amd64"
date: 2014-09-22
forum: Installation &amp; Upgrades
---

### Post by ttyk on 2014-09-22
Just downloaded, emulated into virtual drive (Daemon Tool) and after starting installation it returned error:

[http://puu.sh/bKcuT/632fe6a824.jpg](http://puu.sh/bKcuT/632fe6a824.jpg)

Log file:

[http://ttyk.ru/share/wubi-14.04-rev286.log](http://ttyk.ru/share/wubi-14.04-rev286.log)

---

### Post by yancek on 2014-09-22
You are using the wubi installer to install Ubuntu inside windows as a program.  It is not supported any longer although some people still get it to work.  It probably won't work if you have windows 8 which the link below indicates.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by hakuna_matata on 2014-09-29
> **ttyk said:**
> 
[http://ttyk.ru/share/wubi-14.04-rev286.log](http://ttyk.ru/share/wubi-14.04-rev286.log)
Unfortunately, current wubi.exe doesn't work with iso files of Ubuntu 14.04.[COLOR=#ff0000]1[/COLOR]

As your log said:
> ```
09-23 11:45 INFO   Distro: [COLOR=#ff0000]Found[/COLOR] a valid iso for Ubuntu: E:\_ubuntu\ubuntu-14.04.[COLOR=#ff0000]1[/COLOR]-desktop-amd64.iso
```
But:
> ```
09-23 11:45 ERROR  CommonBackend: Invalid md5 for ISO E:\_ubuntu\ubuntu-14.04.1-desktop-amd64.iso ([COLOR=#ff0000]dccff28314d9ae4ed262cfc6f35e5153[/COLOR] != [COLOR=#ff0000]119cb63b48c9a18f31f417f09655efbd[/COLOR]) None
```

[COLOR=#ff0000]dccff28314d9ae4ed262cfc6f35e5153 [/COLOR]is md5sum of ubuntu-14.04-desktop-amd64.iso
[COLOR=#ff0000]119cb63b48c9a18f31f417f09655efbd [/COLOR]is md5sum of ubuntu-14.04**.**[COLOR=#ff0000]1[/COLOR]-desktop-amd64.iso

This means, you have ubuntu-14.04.[COLOR=#ff0000]1[/COLOR]-desktop-amd64.iso but wubi.exe needs ubuntu-14.04-desktop-amd64.iso

Recommendation: If possible, install without Wubi.

Other solutions with Wubi (every line is an independent solution):

[LIST]
[*]Download and install ubuntu-14.04-desktop-amd64.iso which is still available:  [http://releases.ubuntu.com/trusty/ubuntu-14.04-desktop-amd64.iso](http://releases.ubuntu.com/trusty/ubuntu-14.04-desktop-amd64.iso) 
[*]Download wubi14041.exe from a small project with all bugfixes: [http://ubuntuforums.org/showthread.php?t=1639198&page=121&p=13121598#post13121598](http://ubuntuforums.org/showthread.php?t=1639198&page=121&p=13121598#post13121598) 
[*]Edit current wubi.exe with [7zip.]("http://www.7-zip.org") Change 14.04 to 14.04.1 in included file **data/isolist.ini ** 
[*]**......** 
[/LIST]

---

