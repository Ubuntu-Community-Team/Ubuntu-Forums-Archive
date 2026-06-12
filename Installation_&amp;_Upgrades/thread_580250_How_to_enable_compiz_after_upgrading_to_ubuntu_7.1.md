---
title: "How to enable compiz after upgrading to ubuntu 7.10"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by yinglcs2 on 2007-10-18
Hi,

I have been using ubuntu 7.04 and install compiz fusion myself.

Today, I follow this to upgrade to 7.10,
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

however, after the upgrade, i don't see compiz fusion.
And when I click Compizconfig manager, nothing shows up (no application get started).

Can you please tell me how to fix my problem?

---

### Post by climatewarrior on 2007-10-18
Look under system/preferences/appearance then click the visual effects effects tab. There you will be able to start compiz. If you want to configure Compiz you will have to get the Advanced Desktop Effects Settings. Just look for compiz in add/remove and you will be able to install it from there. If you haven't removed your old beryl/compiz/compizfusion installation it is likely that you will have to delete it in order to get gutsy's compizfusion to work.

If you have any doubts post again.

Enjoy the Gutsy ;)

---

### Post by yinglcs2 on 2007-10-18
Thanks for your help.
i am now able to start compiz by following your suggestion.

But when i click 'Compizconfig setting manager', nothing shows up (i did see the hardware being busy for 15 seconds, but nothing happens afterward).  

You mention i need to remove my old beryl, compiz fusion that i installed manually for 7.04. What is the safest way for me to do that?

How can I configure compiz in 7.10 ?

---

### Post by Hayesio on 2007-10-18
You need to run the compizconfig manager from the terminal to see what the fault is.  Then post the output.

---

### Post by yinglcs2 on 2007-10-18
I get this :

~$ compizconfig
bash: compizconfig: command not found

---

### Post by Hayesio on 2007-10-18
I don't know if thats the right command.  Go to the icon in the menu, right click on it and click properties.  The correct command (the command that the icon uses) will be listed here in the properties.  Type/cut-and-paste that command into the terminal and run it. 

Any change?

---

### Post by yinglcs2 on 2007-10-18
Okay, this is what I get:

$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

ccsm is the command. 

Thank you for any more pointers.

---

### Post by climatewarrior on 2007-10-20
I suggest you install Advanced Desktop Effects Settings and remove your old compiz fusion manager. That should fix it.

---

### Post by yinglcs2 on 2007-10-21
I finally solve it by go to synatic package manager:
1. uninstall compiz setting manager
2. install compiz setting manager

My guess is I have a version of compiz setting manager (manually installed compiz on ubuntu 7.04) which is incompatible with compiz in ubuntu 7.10.
__________________
Edit/Delete Message

---

