---
title: "Installing Eclipse 3.7 on Ubuntu 11.4 Problem"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by YasinG on 2012-10-09
I have been trying to install Eclipse 3.7 on Ubuntu 11.4 but I ran into a problem. I followed this [article]("http://colinrrobinson.com/technology/install-eclipse-ubuntu/"), downloading eclipse-SDK-3.7.2-linux-gtk.tar.gz, and all was well, seemingly, until the very last step:

6) Launch Eclipse for the first time

[COLOR=Blue] sudo /opt/eclipse/eclipse -clean &[/COLOR]

Which gives me this reply:
[COLOR=Blue][1] 6719
User@User:~$ sudo: /opt/eclipse/eclipse: command not found[/COLOR]

Also, when I try to run it from gnome and click the icon it starts to run but then disappears, or quits, immediately.
I'd  appreciate it if anyone could help me.
Thanks in advance.

---

### Post by YasinG on 2012-10-11
The problem is, somehow solved, after I have used this command on the same tar file but from desktop this time:

[COLOR=Blue]tar [COLOR=Red]xvfz[/COLOR] eclipse-SDK-3.7.2-linux-gtk.tar.gz[COLOR=Red] -C /opt[/COLOR][/COLOR]

The one I used at first, following the article I linked in the first comment, was slightly different, although I have no idea what's the difference:

[COLOR=Blue]tar [COLOR=Red]xzf[/COLOR] eclipse-SDK-3.7-linux-gtk-x86_64.tar.gz[/COLOR]

Have a nice day.

---

