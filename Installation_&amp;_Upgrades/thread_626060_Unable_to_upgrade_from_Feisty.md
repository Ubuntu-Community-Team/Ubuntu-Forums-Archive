---
title: "Unable to upgrade from Feisty"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by Shinigami Delroën on 2007-11-28
Hello,

It's been more than a month since the release of the 7.10, but I'm still unable to make the upgrade.

I tried all known methods, but none worked :
[LIST]
[*]gksu "update-manager -c"
[*]sudo apt-get dist-upgrade
[*]Synpatic
[*]Alternate CD
[/LIST]

I simply don't get the message "New release available"... 

I checked my sources.list and generate a new one on sourcelist.org (a component of the French ubuntu community website, for I'm French but none in the French communty was able to help me on this)

Thanks a lot !

---

### Post by Sef on 2007-11-28
Did you try System > Administration > Upgrade Manager?

> Alternate CD

What happened when you used that?

---

### Post by Shinigami Delroën on 2007-11-29
> Did you try System > Administration > Upgrade Manager?That's what the command **gksu "update-manager -c"** does.

> What happened when you used that?I don't remember exactly, so I tried again with a mounted ISO, and this is what I get :
```
Traceback (most recent call last):
  File "/tmp/tmp.LAPhao2787/gutsy", line 36, in <module>
    filemode='w')
  File "/tmp/tmp.LAPhao2787/__init__.py", line 1240, in basicConfig
    
  File "/tmp/tmp.LAPhao2787/__init__.py", line 770, in __init__
    
IOError: [Errno 13] Permission denied: '/var/log/dist-upgrade/main.log'
```

and when I burn it on a CD : 
```
bash: /media/cdrom0/cdromupgrade : /bin/sh : mauvais interpréteur: Permission non accordée
```
(which must give something like "wrong interpretor : Permission denied" in English)

---

