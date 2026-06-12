---
title: "gdm only runs gnome-session"
date: 2014-10-14
forum: Installation &amp; Upgrades
---

### Post by 316479 on 2014-10-14
I want to use gdm as my default-display-manager  and  xfce4-session as my default session[FONT=courier new]

[/FONT]This worked for me in Precise but broke when I upgraded to Trusty.

/usr/bin/x-session-manager -> /etc/alternatives/x-session-manager  -> /usr/bin/xfce4-session

and 
~/.xsession   contains

#!/usr/bin/env  bash
exec  /usr/bin/xfce4-session

/etc/gdm/custom.conf is vanilla

rm -rf .cache/sessions   doesn't help

In spite of all this configuration   gdm **always**&#8203; runs /usr/bin/gnome-session

Is there a configuration file somewhere that I've missed ?

---

### Post by 316479 on 2014-10-19
It turns out the gdm in 14.04 uses the user profile setting in 

/var/lib/AccountsService/users/<USER">  

to select the session to run.

Setting  XSession=xfce 

in my profile gave me the session I wanted.
[B]
GRUMBLE
[/B]- totally undocumented interface
- shouldn't override existing mechanisms like   /usr/bin/x-session-manager 
   and ~/.xsession
- should be included in gdm documentation.

---

