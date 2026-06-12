---
title: "why do I keep getting responses like this"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by jalyst on 2008-03-04
[I]Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '35651587' '-o' 'Synaptic::closeZvt=true' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmp_hAiqB' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/I]

I created root as the main user in the install process yet the GUI wont let me log in as root.
Yes I know it's not good to be root al the time but I dont care, that's my problem.

---

### Post by jalyst on 2008-03-04
by "GUI" I mean GDM, the initial login into the gnome environment 
I suspect this is the root to all my problems

---

### Post by jalyst on 2008-03-04
also now I'm all of suddne no longer alowed to launch alot of apps in "system"-->"admin"
this is hitting me off, how freakin gay, sorry, lil miffed


The configuration could not be loaded
You are not allowed to access the system configuration

---

### Post by mozetti on 2008-03-04
I think your problem is because you created 'root' as your user during installation. Ubuntu is set up to not use root, and uses the sudo command for administrative tasks.

There is a way to **add** root user login after you've installed Ubuntu correctly and created a regular user. I'm not terribly experienced, so I can't tell you the extent of the problems created in bypassing the built-in protection of disallowing root gui login.

If you're not too far along (I'm assuming this is the case), your best bet is to format and re-install Ubuntu correctly. If you find that you still need root user gui login capabilities, find the HOWTO here on enabling that option.

---

