---
title: "Ubuntu Software Center and JoliOS not working"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by dj_Klinger on 2011-05-25
Sadly, I started out as a JoliOS user - but I have petty much removed all the Joli features and am just using the bare Ubuntu system. Nonetheless, I can't get the Ubuntu Software Center to work. When I run in terminal I get the following message:

ImportError: No module named Joli OS

Any suggestions?

---

### Post by sikander3786 on 2011-05-25
Welcome to the forums :)

I don't know much about JoliOS but can try to help you. Doesn JoliOS really come with Software Center? I don't think so...

From Terminal, you are trying this command?

```
software-center
```

What if you try to install it?

```
sudo apt-get install software-center
```

---

### Post by dj_Klinger on 2011-05-25
Thanks for the reply.

'sudo apt-get install software-center' shows that it is installed and is  the latest version 2.0.7 (as does synaptic package manager). But when I  try to run it from terminal ('software-center') it looks like it wants  to run, until:[FONT=monospace][FONT=Verdana]
  
[/FONT][/FONT]> [FONT=monospace]File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 77, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named Joli OS[/FONT]
[FONT=monospace] 
  
So I'm thinking maybe it goes looking in that file  (/usr/share/software-center/softwarecenter/distro/__init__.py) for a  definition to apply to the relevant distro (Joli OS in this case). It  doesn't find it so it just quits. But I'm pretty new to this so it's  just a guess.
  
Here's all the code:
  
[/FONT]> Traceback (most recent call last):
  File "/usr/bin/X11/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 34, in <module>
    from softwarecenter.backend.channel import SoftwareChannel
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 22, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 88, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 77, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named Joli OS

[FONT=monospace]
[/FONT]

---

### Post by dj_Klinger on 2011-05-26
Any other suggestions?

---

