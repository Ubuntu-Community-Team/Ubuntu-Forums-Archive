---
title: "Upgraded to natty, and dont have unity"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by marin123 on 2011-04-26
today i upgraded to natty and it went well (except for mistake of not removing ati driver before upgrading what caused 2 hours of me fixing..)..

now i have weird problem - there no unity.

my desktop looks the same as before - docky and 1 gnome panel, no matter what session i choose (unity or classic)..

this is good news for unity haters, but i did upgrade because i wanted unity.

can someone help? i guess i have to run something to set defaults on system...

---

### Post by marin123 on 2011-04-27
compiz --replace gives this...

```
marin@marincelo:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (bailer) - Info: Ensuring a shell for your session
marin@marincelo:~$ Cannot register the panel shell: there is already one running.


```

---

### Post by dino99 on 2011-04-27
with synaptic: 

remove/purge shell/dock if installed
remove/purge then reinstall compiz & unity

logout and reboot

---

### Post by linuxmonamour on 2011-04-27
Help please!

I've just installed 11.04 but can't have unity since it doesn't support ATI Radeon HD 5600 series along other ATI cards. Anyone who knows when ubuntu is planning to solve this problem?

Anyone who offers any solution?

---

### Post by dino99 on 2011-04-27
> **linuxmonamour said:**
> Help please!

I've just installed 11.04 but can't have unity since it doesn't support ATI Radeon HD 5600 series along other ATI cards. Anyone who knows when ubuntu is planning to solve this problem?

Anyone who offers any solution?

Please dont spam this thread, open yours. You still can select the "classic" choice while you set gdm logging, then if your hardware config is conflicting:
- with synaptic: remove/purge ubuntu-desktop, unity
- file a bug report: ubuntu-bug unity
  ( you need to create a launchpad account first)

---

### Post by marin123 on 2011-04-27
> **dino99 said:**
> with synaptic: 

remove/purge shell/dock if installed
remove/purge then reinstall compiz & unity

logout and reboot

i did this, it messed up everything... i'm going to reinstall and remove windows...

it's not problem with unity, its with video drivers. they got messed up during upgrade because i didnt remove ati drivers before upgrading.

thanks for your help :)

---

